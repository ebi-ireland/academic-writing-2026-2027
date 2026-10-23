# 04 Literature Review(本文を書くファイル)※最重要
対応: Proposal の Literature Review(最大 1500 語・配点 30%)
採点: 批判的評価(10)/ 最新動向(8)/ ギャップ(6)/ 出典(6)
語数配分: 導入 100 / 層A 300 / 層B 700 / 層C 200 / ギャップ 200

## English draft(Synthesis まで・作業中)

### Introduction
This review organises the detection assessment based on ATT&CK into three layers; foundation – ATT&CK and adversary emulation, empirical detection evaluation – EDR and detection rules, and standards & practice. Focusing on empirical detection evaluation, this study will critically synthesise the findings from the perspectives of evaluation targets, methods and reproducibility, and identify gaps in this project.

### Foundation: ATT&CK and Adversary Emulation
ATT&CK is a knowledge base that systematically categorises (NO.1) the behaviour of adversaries observed into tactics and techniques. This concept, which is more specific than Kill Chain and more general than individual IoCs, has become widely adopted as a common framework for detection and exercises. Among the surveys, Roy et al. (NO.3) highlight the need for implementation and evaluation research, whilst Jiang et al. (NO.5) the current limitations. Furthermore, adversary emulation tools such as CALDERA allow the technique to be repeatedly reproduced through executable steps, which is a requirement for reproducible measurements. However, these are just a foundation and do not provide evidence of detection performance. The fact that a technique is listed in ATT&CK (NO.2) does not mean it can be detected.

### Empirical Detection Evaluation: EDR and Detection Rules

#### Commercial EDR
The MITRE Engenuity evaluation is a standard evaluation of commercial products. It recreates the attack chains of real APT groups and publishes the result for each product. Study [7] argues that the published results focus on the detection of individual steps. As a result, they do not show whether a product can link the steps into one whole attack. Study [7] therefore proposed an analysis based on whole-attack graphs. Another study [6] also evaluates commercial EDR products.

**Critique:** This line of work has three limitations. First, it targets commercial products and does not cover free, open-source detection stacks. Second, the products are black boxes, so other researchers cannot reproduce the results or check why a detection succeeded. Third, vendors take part in the evaluation, so the published results alone are not sufficient. The fact that study [7] needed an extra method supports this point.

#### Detection rules
Open-source detection mainly relies on shared rules such as Sigma. Study [8] tested 292 Windows process-creation rules by actually reproducing evasions. It found that 38% (110 rules) could be fully evaded and 7% (19 rules) could be partly evaded. The existence of a rule does not guarantee detection. Therefore, coverage should be measured by whether rules actually fire, not by how rules are mapped to ATT&CK. Study [10] argues that redundant rules cause false positives and alert fatigue, and it proposes optimising rules with an LLM. Another study [9] also deals with rule quality.

**Critique:** Study [8] covers individual rules and only process creation, so it does not cover ATT&CK as a whole. Study [10] deals with duplicate rules, but it does not measure ATT&CK coverage or rule firing against real attacks.

#### Synthesis
| Aspect | Commercial EDR evaluation | Rule quality studies | This study |
|---|---|---|---|
| Target | Products | Single rules or rule sets | Open-source detection stack |
| Measured against ATT&CK | Yes | Partly | Yes |
| Reproducibility | Low | Varies by study | Environment, procedure, and versions are fixed |

Commercial EDR studies have real ATT&CK measurements, but their results cannot be reproduced. Rule quality studies are open, but they do not measure detection across ATT&CK as a whole. Within the scope of this review, no study was found that fills the gap between the two approaches.

### Standards & Practice
The SCYTHE Purple Team Exercise Framework [11] publishes the planning, running, and improvement of purple team exercises in a reusable format. It is a practical reference for designing the evaluation procedure. The Red Canary report [13] lists the ATT&CK techniques that are most common in real environments every year. It gives a basis for choosing which techniques to test. However, the method is not guaranteed to be as rigorous as that of peer-reviewed work.

### Gap
The literature shows three points. First, evaluation is biased toward commercial products [7]. Second, rule studies address the evasion resistance of individual rules [8] and rule duplication [10], but they do not measure the ATT&CK coverage of a whole detection stack. Third, reproducibility is missing. For open-source setups, we found no results that can be measured again with a fixed environment, procedure, and rule version. Therefore, few studies have measured the ATT&CK coverage of open-source detection stacks in a reproducible way. This project addresses this gap. It runs techniques automatically with adversary emulation and measures whether each technique is detected, using a fixed environment and procedure.

---

## 日本語下書き(英訳前・作業中)

### 1. 導入
本レビューは、ATT&CK に基づく検知評価を 3 層で整理する。層 A は理論の土台、層 B は検知評価の実証研究(商用 EDR とルール品質)、層 C は実務文書(灰色文献)である。層 B を中心に、評価の対象・方法・再現性の観点から批判的に統合し、本プロジェクトのギャップを特定する。

