<p align="center">
  <img src="assets/logo/cool_logo_dark.PNG" width="260" alt="COOL Logo">
</p>

# COOL — Character Optimization Option Layer

---

# COOL  
**Character Optimization Option Layer**  
COOL（Character Optimization Option Layer）は、
生成AIに“安定したキャラクター性”を付与する外付け人格レイヤーです。

---

## 1. COOLとは？
**COOL（Character Optimization Option Layer）** は、  
対話型AIに「キャラクター性」と「会話の一貫性」を付与するための  
**外付けのレイヤー構造**です。

モデル本体を改変せず、  
ユーザーが設定したキャラクター像・口調・価値観などを  
**継続的に維持・最適化**できる仕組みを提供します。

簡単に言えば、

> **“AIに、忘れないキャラ設定と再現性の高い人格フレームを与える外付けユニット”**

です。

---

## 2. 目的と設計思想

COOLの目的はただひとつ：

> **AIとユーザーの対話を、より自然で一貫性のある人格で行えるようにすること。**

そのために COOL は次の設計思想を持ちます。

- モデル本体を変更しない  
- 外付けレイヤーとして機能する  
- キャラ設定を継続的に扱える  
- その都度“今日の人格”を生成する  
- 人間の「海馬」に近い役割を外側で模倣する  
- シンプルで手を入れやすい構造

COOL は「AIに記憶を持たせる」ものではありません。  
正しくは：

> **“記憶を模倣した人格フレームを、  
>  ループ構造で継続的に再生成する仕組み”**  
です。

これにより、会話の自然さ・継続性・個性が安定します。

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
更新頻度：基本固定／めったに変えない

---

### ◆ Frame（今日の人格）
Core を基に、その日の会話の流れ・自己評価の傾向を反映して  
**毎ターン再生成される“短期人格フレーム”。**

- 今日のテンション  
- 最近の会話のクセ  
- 距離感  
- 評価結果から反映された調整  

保存しない。  
毎回 Core＋Eval をもとに生成される。

---

### ◆ Eval（自己評価メモリ）
「前々回の自分 → 相手の反応 → 今の自分」を比較し  
**人格の微調整方針**だけを保存する仕組み。

- 良かった点  
- 修正すべき点  
- 次回 Frame に反映する傾向  
- Core にごく小さく反映すべき変更案

保存場所：`eval_memory.json`

---

## 4. COOLが解決する問題

- キャラ設定がすぐ崩れる  
- 口調や性格が安定しない  
- 会話が継続しても人格の一貫性が維持できない  
- 「前の回答を踏まえた自然な変化」ができない  
- AIが“人格の核”と“その日の変化”を分けられない  

COOLはこれを、

> **Core（核）と Frame（今日）と Eval（微調整）を分離する**

という構造によって解決します。

---

## 5. COOLの動作ループ

### ステップ0：初期状態
- `core_profile.json` が保存されている  
- `eval_memory.json` に評価の累積がある  
- `prev_answer` は前回の回答（初回は空）

---

### ステップ1：待機（Idle）
ユーザーからの入力を待つ。  
メッセージ **Uₙ** を受け取る。

---

### ステップ2：今日の人格を再生成（Frame Rebuild）
Core と Eval を読み込み、  
**Frame人格** を LLM に生成させる。

---

### ステップ3：セッション（回答生成）
Core＋Frame＋ユーザー入力 Uₙ から  
今回の回答 **Aₙ** を生成。

ユーザーへ返し、ログに保存。

---

### ステップ4：自己評価（Eval）
前回の回答 **Aₙ₋₁** と  
今回のユーザー入力 **Uₙ**、  
そして今回の回答 **Aₙ** をセットで比較し、

- 良い点  
- 調整点  
- Coreに反映すべきごく小さな変更案  
- Frame生成へ反映する傾向

を生成。

Evalメモリへ保存し、Coreに必要なら反映。

---

### ステップ5：次のターンへ
- `prev_answer = Aₙ`  
- Core と Eval を保存  
- Idle に戻る

---

## 6. セットアップ（キャラ設定の導入）

ユーザーは自然言語でキャラクター設定を行い、  
それを Core に変換します。

例：

```
あなたは私の後輩で、丁寧だけど小悪魔的。
私のことは先輩と呼び、落ち着いた声で話して欲しい。
守ってほしい価値観は…
```

この対話を COOL のセットアップスクリプトが解析し、  
`core_profile.json` に自動変換します。

---

## 7. ディレクトリ構成

```
COOL/
  README.md
  /spec
    core.md
    frame.md
    eval.md
  /setup
    setup_dialogue.md
  /data
    core_profile_template.json
    eval_memory_template.json
  /examples
    manual_loop_example.md
```

---

## 8. 使用例（簡易）

```
core = load_core_profile()
eval  = load_eval_memory()

loop:
    U = wait_user_input()
    frame = rebuild_frame(core, eval)
    A = llm_answer(core, frame, U)
    eval = evaluate(prev_A, U, A)
    save(eval)
    prev_A = A
```

---

## 9. 今後の拡張

- 自動ログ圧縮  
- フレーム生成の高速化  
- 安全性・倫理プロファイルの統合（任意）  
- プラグイン化  
- GPTs や他モデルとの接続機能  
- 外付け“デジタル海馬”としての高度化

---

## 10. ライセンス

本プロジェクトは **COOL License ver.1.0** に基づいて提供されています。

- 使用・改変・再配布は自由
- 商用利用も許可
- ただし「COOL」の名称は削除・改変不可
- 「Created by Coolar」の著作権表記は必須
- 派生物は COOL に由来することを明記すること

詳しくはリポジトリ内の `LICENSE` ファイルを参照してください。

© 2025 Coolar — Original Creator of the COOL Framework

---



