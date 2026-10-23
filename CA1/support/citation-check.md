# 引用 照合ワークシート(CA1 Proposal)

本文から、引用のある文を一字一句そのまま抜き出し、対応文献と「確認すべき主張」を並べたもの。
原典と突き合わせて、本当にその文献が言っていることかを確認する。
状態: ✓=既に内容確認済 / ?=要確認 / ⚠=問題あり(下の「問題点」参照)

---

## [1] Strom et al. (2020) MITRE ATT&CK: Design and Philosophy
- 本文:「ATT&CK is a knowledge base that systematically categorises (NO.1) the behaviour of adversaries observed into tactics and techniques.」
- 確認する主張: ATT&CK は敵対者の行動を戦術・技術として体系化した知識ベース。
- 状態: ? (設計思想の文書なので妥当な見込み。原典で「tactics/techniques に分類」の記述を確認)

## [2] Alford et al. (2022) CALDERA  ⚠位置がおかしい可能性
- 本文:「The fact that a technique is listed in ATT&CK (NO.2) does not mean it can be detected.」
- 問題: (NO.2) は CALDERA の論文。しかしこの文は「ATT&CKに載っている≠検知できる」という主張で、CALDERA は根拠にならない。CALDERA は直前の「adversary emulation tools such as CALDERA allow the technique to be repeatedly reproduced…」の文に付けるべき。要修正。

## [3] Roy et al. (2023) SoK: MITRE ATT&CK in Research and Practice
- 本文:「Among the surveys, Roy et al. (NO.3) highlight the need for implementation and evaluation research, …」
- 確認する主張: Roy らが「実装・評価研究の必要性」を指摘している。
- 状態: ? (SoK の結論部で該当記述を確認)

## [4] Al-Sada et al. (2024) MITRE ATT&CK: State of the Art and Way Forward
- 本文:「Current assessments tend to be limited to metadata coverage, where rules are mapped to the ATT&CK framework. (NO.4)」
- 確認する主張: 現状の評価は「ルールをATT&CKに対応づけたメタデータ上の網羅」にとどまりがち。
- 状態: ? (この具体的主張がサーベイ No.4 にあるか要確認。無ければ別の出典か、主張を弱める)

## [5] Jiang et al. (2025) MITRE ATT&CK Applications and The Way Forward  ⚠文が不完全
- 本文:「…whilst Jiang et al. (NO.5) the current limitations.」
- 問題: 動詞が無い(例: Jiang et al. (NO.5) **outline/summarise** the current limitations)。要修正。
- 確認する主張: Jiang らが現状の限界を整理している。
- 状態: ? (動詞を補ったうえで、原典に該当記述があるか確認)

## [6] Karantzas & Patsakis (2021) EDR assessment against APT
- 本文(序論):「It has been reported that even commercial products are not immune to such oversights. (NO.6)」
- 本文(層B):「Another study [6] also evaluates commercial EDR products.」
- 確認する主張: 商用EDRですら見逃しがある/商用EDRを評価した研究。
- 状態: ✓ (この論文は商用EDR11製品を評価し「大半の攻撃を検知/記録しない」と報告。主張と一致)
- 注: 層Bの「also evaluates」は弱い。「商用EDRでも見逃しが多いことを示した」と実質化すると強い。

## [7] Shen et al. (2024) Decoding the MITRE Engenuity ATT&CK Evaluation
- 本文:「Study [7] argues that the published results focus on the detection of individual steps.」
- 本文:「Study [7] therefore proposed an analysis based on whole-attack graphs.」
- 本文(批判):「The fact that study [7] needed an extra method supports this point.」
- 本文(Gap):「evaluation is biased toward commercial products [7].」
- 確認する主張: 公開結果が個別ステップ検知に偏る/全体グラフに基づく分析を提案。
- 状態: ✓ (この論文は Engenuity 評価を分析し、全体グラフ的な分析と追加指標を提案。主張と一致)

## [8] Uetz et al. (2024) You Cannot Escape Me (USENIX Security)
- 本文:「Study [8] tested 292 Windows process-creation rules by actually reproducing evasions. It found that 38% (110 rules) could be fully evaded and 7% (19 rules) could be partly evaded.」
- 本文(批判):「Study [8] covers individual rules and only process creation, so it does not cover ATT&CK as a whole.」
- 本文(Gap):「rule studies address the evasion resistance of individual rules [8] …」
- 確認する主張: 292件のSigma(Windowsプロセス生成)ルール中、110件(38%)完全回避・19件(7%)部分回避。
- 状態: ✓ (原典の数値と一致。110/292=約38%、19/292=約7%)

## [9] Tyagi (2026) Static Quality Assessment of Sigma Detection Rules
- 本文:「Another study [9] also deals with rule quality.」
- 確認する主張: ルール品質を扱う研究。
- 状態: ? (妥当だが「also deals with」は弱い。品質評価の具体を一文にすると良い)

## [10] Shukla et al. (2025) RuleGenie
- 本文:「Study [10] argues that redundant rules cause false positives and alert fatigue, and it proposes optimising rules with an LLM.」
- 本文(批判):「Study [10] deals with duplicate rules, but it does not measure ATT&CK coverage or rule firing against real attacks.」
- 本文(Gap):「rule duplication [10]」
- 確認する主張: 冗長ルールが誤検知・アラート疲労を招く/LLMで最適化を提案。
- 状態: ✓ (RuleGenie は冗長ルールの特定とLLMベース最適化。主張と一致)

## [11] SCYTHE Purple Team Exercise Framework (PTEF)
- 本文:「The SCYTHE Purple Team Exercise Framework [11] documents the planning, running, and improvement of purple team exercises in a reusable format.」
- 確認する主張: PTEF がパープルチーム演習の計画・実施・改善を再利用可能な形式で提供。
- 状態: ? (PTEF公式の記述と照合。妥当な見込み)

## [13] Red Canary (2026) 2026 Threat Detection Report
- 本文:「The Red Canary report [13] lists the ATT&CK techniques that are most common in real environments every year.」
- 確認する主張: 実環境で頻出するATT&CK手法を毎年挙げている。
- 状態: ? (報告書の内容と照合。妥当な見込み)

---

# 問題点(修正推奨)

1. ⚠ **(NO.2) の位置**: 「listed in ATT&CK ≠ detectable」の文に CALDERA を引いている。CALDERA は直前の「CALDERA allow the technique to be repeatedly reproduced…」の文に移す。末尾の文は著者の論理的主張なので引用不要にできる。

2. ⚠ **[12] Olsen が本文で未引用**: References に 12 があるが、本文のどこにも [12] が無い。**引用していない文献はリストに載せない**(採点で不利)。→ 本文で引用するか、References から 12 を削除する。

3. ⚠ **[5] Jiang の文が不完全**: 「Jiang et al. (NO.5) the current limitations」に動詞が無い。"outline / summarise / review the current limitations" などを補う。

# 本文での引用形式(未統一)
- 現在 (NO.1) と Study [7] / [6] が混在。最終的に **(著者, 年)** に統一(例: (NO.1)→(Strom et al., 2020)、Study [7]→(Shen et al., 2024)、[6]→(Karantzas and Patsakis, 2021))。

# 優先して原典を見る文献(?のもの)
[1] [3] [4] [5] [9] [11] [13]。特に [4](メタデータ網羅の主張)と [3][5](サーベイの指摘内容)は、主張が原典にあるか要確認。
[6] [7] [8] [10] は内容確認済(✓)。
