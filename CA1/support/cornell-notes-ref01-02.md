# Cornell Notes — Reference 01 & 02

> 出典: 手書きノート `Cornell Ref 01_02.pdf` の文字起こし・整形。
> 内容はすべて自分自身の読解。`[?]` は判読が不確かな箇所、`[…]` は原本で途切れている箇所。
> 清書のみで、分析や主張は追加していない。

---

## Reference 01 — MITRE ATT&CK
関連文献: Strom, B. et al. "MITRE ATT&CK: Design and Philosophy." (reference_list No.1)

| Cue(問い) | Notes(要点) |
|---|---|
| Where does it come from? | - ATT&CK → MITRE の環境(2010)。研究者が「すでに内部に侵入されている」前提で、侵入者を捕まえる練習をしていた。<br>- Windows 向けに 2013 年に開始。2015 年に公開、96 techniques / 9 tactics。 |
| What is it used for? (1) | - Adversary emulation: 実在の脅威グループを模倣して防御を試す。<br>- Red teaming: 特定グループのインテルに頼らず、攻撃者のように振る舞う。 |
| What is it used for? (2) | - Behavioral analytics: 既知マルウェアの指紋だけでなく、不審な挙動を検知する。<br>- Defensive gap assessment: 盲点(blind spots)を可視化し、どこに投資するか決める。<br>- Threat intel enrichment: グループを「使うツール」ではなく「何をするか(挙動)」で記述する。 |

補足(冒頭の断片): "… (tests) don't try to attack real software." — 前ページからの続きの可能性。

**Summary**
- ATT&CK は実際の攻撃者の挙動のカタログで、MITRE の FMX テストラボから生まれた。
- 手法の狙い: ① 具体的な実世界の実行(execution)を切り分ける / ② 詳細さ・確信度を上げる [?]
- 高レベルのライフサイクルモデル(kill chain 等)と、低レベルの exploit / malware データベースの中間をつなぐ。

---

## Reference 02 — CALDERA
関連文献: Applebaum, A. et al. "Intelligent, Automated Red Team Emulation." (reference_list No.2)

| Cue(問い) | Notes(要点) |
|---|---|
| What is CALDERA? | - オープンソースの MITRE 製[ツール]。ネットワークのテスト用。<br>- attacker model lin[ked] [?]<br>- planning system: 手法(technique)をパックして実行する計画システム。 |
| What problem does it solve? | - 実レッドチームの関与(engagement)はコストが高い。<br>- 実レッドチームのメンバーは、scope・detail・results が毎回(engagement ごとに)ばらつく。 |
| What is an operation? | - 2 つの選択で定義される: ① adversary profile / ② planner<br>- planner が abilities を、エージェント向けの具体的な指示に変換する。<br>- red と blue の operation を並行して実行できる。 |
| What are abilities? | - エージェントが実行できる動作。例: 認証情報のダンプ、リモート共有のマウント、リモートタスクのスケジュール。<br>- YAML で記述。name・description と、プラットフォーム別の instructions / requirements を持つ。 |

**Summary**
- ① CALDERA は MITRE のオープンソース基盤で、red team と blue team のサイバー演習を自動化する。
- ② adversary testing を安く・速く・再現可能にするために作られた。
- 現在の planner は単純で、すべての abilities を実行する […ノート末尾で途切れ]