### 2. 層 A:理論の土台 (Foundations: ATT&CK and Adversary Emulation)
ATT&CK は、実観測された敵対者の行動を戦術・技術として体系化した知識ベースである。Kill Chain より具体的で個別の IoC より汎用的という中間的な抽象度が、検知や演習の共通語彙として普及した理由である [1]。サーベイのうち、Roy ら [3] は実装・評価研究の必要性を指摘し、Jiang ら [5] は有効性や検証方法を含む現状の限界を整理している。また、CALDERA 等の敵対者エミュレーションは技術を実行可能な手順として繰り返し再現でき、再現可能な測定の前提となる [2][要確認]。ただし、これらは土台であって検知性能の証拠ではない。ATT&CK に載っていることは、検知できることを意味しない。

### 3. 層 B:検知評価 (Empirical Detection Evaluation: EDR and Detection Rules)
商用 EDR。MITRE Engenuity の評価は、実在の APT の攻撃チェーンを再現して各製品の結果を公開する標準的評価である。Shen ら [7] は、その提示が個別ステップの検知に偏り、攻撃全体の関連づけ能力が見えないことを指摘し、全体グラフに基づく分析を提案した。[6] も商用 EDR の評価研究である [要確認]。

批判:この系統は、(1) 対象が商用製品で、無償のオープンソース構成を扱わない、(2) 内部がブラックボックスで、検知の成立要因を再現・検証できない、(3) ベンダー参加型で、公開結果だけでは解釈が不十分(Shen らが追加手法を要したこと自体が証左)、という限界を持つ。

検知ルール。オープンソース検知は Sigma 等の共有ルールが中心である。Uetz ら [8] は Windows のプロセス生成ルール 292 件を実際に再現して検証し、38%(110 件)が完全に、7%(19 件)が部分的に回避可能であることを示した。ルールの存在は検知を保証しないため、カバレッジは「対応づけ」ではなく「実際の発火」で測るべきである。Shukla ら [10] は、冗長なルールが誤検知とアラート疲労を招くとして LLM による最適化を提案した。[9] もルール品質に関わる [要確認]。

批判:[8] は個別ルールかつプロセス生成に限られ、ATT&CK 全体を対象としない。[10] は重複を扱うが、ATT&CK 網羅や実攻撃での発火は測っていない。

統合。両者を統合すると次の構図になる。

| 観点 | 商用 EDR 評価 [6][7] | ルール品質研究 [8][10] | 本プロジェクト |
|---|---|---|---|
| 対象 | 製品 | 個別ルール・ルール集合 | OSS 検知スタック |
| ATT&CK 実測 | あり | 部分的 | あり |
| 再現可能性 | 低い | 研究により異なる | 環境・手順・版を固定 |

前者は ATT&CK 上の実測を持つが再現できず、後者はオープンだが ATT&CK 全体の実測を持たない。両者の間を埋める研究は、このレビューの範囲では確認できなかった。

### 4. 層 C:標準・実務(灰色文献) (Standards and Practice)
SCYTHE の PTEF [11] はパープルチーム演習の計画・実施・改善を再利用可能な形式で公開しており、評価手順設計の実務的な参照枠になる。Red Canary の報告 [13] は実環境で頻出する ATT&CK 技術を毎年示し、評価対象を優先づける根拠になるが、方法論の厳密さは査読文献ほど保証されない。

### 5. ギャップ
文献から 3 点が示される。(1) 評価は商用製品に偏る [7]。(2) ルール研究は個別ルールの回避耐性 [8] や重複 [10] を扱うが、検知スタックの ATT&CK 網羅は測っていない。(3) 再現可能性が欠けている。オープンソース構成について、環境・手順・ルール版を固定して再測定できる結果は見当たらない。

したがって、オープンソース検知スタックの ATT&CK 網羅を再現可能に測定した研究は乏しい。本プロジェクトは、敵対者エミュレーションで技術を自動実行し、検知可否を固定した環境・手順で測定することで、このギャップに取り組む。

### 参考文献(作業用・最終版はセクション07へ)
- [1] MITRE, MITRE ATT&CK: Design and Philosophy (PRS 19-01075).
- [2] ICAPS 2022 デモ論文 (paper 375) [著者・題名を要確認].
- [3] Roy, S. et al. (2023). SoK: The MITRE ATT&CK Framework in Research and Practice. arXiv:2304.07411.
- [4] ACM, doi:10.1145/3687300 [書誌を要確認].
- [5] Jiang, Y. et al. (2025). MITRE ATT&CK Applications in Cybersecurity and The Way Forward. arXiv:2502.10825.
- [6] doi:10.3390/jcp1030021 (J. Cybersecur. Priv.) [書誌を要確認].
- [7] Shen, X., Li, Z., Burleigh, G., Wang, L., Chen, Y. (2024). Decoding the MITRE Engenuity ATT&CK Enterprise Evaluation. ASIA CCS '24. doi:10.1145/3634737.3645012.
- [8] Uetz, R. et al. (2024). You Cannot Escape Me: Detecting Evasions of SIEM Rules in Enterprise Networks. USENIX Security '24.
- [9] SSRN abstract 6823718 [書誌を要確認].
- [10] Shukla, A. et al. (2025). RuleGenie: SIEM Detection Rule Set Optimization. arXiv:2505.06701.
- [11] SCYTHE, Purple Team Exercise Framework. https://github.com/scythe-io/purple-team-exercise-framework
- [13] Red Canary, Threat Detection Report. https://www.zscaler.com/resources/industry-reports/red-canary-2026-threat-detection-report.pdf
- (参考)[12] ProQuest docview/2658836337:内容未確認のため本文では未引用。
