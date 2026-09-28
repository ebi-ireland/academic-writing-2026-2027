# 文献リスト(Web検索で実在確認)— 案A パープルチーム型検知評価

使い方:
1. まず「アンカー」(No.4)を読む=分野の地図。参考文献をたどれば芋づる式に増える(スノーボール法)。
2. 中核(層B)を優先して読む。特に No.7・No.9 はあなたの仮説に直結。
3. 引くのは「自分が読んだもの」だけ。書誌の正確な著者/年/DOIは引用前に最終確認。
4. 査読=peer-reviewed、灰色=査読なしだが権威ある実務/標準文書。灰色は「査読ではない」と明記して使う。

## 格の内訳(正直な分類)
- 【格1 査読・強い】No.8(USENIX Security 2024), No.4(ACM Computing Surveys 2024),
  No.2(ACSAC 2016), No.7(ACM AsiaCCS 2024), No.6(J. Cybersecurity and Privacy, MDPI査読誌)
- 【格2 権威ある企業/技術報告(査読ではないが学術で多数引用)】No.1(MITRE), No.11(MITRE Engenuity), No.14(Red Canary)
- 【格3 プレプリント(未査読・要確認、掲載済みなら格上げ)】No.3, No.5(arXiv), No.9(SSRN), No.10(arXiv)
- 【格4 実務フレーム(灰色・明示して控えめに)】No.12(SCYTHE PTEF), No.13(GitHub・最弱=使うなら慎重に)
- 【ブログ級(任意・本文の主張の土台にしない)】Pyramid of Pain。Cyber Kill Chainは企業白書(灰色だが多数引用)
→ 骨格は格1+格2で組む。格3は指導教員が可なら使い掲載先を確認。格4は少数を灰色と明記。ブログ級は避けるか概念紹介に留める。

═══════════════════════════════════════════════════════════
## 層A: 理論・枠組みの土台

1. Strom, B. et al. "MITRE ATT&CK: Design and Philosophy." MITRE, 2018(2020改訂). [灰色/権威]
   URL: https://attack.mitre.org/docs/ATTACK_Design_and_Philosophy_March_2020.pdf
   使いどころ: ATT&CKを研究の枠組みとして導入する。

2. Applebaum, A. et al. "Intelligent, Automated Red Team Emulation." ACSAC 2016, pp.363-373. [査読]
   使いどころ: 敵対者エミュレーションの自動化(CALDERA)の学術的根拠。手法実行の方法論。
   関連: CALDERA "A Red-Blue Cyber Operations Automation Platform" ICAPS 2022(デモ論文)
   URL: https://icaps22.icaps-conference.org/demos/ICAPS_2022_paper_375.pdf

(任意の古典・要確認)
- Hutchins, Cloppert & Amin "Intelligence-Driven Computer Network Defense"(Cyber Kill Chain, Lockheed Martin 2011)[灰色]
- Bianco, D. "The Pyramid of Pain"(検知の頑健性の概念)[灰色/ブログ]

═══════════════════════════════════════════════════════════
## 層B: 中核 — 検知カバレッジ/評価(主戦場)

3. Roy, S., Panaousis, E. et al. "SoK: The MITRE ATT&CK Framework in Research and Practice."
   arXiv:2304.07411, 2023. [プレプリント/著名研究者だが査読掲載は未確認=要確認]
   URL: https://arxiv.org/pdf/2304.07411
   使いどころ: ATT&CK研究の体系化。現在の知見とギャップの整理。掲載先をDBLPで要確認。

4. ★アンカー★ "MITRE ATT&CK: State of the Art and Way Forward." ACM Computing Surveys, 2024. [査読]
   DOI: 10.1145/3687300  URL: https://dl.acm.org/doi/10.1145/3687300
   使いどころ: 分野の全体像。ここの参考文献からスノーボール。

