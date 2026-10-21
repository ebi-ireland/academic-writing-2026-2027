# 提案書アウトライン + 語数配分(書き出し用)

> 各段落で「何を・どの順で言うか」を点で示したもの。点を自分の言葉で文に展開する。
> これは構造の支援であり本文ではない。AI 利用は Acknowledgements に申告する。
> 文献番号は reference_list_verified.md の No. に対応。

---

## 1. Title + Keywords(20 語 / 5 個)
→ `title-options.md` から選ぶ。

## 2. Introduction(500 語・配点 10%)
採点: 背景(3)/ 意義(3)/ 問題・目的(4)

- 段落1 Background(約 180 語)
  - ATT&CK は攻撃者の振る舞いを体系化した知識ベース(No.1)
  - 防御側は「自分が実際にどれを検知できているか」を体系的には把握できていない
  - 根拠に survey を一言(No.4)
- 段落2 Rationale / Significance(約 180 語)
  - 検知の盲点 = 実際の侵害がすり抜ける → 重要
  - 商用製品ですら見逃しが多いことが示されている(No.6)
  - オープンソースは誰でも使えるので、その実力を知る価値がある
  - サステナビリティ: 検知スタックの計算コストにも触れる(LO2)
- 段落3 Problem / Overarching Aim(約 140 語)
  - 問題: オープンソース検知スタックの ATT&CK 網羅を、再現可能に測った研究が乏しい
  - 全体目標: その網羅と盲点を、隔離ラボでの敵対者エミュレーションにより体系的に測る

## 3. Aims & Objectives(250 語・配点 10%)
採点: 全体目標(4)/ SMART 目標(6)

- Overall Aim(約 40 語・1 文)
  - 「オープンソース検知スタックの ATT&CK 網羅と盲点を、再現可能な形で測定・評価する」
- Objectives(各約 40 語・4〜6 個、すべて測定可能に)
  1. 隔離 VM ラボ(標的 + ログ収集 + SIEM + 実行 + 集計)を構築する
  2. 事前定義した技術群を公開テストで実行する
  3. 検知を 3 段階(Detected / Telemetry-only / Missed)で採点する枠を作る
  4. 戦術カテゴリ別の網羅と盲点を測定する
  5. (任意)検知できた技術の変種で頑健性を試す
  6. (LO2)ルール数と網羅の関係を見る
- メモ: 今学期 PoC の範囲と次学期の完全測定を分けて書く = achievable で加点

## 4. Literature Review(1500 語・配点 30%)※最重要
採点: 批判的評価(10)/ 最新動向(8)/ ギャップ(6)/ 出典(6)
語数配分: 導入 100 / 層A 300 / 層B 700 / 層C 200 / ギャップ 200

- 導入(100): このレビューが扱う範囲を一言
- 層A 理論の土台(300)
  - ATT&CK の枠組みと中間的な抽象度(No.1)
  - 敵対者エミュレーションと CALDERA(No.2)
  - 任意: Kill Chain / Pyramid of Pain を 1〜2 行
  - 批判の一言: これらは土台だが「検知評価の証拠」ではない
- 層B 中核 = 検知評価(700)← ここに一番字数を使う
  - 現状の全体像(No.4)
  - 商用 EDR の評価とその限界(No.6)= 評価が商用に偏る
  - ルールの回避・品質(No.8, No.9)= シグネチャ型は変種に弱い
  - 「並べる」ではなく「評価・統合」: 再現性に触れていない評価が多い、対象が商用中心、など
- 層C 標準・実務(200)※灰色文献と明記
  - MITRE Evaluations(No.11)/ SCYTHE PTEF(No.12)/ Red Canary(No.14)を 1 文ずつ
  - 「実務は進むが、学術的な再現可能な測定が追いついていない」
- ギャップ(200)
  - reading-map.md のギャップ文を自分の言葉で。全体目標につなげる

## 5. Methodology(750 語・配点 30%)※最重要
採点: 研究設計(8)/ 評価・成功指標(4)/ ツール(6)/ 倫理・法・環境(6)/ 正当化・実現可能性(6)
→ 中身は `methodology-decisions.md` で確定済。それを文に展開する。
語数配分の目安:
- Research Design & Methods(約 200): 実験・測定型。ラボ 5 部品。独立変数 = 技術、従属変数 = 検知結果。測定ループ。固定した Sysmon 設定(統制変数)。[決定 ①④]
- Evaluation & Success Measures(約 120): 3 段階の検知定義 + 戦術別の網羅・盲点。[決定 ③⑤]
- Tools & Techniques(約 150): Wazuh / Sigma / Sysmon / Atomic Red Team / ATT&CK Navigator / Git を各々正当化。[決定 ②]
- Software development methodology(約 60): インクリメンタル(増分で PoC を作る)
- Ethical / Legal / Environmental(約 120): 隔離ラボ・責任ある利用・計算コスト
- Justification & Feasibility(約 100): 自分の PC で成立・範囲を締める・今学期は PoC まで
- 末尾: Ethical approval 必要か(想定 No、Week5 倫理 WS で確認)

## 6. Project Plan / Resources(400 語・配点 10%)
採点: タイムライン(6)/ 体裁(4)
語数配分: タイムライン 250 / 資源 100 /(図は別途)

- タイムライン(週マイルストーン)
  - ~Wk6 提案書 / Wk7-8 ラボ構築 / Wk9-10 測定と採点 / Wk11 仕上げ・デモ用 / Wk12 報告・デモ提出
- 資源
  - ソフト: VirtualBox, Atomic Red Team, Wazuh, Sysmon, Sigma, ATT&CK Navigator, Git/GitHub Projects
  - ハード: 自分の PC(i7-8650U / RAM 24GB)。学科からの貸与は不要(No)
  - データ: ATT&CK、公開テスト
- 図: Gantt もしくは Kanban を 1 枚(下の Kanban カード案を使う)

### Project Plan 用 Kanban カード案(GitHub Projects などに入れる)
列: Backlog / To Do / In Progress / Done
カード(マイルストーン付き):
- 提案書を書く・提出(CA1, ~10/23)
- ラボ VM を構築(標的 + Sysmon)
- Wazuh を立てログを取り込む
- 公開テストを実行できるようにする
- 検知を 3 段階で採点する仕組み
- 戦術別の網羅を集計
- ATT&CK Navigator でヒートマップ
- 盲点リストを作る
- 技術報告(CA2)を書く
- デモ動画・計画(CA3)
各カードに Target date と Risk(高/中/低)フィールドを足す。

## 7. References(Harvard UL・上限なし)
採点: 参照(3, Presentation に含む)
→ `zotero_reference_list.md` と Zotero から生成。下の型に合わせて確認。

### Harvard UL の型(見本・要確認)
会議論文の例(No.8):
Uetz, R., Herzog, M., Hackländer, L., Schwarz, S. and Henze, M. (2024) You Cannot Escape Me: Detecting Evasions of SIEM Rules in Enterprise Networks, Proceedings of the 33rd USENIX Security Symposium, USENIX Association. Available: https://www.usenix.org/conference/usenixsecurity24/presentation/uetz [21 October 2026].

技術報告の例(No.1):
Strom, B.E., Applebaum, A., Miller, D.P., Nickels, K.C., Pennington, A.G. and Thomas, C.B. (2020) MITRE ATT&CK: Design and Philosophy, The MITRE Corporation. Available: https://attack.mitre.org/docs/ATTACK_Design_and_Philosophy_March_2020.pdf [21 October 2026].

注: 正確な体裁は UL "Cite it Right" ガイドと Zotero の出力で最終確認する。
