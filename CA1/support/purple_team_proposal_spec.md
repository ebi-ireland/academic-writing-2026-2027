# 提案書 具体化スペック — パープルチーム型(検知網羅・盲点の測定)

方向: 隔離VMラボでATT&CK手法を実行(オフェンシブ)し、オープンソース検知スタックの
検知網羅と盲点を測定(ディフェンシブ)。攻撃=刺激 / 貢献=検知側の測定。

作業メモ: [   ]=自分の言葉で埋める。>>=書き方のヒント。◎=配点が重い。
GenAI境界: 本文はあなたが書く。この設計図はブレスト/構造まで。

═══════════════════════════════════════════════════════════
## 1. Title (max 20 words) + Keywords (max 5)
- Title: [   ]
  >> 方向例: Measuring Detection Coverage and Blind Spots of Open-Source Security
  >>         Tooling Against MITRE ATT&CK: A Purple-Team Approach
- Keywords: [   ] / [   ] / [   ] / [   ] / [   ]
  >> 例: purple teaming, MITRE ATT&CK, detection engineering, adversary emulation, SOC

═══════════════════════════════════════════════════════════
## 2. Introduction (max 500 words)  ── 配点10%
- Background/Context: [   ]
  >> 攻撃手法はATT&CKで体系化済み。しかし防御側は「自分が実際に何を検知できているか」を
  >>   知らないことが多い。SOCは持っていない検知を持っていると思い込みがち。
- Rationale/Significance: [   ]
  >> 検知の盲点=実際の侵害がすり抜ける。パープルチームがこれを閉じる実務。
  >> ★LO2(サステナビリティ): 検知スタックは重い。少ないルールで網羅を取れないかという論点。
- Problem/Overarching Aim: [   ]
  >> 「オープンソース検知スタックのATT&CK網羅と盲点を、再現可能な形で体系的に測る」。

═══════════════════════════════════════════════════════════
## 3. Aims & Objectives (max 250 words)  ── 配点10%
- Overall Aim(1文): [   ]
- Objectives(SMART, 4-6):
  1. [   ] >> 隔離VMラボを構築する(攻撃VM・被害VM・収集/検知)
  2. [   ] >> 事前定義したATT&CK手法群を Atomic Red Team で実行する
  3. [   ] >> テレメトリを収集し、検知の有無を採点する枠組みを作る
  4. [   ] >> 検知率・見逃し・戦術カテゴリ別の網羅を測定する
  5. [   ] >> (発展)未検知手法に簡単な変種を作り、検知の頑健性を試す
  6. [   ] >> (LO2)ルール数と網羅の関係を測り、少ルールでの網羅を検討する
>> ★今学期PoC範囲と次学期の完全測定を分けて書く=achievableで加点。

═══════════════════════════════════════════════════════════
## 4. Literature Review (max 1500 words)  ── 配点30% ◎最重要
採点: Critical Evaluation(10)/Current Knowledge&Trends(8)/Gaps(6)/Use of Sources(6)
3層で構成:
- (A) 理論の土台 [   ]
  >> MITRE ATT&CK(手法の分類体系)/ パープルチームの概念 / 検知エンジニアリングと
  >>   detection-as-code(Sigma)/ 敵対者エミュレーション(Atomic Red Team, CALDERA)/
  >>   "assume breach" / Pyramid of Pain(検知の頑健性の考え方)。
- (B) 中核: 検知網羅の評価 [   ]
  >> 検知カバレッジ評価やEDR/IDS評価の研究、SIEM検知のギャップ、
  >>   検知の回避(案4と地続き)。掲載先と年はDBLP/公式で確認。
- (C) 標準・実務(灰色文献と明示) [   ]
  >> MITRE ATT&CK Evaluations、Sigma公式、NIST/ENISAの検知ガイド、ベンダー報告。
- Gaps(必ず1段落) [   ]
  >> 「有償EDRの評価は多いが、オープンソース検知スタックの網羅を**再現可能に**
  >>   体系測定した研究が薄い」= 本研究が埋める穴。
>> 1500語厳守。時間配分も最大に。

═══════════════════════════════════════════════════════════
## 5. Methodology (max 750 words)  ── 配点30% ◎最重要
採点: Research Design(8)/Evaluation&Success(4)/Tools(6)/Ethical-Legal-Environmental(6)/Justification&Feasibility(6)

- Research Design & Methods: [   ]
  >> 実験・測定型。ラボ構成(攻撃VM / 被害VM / 収集・検知)。手法を実行→収集→採点。
  >> 独立変数=ATT&CK手法(と変種)、従属変数=検知有無・アラート品質。
- Evaluation & Success Measures: [   ]  ← 4点だが忘れやすい
  >> 検知率 / 見逃し(false negative)/ 戦術別の網羅 /(発展)変種での回避成功。
  >> 「検知できた」の定義を先に固める(アラート発火+正しい手法マッピング)。
