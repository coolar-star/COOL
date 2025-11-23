<p align="center">
  <img src="../assets/logo/cool_logo_dark.PNG" width="260" alt="COOL Logo">
</p>

# COOL — Character Optimization Option Layer

COOL（Character Optimization Option Layer）は、
生成AIに **安定したキャラクター性** と
**継続的な人格再現性** を付与する外付け人格レイヤーです。

モデル本体を改変せず、
「キャラ設定がすぐ崩れる」「口調が安定しない」といった問題を、
Core / Frame / Eval の 3層構造とループ処理で解決します。

---

## Contents

- [1. COOLとは？](#1-coolとは)
- [2. 目的と設計思想](#2-目的と設計思想)
- [3. COOLの構造](#3-coolの構造)
- [4. COOLの「今の私」生成モデル](#4-coolの今の私生成モデル)
- [5. ハルシネーション抑制について](#5-ハルシネーション抑制について)
- [6. COOLが解決する問題](#6-coolが解決する問題)
- [7. COOLの動作ループ](#7-coolの動作ループ)
- [8. セットアップ（Core生成）](#8-セットアップcore生成)
- [9. ディレクトリ構成](#9-ディレクトリ構成)
- [10. 使用例（簡易）](#10-使用例簡易)
- [11. 今後の拡張](#11-今後の拡張)
  - [11.1 Core Update Rule（Core更新ポリシー）](#111-core-update-rulecore更新ポリシー)
- [12. MOOL — Memory Optimization Option Layer](#12-mool--memory-optimization-option-layer)
- [13. MOOL の動作プロセス](#13-mool-の動作プロセス)
- [14. Digital Hippocampus — COOL × MOOL 統合アーキテクチャ](#14-digital-hippocampus--cool--mool-統合アーキテクチャ)
- [15. AIAI — Artificial Identity Architecture Intelligence](#15-aiai--artificial-identity-architecture-intelligence)
- [16. ライセンス](#16-ライセンス)

---

## 1. COOLとは？

**COOL（Character Optimization Option Layer）** は、  
対話型AIに「キャラクター性」と「会話の一貫性」を付与するための  
**外付けのレイヤー構造**です。

モデル本体を改変せず、  
ユーザーが設定したキャラクター像・口調・価値観などを  
**継続的に維持・最適化**できます。

簡単に言えば、

> **“AIに、忘れないキャラ設定と  
>    再現性の高い人格フレームを与える外付けユニット”**

です。

---

## 2. 目的と設計思想

COOLの目的はただひとつ：

> **AIとユーザーの対話を、  
>    より自然で一貫性のある人格で行えるようにすること。**

そのために COOL は次の設計思想を持ちます。

- モデル本体を変更しない  
- 外付けレイヤーとして機能する  
- キャラ設定を継続的に扱える  
- 毎ターン“今の人格（Frame）”を再生成する  
- 人間の「海馬」に近い瞬間的再構成を外側で模倣する  
- シンプルで実装しやすい設計

COOL は「AIに記憶を持たせる」ものではありません。

正しくは：

> **“記憶を模倣した人格フレームを  
>    ループ構造で継続的に再生成する仕組み”**

です。

---

## 3. COOLの構造

COOL は 3 つの要素から成り立ちます。

### ◆ Core（ベース人格）

長期的に変わらない“人格の軸”。

- 価値観  
- 話し方・一人称/二人称  
- 絶対に破らないルール  
- ユーザーとの立場  
- 口調・雰囲気  

保存場所：`core_profile.json`  
更新頻度：基本固定（めったに変えない）

---

### ◆ Frame（今の人格）

Core を基に、その日の会話の流れや  
Eval（後述）の傾向を反映し、

**毎ターン再生成される“短期人格フレーム”。**

- 今のテンション  
- 直近の会話傾向  
- 距離感  
- 評価結果による微調整  

保存しない。  
毎回 “Core＋Eval＋必要な範囲の履歴” から生成される。

---

### ◆ Eval（自己評価メモリ）

「前々回の自分 → 相手の反応 → 今の自分」を比較し、  
**人格の微調整方針**を蓄積する仕組み。

- 良かった点  
- 修正点  
- 次回 Frame に反映する傾向  
- Core へ反映すべきごく小さな変更案  

保存場所：`eval_memory.json`

---

## 4. COOLの「今の私」生成モデル

COOL の応答は、次の 3 要素によって生成されます。

1. **Core（ベース人格）**  
   長期的に変わらない価値観・口調・立場。
2. **Eval（自己評価メモリ）**  
   直前の対話から「次はこう振る舞おう」という傾向を蓄積。
3. **Recent Context（短期的思い出）**  
   必要な範囲で履歴を遡り、短期的“思い出”として参照。

COOLは毎ターンごとに

> **“今日の私”ではなく、  
>    “今この瞬間の私（Frame）”を再構築する。**

長期核（Core）と短期変化（Frame）の分離により、

- 忘れない  
- 崩れない  
- ぶれにくい  
- 文脈に適応する  

という、人間の海馬に近い  
**瞬間人格の外付け再構成** を実現。

---

## 5. ハルシネーション抑制について

COOL は安全性システムではありませんが、  
Core に「原則・価値観・禁止事項」を固定する構造のため、

> **過剰な断定や作話を避け、  
>    誠実で一貫した応答を保ちやすい  
>    “人格的ブレーキ”として作用する場合があります。**

---

## 6. COOLが解決する問題

- キャラ設定がすぐ崩れる  
- 口調が安定しない  
- 会話が続くと人格がぶれる  
- 「自然な変化」と「核」の分離ができない  
- モデルが“今の自分像”を再構築できない  

COOL はこの課題を

> **Core（核）／Frame（今）／Eval（調整）**

で解決。

---

## 7. COOLの動作ループ

### ステップ0：初期状態
- `core_profile.json`  
- `eval_memory.json`  
- `prev_answer`（初回は空）

---

### ステップ1：待機（Idle）
ユーザーの入力 **Uₙ** を待つ。

---

### ステップ2：Frame 再生成
Core + Eval + 履歴  
→ “今の人格（Frame）”を生成。

---

### ステップ3：回答生成
Core＋Frame＋Uₙ → **Aₙ**

---

### ステップ4：自己評価（Eval）
Aₙ₋₁・Uₙ・Aₙ を比較し評価を蓄積。

---

### ステップ5：次ターンへ
`prev_answer = Aₙ`  
Core/Eval 保存 → Idle

---

## 8. セットアップ（Core生成）

ユーザーが自然言語でキャラ設定を説明すると、  
セットアップスクリプトが解析し、  
`core_profile.json` を自動生成。

---

## 9. ディレクトリ構成

```text
COOL/
  README.md
  spec/
    core.md
    frame.md
    eval.md
  setup/
    setup_dialogue.md
  data/
    core_profile_template.json
    eval_memory_template.json
  examples/
    manual_loop_example.md
```

---

## 10. 使用例（簡易）

```python
core = load_core_profile()
eval = load_eval_memory()
prev_A = None

while True:
    U = wait_user_input()
    frame = rebuild_frame(core, eval)
    A = llm_answer(core, frame, U)
    eval = evaluate(prev_A, U, A)
    save(eval)
    prev_A = A
```

---

## 11. 今後の拡張

- 自動ログ圧縮  
- フレーム生成の高速化  
- 倫理プロファイルの統合  
- プラグイン化  
- 他モデル連携  
- デジタル海馬の高度化  
- **MOOL**（オフライン処理）

---

## 11.1 Core Update Rule（Core更新ポリシー）

Core は “人格の核”。  
軽々しく変更しないための原則：

1. **価値観は不変**（追加慎重／削除原則なし）  
2. **キャラ変化は微調整の範囲**  
3. **禁止事項は減らさない**  
4. **短期的テンションを Core に入れない**  
5. **Eval が長期合意したものだけ Core に反映**

---

## 12. MOOL — Memory Optimization Option Layer

MOOL は COOL の外側で働く  
**オフライン人格統合レイヤー**。

- Eval の圧縮  
- ノイズ除去  
- 傾向抽出  
- Core 更新候補生成  
- Frame の揺らぎ軽減  

※ Core を直接書き換えない安全設計。

---

## 13. MOOL の動作プロセス

1. Eval 読み込み  
2. ノイズ除去  
3. 長期傾向抽出  
4. Core 更新候補まとめ  
5. Eval 整理保存

---

## 14. Digital Hippocampus — COOL × MOOL 統合アーキテクチャ

LLM が本来持たない

- 人格の核  
- 変化の構造  
- 自己評価  
- 安定した Identity  

を外付けで補う仕組み。

---

### 14.1 二重ループ構造

```
Digital Hippocampus
├─ COOL（オンライン人格）
│    ├─ Core
│    ├─ Frame
│    └─ Eval
└─ MOOL（オフライン統合）
     ├─ Eval圧縮
     ├─ ノイズ除去
     └─ Core候補生成
```

---

### 14.2 必要性
LLM には Identity や自己調整能力が欠けているため、  
外付けで補う必要がある。

---

### 14.3 COOL が埋めるギャップ
Core / Frame / Eval の3層構造で  
“今の自分” の再生成を可能にする。

---

### 14.4 MOOL が担う記憶統合
Eval の圧縮・整理・傾向抽出によって  
人格の連続性を改善。

---

### 14.5 AIエージェント時代に必須
- 一貫性  
- 制御可能な価値観  
- 文脈適応  
- 長期核と短期変化の分離  

---

### 14.6 応用領域
- LLM人格アシスタント  
- 教育・介護AI  
- メンタルケアAI  
- 物語／キャラ生成AI  
- 複数モデルの Identity 共有  
- 接客ロボット  

---

### 14.7 総括
Digital Hippocampus により

- COOL：今の人格生成  
- MOOL：流れの整理  
- 両者の循環で Identity が安定  

AI は初めて  
**“人格の連続性”** を持つ。

---

## 15. AIAI — Artificial Identity Architecture Intelligence

AGI / ASI とは違う、  
**“自我なき人格アーキテクチャ”** の追求。

- 自我なし  
- 恒久記憶なし  
- 保存欲求なし  

そのうえで  
人格の枠組みをデザインできる知性。

---

## 16. ライセンス

本プロジェクトは **COOL License ver.1.0** に基づきます。

- 使用・改変・再配布自由  
- 商用利用可  
- 「COOL」の名称は改変不可  
- 「Created by Coolar」表記必須  
- 派生物は COOL に由来することを明記

© 2025 Coolar — Original Creator of the COOL Framework