5. "MITRE ATT&CK Applications in Cybersecurity and The Way Forward." arXiv:2502.10825, 2025. [システマティックレビュー]
   URL: https://arxiv.org/pdf/2502.10825
   使いどころ: 417本の査読論文をレビューした最新の全体像。トレンドの裏づけ。

6. Karantzas, G. & Patsakis, C. EDR評価(商用EDR11製品をAPTシナリオで評価). J. Cybersecurity and Privacy, 2021. [査読]
   使いどころ: 「商用EDRですら大半の攻撃を検知/記録しない」。★ギャップの核:評価は商用中心。

7. "Decoding the MITRE Engenuity ATT&CK Enterprise Evaluation: An Analysis of EDR Performance." ACM AsiaCCS 2024. [査読]
   DOI: 10.1145/3634737.3645012  URL: https://dl.acm.org/doi/10.1145/3634737.3645012
   使いどころ: EDR評価の分析。評価方法論の参考。

8. ★H2の核★ Uetz, R. et al. "You Cannot Escape Me: Detecting Evasions of SIEM Rules in Enterprise Networks."
   USENIX Security Symposium 2024. [査読・トップ会議・Distinguished Artifact Award受賞]
   URL: https://www.usenix.org/conference/usenixsecurity24/presentation/uetz
   使いどころ: 292のSigmaルール中110が完全回避可能・19が部分回避可能と実証。仮説H2を直接裏づけ。最強の1本。

9. ★H3関連★ Tyagi, N. "Static Quality Assessment of Sigma Detection Rules: Framework and Empirical Evaluation." SSRN, 2026.
   URL: https://papers.ssrn.com/sol3/papers.cfm?abstract_id=6823718
   使いどころ: SigmaHQ全3,132ルールを6次元で品質評価。ルールの質と量の議論(H3)。

10. "RuleGenie: SIEM Detection Rule Set Optimization." arXiv:2505.06701, 2025. [任意]
    URL: https://arxiv.org/pdf/2505.06701
    使いどころ: 2,347 Sigma / 1,640 Splunkルールで冗長ルールを特定。少数精鋭=H3(持続可能性)。

═══════════════════════════════════════════════════════════
## 層C: 標準・実務(灰色文献と明示して使う=現在性で加点)

11. MITRE Engenuity ATT&CK Evaluations(EDR評価の方法論・結果)[灰色/権威]
    URL: https://attack.mitre.org/resources/adversary-emulation-plans/

12. SCYTHE "Purple Team Exercise Framework (PTEF)"(パープルチーム実施の公開標準)[灰色/実務]
    URL: https://scythe.io/ptef

13. Olsen, X. "Enterprise Purple Teaming: An Exploratory Qualitative Study" [実務/質的研究]
    URL: https://github.com/ch33r10/EnterprisePurpleTeaming

14. Red Canary "Threat Detection Report"(年次・手法の実観測)[灰色]

(標準・要確認で追加候補)
- NIST SP 800-94(侵入検知・防止ガイド)[標準]
- ENISA Threat Landscape(欧州・年次)[灰色/権威]

═══════════════════════════════════════════════════════════
## ツールのドキュメント(方法論の根拠として)
- Sigma(SigmaHQ): https://github.com/sigmahq/sigma
- Atomic Red Team(Red Canary): 手法の再現テスト集
- Wazuh: オープンソースSIEM/XDR 公式ドキュメント

═══════════════════════════════════════════════════════════
## この文献群でギャップ文がこう書ける
「商用EDRの評価(No.6,7)や、ルール品質・回避の個別研究(No.8,9)はあるが、
 オープンソース検知スタック全体のATT&CK網羅を、再現可能な形で体系的に測った研究は乏しい。」
= あなたの研究が埋める穴。

## 注意
- 正確な著者名・年・掲載先・DOIは引用前にDBLP/掲載サイトで最終確認する。
- arXivプレプリントは指導教員に「文献として数えてよいか」を確認(加点方式なら通常可)。
- この文献探しにAIを使ったことはAcknowledgementsに申告する。
