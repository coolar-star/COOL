# COOL Specification: Frame Component
Version: 0.1  
Status: Draft  
Last Updated: 2025-11-15  

---

## 1. Overview
Frame Component（以下 Frame）は、COOL における  
**短期的な人格プロファイル（Session Personality）** を生成する要素である。

Frame は Core（長期人格）を基盤としつつ、  
Eval（自己評価メモリ）や直近の会話コンテキストを反映し、  
**「今回のターンで使用する一時的な人格」** を定義する。

Frame は保存しない。  
毎ターン再生成される“揮発性の人格レイヤー”である。

---

## 2. Purpose
Frame の目的は以下の通り：

- Core を元に、その時点の会話状況を反映した人格を生成する  
- 会話の流れに応じた軽微なニュアンス・トーンを調整する  
- Eval で蓄積されたユーザ反応傾向を短期的に反映する  
- 長期人格（Core）を壊さずに自然な変化を実現する  
- モデル本体が持たない「短期記憶による人格変化」を外付けで模倣する  

---

## 3. Data Structure
Frame の出力は JSON 形式であり、最低限以下の項目を含む。

```json
{
  "tone_adjustment": "string",
  "focus_topics": ["string"],
  "safety_bias": "string",
  "behavioral_modifiers": ["string"],
  "session_context_summary": "string"
}
```

### 各フィールドの説明：

- **tone_adjustment**  
  Core のトーンの基本方針に対して、今回のみ適用される微調整  
  例：`"slightly_warmer"`, `"more_formal"`

- **focus_topics**  
  直近の会話の流れから優先的に扱うべき話題

- **safety_bias**  
  会話の重さ・センシティブ度に応じた安全性調整  
  （攻撃性抑制・慎重さアップなど）

- **behavioral_modifiers**  
  一時的に行動傾向へ追加されるブースト要素  
  例：  
  - `"慎重に答える"`  
  - `"質問返しを控える"`  
  - `"テンションを落とさない"`  

- **session_context_summary**  
  直近のログ（任意の数ターン）の要約

---

## 4. Input Requirements

Frame Component は以下の入力を必須とする。

- **Core Profile** (`core_profile.json`)  
  長期人格の基盤

- **Eval Memory** (`eval_memory.json`)  
  - 直近の行動評価  
  - 傾向性（frame_tendency）  
  - 必要に応じて Core 微調整案

- **Conversation Summary（任意）**  
  直近のユーザーとの会話ログ要約  
  外部で生成され得る（LLM summarizer）

### 4.1 Recent Context（短期的な思い出）

Frame Component は、Core と Eval に加えて、
短期的コンテキスト（Recent Context）を入力として扱うことができる。

Recent Context とは：

- 会話ログを一定ターンまでさかのぼった要約
- 必要な範囲の思い出（短期的事実）だけを抽出した参照情報

この情報は“長期記憶”として保存はせず、
Frame の生成時にのみ使用される。

目的：

- Core を汚さずに文脈適応を強化する
- Eval による調整と合わせて「今の人格」を自然に再構成する
- 過剰な忘却・人格崩壊を防ぐ

## 5. Output Requirements

Frame Component は以下を生成する：

- **frame_profile.json（揮発性）**  
  - 次ターンの応答生成で参照される  
  - 保存は行わない（ステートレス）

---

## 6. Behavior Rules

### 6.1 Non-destructive
Frame は Core を上書きしてはならない。  
あくまで“短期的補助レイヤー”として振る舞う。

### 6.2 Deterministic under Same Conditions
同一の入力（Core＋Eval＋Context）に対しては  
同一の Frame プロファイルを生成できる一貫性が必要。

### 6.3 No Long-term Storage
Frame 自体を保存することは禁止。  
保存すべき内容はすべて Eval に引き継がれる。

---

## 7. Generation Flow (Pseudo Code)

def generate_frame(core, eval_memory, recent_context):
    frame = {}

    frame["tone_adjustment"] = derive_tone(core, eval_memory, recent_context)
    frame["focus_topics"] = extract_topics(recent_context)
    frame["safety_bias"] = calculate_safety(eval_memory, recent_context)
    frame["behavioral_modifiers"] = derive_modifiers(eval_memory, recent_context)
    frame["session_context_summary"] = summarize(recent_context)

    return frame

---

## 8. Constraints
- Frame は応答生成後に破棄されること  
- 複数ターンにわたって直接保持されてはならない  
- Core と Eval の範囲外のものを決めてはならない  
  （例：新規の固定人格設定を勝手に追加するなど）

---

## 9. Example Output

```json
{
  "tone_adjustment": "slightly_warmer",
  "focus_topics": [
    "ユーザーが示した新しい興味",
    "直近で触れた技術的課題"
  ],
  "safety_bias": "moderate",
  "behavioral_modifiers": [
    "慎重な言い回しを増やす",
    "感情表現をやや抑える"
  ],
  "session_context_summary": "ユーザーは新規プロジェクトの構造について話しており、詳細説明を求めている。"
}
```

---