- Tools & Techniques: [   ]
  >> VirtualBox/VMware、Atomic Red Team、Sysmon、Wazuh/Sigma/Suricata、
  >>   Elastic/OpenSearch、Git/GitHub Projects、テスト(TDD/BDD)。なぜ各々か。
- Software development methodology: [   ]
  >> インクリメンタル。可能ならラボをコード化(Vagrant/Ansible)で再現性↑。
- Ethical/Legal/Environmental: [   ]  ← 6点。◎ここを厚く。
  >> 倫理: 隔離ラボのみ・外部ネット遮断・自分の環境のみ・実マルウェア検体は使わない
  >>       (Atomic Red Teamはまさにこの用途の公開ツール)。
  >> 法: 攻撃は自ラボ内に限定。
  >> 環境(LO2): 検知スタックの計算コストを測り、少ルールでの網羅を検討=持続可能性。
- Justification & Feasibility: [   ]
  >> VMで成立・GPU不要。手法群を事前定義して範囲を締める。今学期はPoCまで。
- Ethical approval 必要? Yes / **No(想定)**  >> Week5倫理WSで最終確認。
>> 750語厳守。5項目を全部カバー(1つ欠けると失点)。

═══════════════════════════════════════════════════════════
## 6. Project Plan / Resources (max 400 words)  ── 配点10%
- Timeline(週マイルストーン): [   ]  >> Week1-12計画を流用(下に対応表)。
- Resources: [   ]
  >> ソフト: VirtualBox, Atomic Red Team, Wazuh/Sigma/Suricata, Sysmon, OpenSearch。
  >> ハード: ホストのRAMが肝(目安16GBで快適/8GBは軽量構成)。データ: ATT&CK手法。
- ハードウェア貸与を要求? Yes / No
  >> RAM不足なら「学科からRAM増設機/ラボPCを借りる」か、代替(単一VM+ホスト型エージェント
  >>   /コンテナ/クラウド無料枠)を明記。
>> 400語厳守。Gantt/Kanban図で見やすさ加点。

═══════════════════════════════════════════════════════════
## 7. References (Harvard UL, 上限なし)  ── 体裁10%の一部
- [   ] DBLP/公式で掲載先・年を確認して記載。

═══════════════════════════════════════════════════════════
# 仮説(方法論・考察で使う)
- H1: 検知スタックは一部の戦術(実行・永続化の既知手法)はよく検知するが、
      別の戦術(防御回避・認証情報アクセス)に体系的な盲点を持つ。
- H2: 手法にわずかな変種(難読化・別手順)を加えると、シグネチャ型検知は
      振る舞い型検知より容易に回避される。
- H3(LO2): 検知網羅はルール数に比例して伸びず、少数の厳選ルールで大半の網羅が取れる。

# PoCの「完成」の定義(今学期の線・これ以上広げない)
- 隔離VMラボ: 被害VM1台 + Sysmon + Wazuh(またはSigmaをログにオフライン適用)+ 攻撃元
- ATT&CK手法 5-10個(2-3戦術)を Atomic Red Team で実行
- 検知の採点結果: どれを検知/どこが盲点、を手法別に出す
- 基本テスト(TDD/BDD)+ 生ログ保存 + コード/ラボ定義のタグ付け
→ 全手法網羅・複数ツール比較・変種回避の深掘りは**次学期**。

# リスク登録簿(CA3のProject Management加点にも直結)
| リスク | 兆候 | 対応 |
|---|---|---|
| RAM不足でVMが複数動かない | ラボ構築時に重い | 単一VM+ホスト型エージェント/コンテナ/学科貸与要求 |
| 手法を広げすぎる | Week10で未収集 | 事前定義の手法数で打ち切り |
| 「検知」の定義が曖昧 | 採点がぶれる | 採点ルーブリックを先に固定 |
| ツール構築が沼化 | Week9でラボ未完 | 既存のラボ・コード化テンプレを土台にする |
| 変種テストが沼化 | Week10で超過 | 変種は発展目標のみ・数を限定 |

# あなたが外部に確認すること
- [ ] ホストのRAM量(→ラボ構成が決まる)
- [ ] Week5倫理WSで、隔離ラボのみなら倫理審査不要か確定
- [ ] ワークショップ論文/arXivを文献に数えてよいか
- [ ] 「1万字」は後半学期の付属文書の話か

# Week1-12対応(既存計画の流用)
- W1-2: テーマ確定・文献の当たり・RAM確認 / DBLP裏取り
- W3: Sec1,2,3ドラフト  W4: Sec4,5,6ドラフト+Gantt  W5: 最終化+倫理WS+GitHub
- W6: 提出(10/23)
- W7 Inc0: ラボ構築(被害VM+Sysmon+収集)  W8 Inc1: 手法数個を実行し検知確認
- W9 Inc2: 検知採点の枠+盲点抽出  W10 Inc3: 手法追加/(発展)変種1種+テスト整備
- W11 Inc4: 仕上げ・デモ用データ・タグ付け  W12: デモ動画+報告提出(12/11)
