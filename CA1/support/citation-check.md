# 引用 照合ワークシート(CA1 Proposal)— 本文順

本文の出現順に、引用のある文を一字一句そのまま並べた。各文の下に、置き換える (Author, year) を示す。
原典と突き合わせて主張が正しいか確認する。状態: ✓=内容確認済 / ?=要確認 / ⚠=要修正。

====================================================================
# 2. Introduction
====================================================================

(NO.4) ?
> Current assessments tend to be limited to metadata coverage, where rules are mapped to the ATT&CK framework. (NO.4)
- 置換: (NO.4) → (Al-Sada et al., 2024)
- 確認: 「評価はメタデータ網羅にとどまる」がサーベイにあるか(←一番要確認)

(NO.6) ✓
> It has been reported that even commercial products are not immune to such oversights. (NO.6)
- 置換: (NO.6) → (Karantzas and Patsakis, 2021)
- 確認: 商用EDRでも見逃しが多い(確認済・一致)

====================================================================
# 4. Literature Review — Foundation: ATT&CK and Adversary Emulation
====================================================================

(NO.1) ?
> ATT&CK is a knowledge base that systematically categorises (NO.1) the behaviour of adversaries observed into tactics and techniques.
- 置換: (NO.1) → (Strom et al., 2020)
- 確認: ATT&CKが行動を戦術・技術に分類(妥当な見込み)

(NO.3) ?  ※ナラティブ(著者が主語)
> Among the surveys, Roy et al. (NO.3) highlight the need for implementation and evaluation research, …
- 置換: Roy et al. (NO.3) → Roy et al. (2023)
- 確認: Royらが実装・評価研究の必要性を指摘

(NO.5) ⚠動詞抜け + ?  ※ナラティブ
> … whilst Jiang et al. (NO.5) the current limitations.
- 置換: Jiang et al. (NO.5) → Jiang et al. (2025)
- 要修正: 動詞が無い → 例 "Jiang et al. (2025) outline/review the current limitations."
- 確認: Jiangらが現状の限界を整理

(NO.2) ⚠位置がおかしい
> The fact that a technique is listed in ATT&CK (NO.2) does not mean it can be detected.
- 置換: (NO.2) → (Alford et al., 2022) … だが下記参照
- 要修正: (NO.2)=CALDERA はこの文の根拠にならない。直前の「CALDERA allow the technique to be repeatedly reproduced…」の文末に (Alford et al., 2022) を移す。この文は著者の主張なので引用無しでよい。

====================================================================
# 4. Literature Review — Commercial EDR
====================================================================

[7] ✓  ※ナラティブ
> Study [7] argues that the published results focus on the detection of individual steps.
> Study [7] therefore proposed an analysis based on whole-attack graphs.
- 置換: Study [7] → Shen et al. (2024)
- 確認: Engenuity評価の分析・全体グラフ分析を提案(確認済・一致)

[6] ✓(ただし弱い)
> Another study [6] also evaluates commercial EDR products.
- 置換: Another study [6] → Karantzas and Patsakis (2021)
- 補強案: 「商用EDRでも見逃しが多いことを示した」と実質化すると良い

--- Critique ---

[7] ✓
> The fact that study [7] needed an extra method supports this point.
- 置換: study [7] → Shen et al. (2024)

====================================================================
# 4. Literature Review — Detection rules
====================================================================

[8] ✓
> Study [8] tested 292 Windows process-creation rules by actually reproducing evasions. It found that 38% (110 rules) could be fully evaded and 7% (19 rules) could be partly evaded.
- 置換: Study [8] → Uetz et al. (2024)
- 確認: 292件中110件(38%)完全回避・19件(7%)部分回避(確認済・一致)

[10] ✓
> Study [10] argues that redundant rules cause false positives and alert fatigue, and it proposes optimising rules with an LLM.
- 置換: Study [10] → Shukla et al. (2025)
- 確認: 冗長ルール→誤検知/疲労、LLM最適化(確認済・一致)

[9] ?(弱い)
> Another study [9] also deals with rule quality.
- 置換: Another study [9] → Tyagi (2026)
- 補強案: 品質評価の具体を一文にすると良い

--- Critique ---

[8] ✓
> Study [8] covers individual rules and only process creation, so it does not cover ATT&CK as a whole.
- 置換: Study [8] → Uetz et al. (2024)

[10] ✓
> Study [10] deals with duplicate rules, but it does not measure ATT&CK coverage or rule firing against real attacks.
- 置換: Study [10] → Shukla et al. (2025)

====================================================================
# 4. Literature Review — Standards & Practice
====================================================================

[11] ?
> The SCYTHE Purple Team Exercise Framework [11] documents the planning, running, and improvement of purple team exercises in a reusable format.
- 置換: [11] → (SCYTHE, n.d.)

[13] ?
> The Red Canary report [13] lists the ATT&CK techniques that are most common in real environments every year.
- 置換: [13] → (Red Canary, 2026)

====================================================================
# 4. Literature Review — Gap
====================================================================

[7] ✓
> First, evaluation is biased toward commercial products [7].
- 置換: [7] → (Shen et al., 2024)

[8] ✓ / [10] ✓
> Second, rule studies address the evasion resistance of individual rules [8] and rule duplication [10], but they do not measure the ATT&CK coverage of a whole detection stack.
- 置換: [8] → (Uetz et al., 2024) / [10] → (Shukla et al., 2025)

====================================================================
# (Author, year) コピペ一覧(1–13)
====================================================================
括弧内形式(文末に付けるとき):
- [1]  (Strom et al., 2020)
- [2]  (Alford et al., 2022)
- [3]  (Roy et al., 2023)
- [4]  (Al-Sada et al., 2024)
- [5]  (Jiang et al., 2025)
- [6]  (Karantzas and Patsakis, 2021)
- [7]  (Shen et al., 2024)
- [8]  (Uetz et al., 2024)
- [9]  (Tyagi, 2026)
- [10] (Shukla et al., 2025)
- [11] (SCYTHE, n.d.)
- [12] (Olsen, 2022)   ← ただし本文で未引用。引くか、References から削除
- [13] (Red Canary, 2026)

ナラティブ形式(著者が主語のとき。年だけ括弧):
- [1]  Strom et al. (2020)
- [2]  Alford et al. (2022)
- [3]  Roy et al. (2023)
- [4]  Al-Sada et al. (2024)
- [5]  Jiang et al. (2025)
- [6]  Karantzas and Patsakis (2021)
- [7]  Shen et al. (2024)
- [8]  Uetz et al. (2024)
- [9]  Tyagi (2026)
- [10] Shukla et al. (2025)
- [11] SCYTHE (n.d.)
- [12] Olsen (2022)
- [13] Red Canary (2026)

====================================================================
# 要修正(まとめ)
====================================================================
1. (NO.2) CALDERA の位置 → 直前の CALDERA の文へ移す(末尾の文は引用不要)
2. [12] Olsen が本文未引用 → 引用するか References から削除
3. [5] Jiang の文に動詞を補う(outline / review the current limitations)
4. 引用形式を (NO.x)/[x] から上の (Author, year) に統一
