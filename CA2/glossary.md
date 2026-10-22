# Glossary of Terms — 学習用用語集

> 目的: 研究内容を理解するための学習用資料(Claude 作成)。
> 報告書(CA2)の Glossary / Acronyms に載せるときは、本文で実際に使う語だけを選び、定義は自分の言葉で書くか、出典(MITRE ATT&CK 公式、NIST CSRC Glossary、各ツールの公式ドキュメント)を付けること。
> 生成 AI で作った資料なので、使った場合は Acknowledgements に記録する。
> 版によって変わる情報(ATT&CK の技術数、ツールの機能など)は公式サイトで最新を確認する。

## 目次
(この版は第 1〜8 節まで)
1. MITRE と ATT&CK の基本
2. ATT&CK Enterprise の 14 戦術
3. 本研究で扱いそうな代表的技術
4. 脅威モデルと関連フレームワーク
5. チーム・演習の種類
6. 敵対者エミュレーションのツール
7. 検知・監視の基盤
8. ログとテレメトリ

---

## 1. MITRE と ATT&CK の基本

| 用語 | 意味 | 本研究とのつながり |
|---|---|---|
| MITRE | 米国の非営利研究機関。ATT&CK、CVE、CWE、CALDERA などを運営・開発している。 | 文献 No.1・No.2 の発行元 |
| MITRE ATT&CK (Adversarial Tactics, Techniques, and Common Knowledge) | 実際の攻撃の観測にもとづく、攻撃者の戦術と技術の知識ベース。無料で公開されている。 | 研究全体の枠組み。網羅を測る「物差し」 |
| Matrix(マトリクス) | 戦術を列、技術を行に並べた表。Enterprise(Windows・Linux・macOS・クラウド等)、Mobile、ICS の 3 領域がある。 | 本研究は Enterprise を使う |
| Tactic(戦術) | 攻撃者がその行動で達成したい目的(「なぜ」)。ID は TA0001 の形式。 | 戦術ごとの網羅を比較する(H1) |
| Technique(技術) | 目的を達成するための手段(「どうやって」)。ID は T1059 の形式。 | 実験の単位 |
| Sub-technique(サブ技術) | 技術をさらに細かく分けたもの。ID は T1059.001 の形式。 | どの粒度で測るかを決める必要がある |
| Procedure(手順) | 特定の攻撃者やマルウェアが、技術を実際にどう実装したかの具体例。 | Atomic テストは手順の一種と見なせる |
| TTP (Tactics, Techniques, and Procedures) | 戦術・技術・手順の総称。攻撃者の「振る舞い」を表す。 | 検知の対象を IoC ではなく TTP に置く根拠 |
| Group(グループ) | ATT&CK に記録された攻撃者集団(例: APT29)。ID は G0016 の形式。 | 敵対者エミュレーションの模倣対象 |
| Software(ソフトウェア) | 攻撃者が使うマルウェアやツール。ID は S0002 の形式。 | — |
| Campaign(キャンペーン) | 特定の期間に行われた一連の侵入活動。ID は C0001 の形式。 | — |
| Mitigation(緩和策) | 技術を防ぐための対策。ID は M1036 の形式。 | 検知ではなく予防側の情報 |
| Data Source / Data Component(データソース) | 技術を検知するために必要なログや情報の種類(例: Process Creation)。 | 「そもそもログがあるか」の確認に使う |
| ATT&CK Navigator | ATT&CK のマトリクスに色を付けて可視化する Web ツール。結果をレイヤー(JSON)として保存できる。 | 網羅のヒートマップ作成(スキル 4) |
| STIX / TAXII | 脅威情報を表す標準データ形式 / それを配信するプロトコル。ATT&CK は STIX 2.1 形式でも配布されている。 | スクリプトで ATT&CK データを読み込むとき |
| MITRE ATT&CK Evaluations | MITRE(Engenuity)が行う商用セキュリティ製品の検知評価。評価方法論が公開されている。 | 文献 No.7・No.11。評価方法の参考 |

---

## 2. ATT&CK Enterprise の 14 戦術

| ID | 戦術 | 意味 |
|---|---|---|
| TA0043 | Reconnaissance(偵察) | 標的の情報を集める |
| TA0042 | Resource Development(リソース開発) | 攻撃に使うインフラやアカウントなどを用意する |
| TA0001 | Initial Access(初期アクセス) | 標的のネットワークに最初に入り込む |
| TA0002 | Execution(実行) | 悪意あるコードを動かす |
| TA0003 | Persistence(永続化) | 再起動後も足場を保ち続ける |
| TA0004 | Privilege Escalation(権限昇格) | より高い権限を得る |
| TA0005 | Defense Evasion(防御回避) | 検知や防御を避ける |
| TA0006 | Credential Access(認証情報アクセス) | パスワードなどの認証情報を盗む |
| TA0007 | Discovery(探索) | 侵入した環境の情報を調べる |
| TA0008 | Lateral Movement(横展開) | ほかの端末へ移動する |
| TA0009 | Collection(収集) | 目的のデータを集める |
| TA0011 | Command and Control(C2) | 侵入先の端末を遠隔から操作するための通信 |
| TA0010 | Exfiltration(持ち出し) | データを外部へ送り出す |
| TA0040 | Impact(影響) | システムやデータを破壊・妨害・改ざんする |

メモ: PoC の被害 VM は 1 台なので、偵察・リソース開発(侵入前の段階)や横展開(複数の端末が必要)は対象外になりやすい。対象にする戦術と、外す理由を提案書の Scope に書く。

---

## 3. 本研究で扱いそうな代表的技術

防御側の視点で、何が起きるかと、どのログが手がかりになるかをまとめた。実際に選ぶ技術は、Atomic Red Team にテストがあり、1 台の VM で再現できるものから決める。

| ID | 技術 | 何が起きるか | 主な手がかりとなるログ |
|---|---|---|---|
| T1059 | Command and Scripting Interpreter | PowerShell やコマンドプロンプトなどのインタプリタでコマンドを実行する | プロセス作成、PowerShell ログ |
| T1059.001 | PowerShell | 上のうち PowerShell を使うもの | PowerShell Script Block Logging(4104) |
| T1053.005 | Scheduled Task | タスクスケジューラに登録して実行・永続化する | タスク作成のイベント、プロセス作成 |
| T1547.001 | Registry Run Keys / Startup Folder | ログオン時に自動で実行される場所に登録して永続化する | レジストリ変更(Sysmon 13) |
| T1003.001 | LSASS Memory | 認証情報を持つプロセス(LSASS)のメモリから資格情報を取り出す | プロセスアクセス(Sysmon 10) |
| T1082 | System Information Discovery | OS やハードウェアの情報を調べる | プロセス作成 |
| T1087 | Account Discovery | アカウントの一覧を調べる | プロセス作成 |
| T1070 | Indicator Removal | ログの消去など、痕跡を消す | 監査ログ消去(Security 1102) |
| T1027 | Obfuscated Files or Information | 内容を難読化・符号化して検知を逃れる | スクリプトログ、コマンドライン |
| T1036 | Masquerading | 正規のファイル名や置き場所に見せかける | プロセス作成(パスと名前の不一致) |
| T1218 | System Binary Proxy Execution | 署名付きの正規 Windows プログラムを経由して実行する | プロセス作成(親子関係) |
| T1021 | Remote Services | RDP や SMB などの正規のリモート機能で他の端末に入る | ログオン(Security 4624) |
| T1105 | Ingress Tool Transfer | 外部からツールを持ち込む | 通信、ファイル作成 |

---

## 4. 脅威モデルと関連フレームワーク

| 用語 | 意味 | 本研究とのつながり |
|---|---|---|
| Cyber Kill Chain | Lockheed Martin(2011)の攻撃ライフサイクルモデル。偵察 → 武器化 → 配送 → 攻撃 → インストール → C2 → 目的の実行、の 7 段階。 | ATT&CK より粗い「高レベルのライフサイクルモデル」の代表(Cornell ノート Ref 01 の要約) |
| Unified Kill Chain | Kill Chain と ATT&CK を統合し、段階を細かくしたモデル(Paul Pols)。 | 比較として触れる程度 |
| Pyramid of Pain | David Bianco(2013)の考え方。ハッシュ値 → IP → ドメイン → 痕跡 → ツール → TTP の順に、攻撃者にとって変えるのが「痛い」。上の層を検知するほど防御の価値が高い。 | 仮説 H2(シグネチャ型は変種に弱い)の理論的な土台 |
| Diamond Model | 侵入を「攻撃者・能力・インフラ・被害者」の 4 要素で分析するモデル。 | 脅威インテリジェンス側の概念として |
| Threat model(脅威モデル) | 攻撃者が誰で、何を、どこまでできるかを前提として決めたもの。 | 「攻撃者は被害 VM 上でコマンドを実行できる」などを提案書に明記する |
| Assume breach(侵害前提) | 「すでに侵入されている」と仮定して、内部での検知を考える姿勢。 | ATT&CK の出発点(Cornell ノート Ref 01) |
| MITRE D3FEND | 防御側の対策技術を体系化した知識グラフ。ATT&CK と対応づけられている。 | 防御側の語彙として |
| MITRE CAR (Cyber Analytics Repository) | ATT&CK に対応づけた検知アナリティクス(検知ロジック)の集まり。 | 検知ルールの参考源 |
| MITRE ATLAS | AI システムへの攻撃をまとめた知識ベース(ATT&CK の AI 版)。 | 対象外(関連領域) |
| CVE (Common Vulnerabilities and Exposures) | 個々の脆弱性に付く識別番号(例: CVE-2021-44228)。MITRE が運営。 | 本研究は脆弱性ではなく振る舞いを扱う、という対比に使える |
| CWE (Common Weakness Enumeration) | 脆弱性の「種類」の分類。 | — |
| CVSS (Common Vulnerability Scoring System) | 脆弱性の深刻度を数値で表す方式。 | — |
| NVD (National Vulnerability Database) | NIST が運営する脆弱性データベース。 | — |
| APT (Advanced Persistent Threat) | 長期間、高度な手口で特定の標的を狙う攻撃者(国家系など)。 | ATT&CK の Group の多くがこれにあたる |
| Threat actor / Threat group | 攻撃を行う主体。 | — |
| CTI (Cyber Threat Intelligence) | 攻撃者や手口について分析された情報。 | ATT&CK の用途の 1 つ(Threat intel enrichment) |

---

## 5. チーム・演習の種類

| 用語 | 意味 | 本研究とのつながり |
|---|---|---|
| Red team | 攻撃者の立場で防御を試すチーム。 | — |
| Blue team | 防御・検知・対応を担うチーム(SOC など)。 | — |
| Purple team / Purple teaming | Red と Blue が協力し、攻撃を実行しながら検知を確かめて改善する進め方。 | 本研究の手法 |
| Adversary emulation(敵対者エミュレーション) | 特定の実在グループの TTP を再現して防御を試すこと。 | Cornell ノート Ref 01 |
| Adversary simulation | 攻撃者の振る舞いを模擬すること全般。エミュレーションとの使い分けは文献によって異なる。 | 用語の定義を本文で明確にする |
| Penetration testing(ペネトレーションテスト) | 脆弱性を突いて侵入できるかを確かめる試験。目的は「入れるか」。 | 本研究は「入れるか」ではなく「検知できるか」を測る点で異なる |
| BAS (Breach and Attack Simulation) | 攻撃の模擬を自動で継続的に実行し、防御を検証する製品群。 | 商用の類似アプローチ |
| Threat hunting(脅威ハンティング) | アラートを待たず、仮説を立てて能動的に侵入の痕跡を探す活動。 | — |
| PTEF (Purple Team Exercise Framework) | SCYTHE が公開したパープルチーム演習の進め方。 | 文献 No.12 |
| Atomic testing | 1 つの技術を、小さく単独で試すテスト。 | Atomic Red Team の考え方 |
| Engagement | Red team などの 1 回の実施(案件)。 | Cornell ノート Ref 02 |
| Tabletop exercise | 机上で、事態の進み方を議論する演習。 | — |

---

## 6. 敵対者エミュレーションのツール

| 用語 | 意味 | 本研究とのつながり |
|---|---|---|
| Atomic Red Team | Red Canary が公開している、ATT&CK の技術ごとの小さなテスト集。テストは YAML で定義されている。 | PoC の攻撃側の主要ツール |
| Atomic test | 1 つの技術に対する 1 つのテスト。技術ごとに番号が付く(例: T1003.001 のテスト #1)。 | 実験の最小単位 |
| Invoke-AtomicRedTeam | Atomic テストを PowerShell から実行するモジュール。前提条件の確認、実行、後片付けができる。 | 自動化(スキル 3) |
| Prerequisites / Dependencies | テストを実行する前に必要な条件や準備。 | — |
| Cleanup command | テストの後に環境を元に戻すためのコマンド。 | 繰り返し実験の再現性 |
| Input arguments | テストに渡す値(ファイルパスなど)。変えると変種を作れる。 | H2 の変種づくりの入口 |
| CALDERA | MITRE のオープンソースの自動敵対者エミュレーション基盤。 | 文献 No.2 |
| Agent(エージェント) | 被害端末で動き、サーバーからの指示を受けるプログラム。CALDERA の標準は Sandcat(Go 製)。 | Cornell ノート Ref 02 |
| Ability(アビリティ) | エージェントが実行できる 1 つの動作。ATT&CK の技術に対応する。 | Cornell ノート Ref 02 |
| Adversary profile(敵対者プロファイル) | 模倣する攻撃者を、アビリティの組み合わせで定義したもの。 | Cornell ノート Ref 02 |
| Operation(オペレーション) | プロファイルとプランナーを選んで実行する 1 回の演習。 | Cornell ノート Ref 02 |
| Planner(プランナー) | どのアビリティをどの順番で実行するかを決める部品。 | Cornell ノート Ref 02 |
| Fact / Source | 実行中に集めた情報(ホスト名など)と、その初期値の集まり。後続のアビリティで使われる。 | — |
| Plugin | CALDERA の拡張機能。例: Stockpile(アビリティ集)、Atomic(Atomic Red Team の取り込み)、Response(防御側の自動対応)。 | — |
| Metasploit | 有名なペネトレーションテスト用フレームワーク。 | 本研究では使わない(比較の語彙) |
| Stratus Red Team | クラウド(AWS など)向けの Atomic 型テストツール。 | 対象外(クラウド) |

---

## 7. 検知・監視の基盤

| 用語 | 意味 | 本研究とのつながり |
|---|---|---|
| SOC (Security Operations Center) | 組織の監視・検知・対応を担う部署。Tier 1(一次対応)から Tier 3 に分かれることが多い。 | 就職先として想定する職場 |
| SIEM (Security Information and Event Management) | さまざまなログを集めて相関分析し、ルールでアラートを出す基盤。 | スキル 1。評価の中心 |
| EDR (Endpoint Detection and Response) | 端末上の振る舞いを監視し、検知・調査・対応する製品。 | 商用 EDR の評価研究(No.6・No.7)との対比 |
| XDR (Extended Detection and Response) | 端末・ネットワーク・クラウドなど複数の層をまたいで検知・対応する考え方。 | Wazuh は XDR を名乗っている |
| IDS / IPS | 侵入を検知するシステム / 検知して遮断まで行うシステム。 | — |
| NIDS / HIDS | 通信を見る IDS / 端末上の動きを見る IDS。 | Suricata は NIDS、Wazuh エージェントは HIDS 寄り |
| NSM (Network Security Monitoring) | 通信を記録・分析して監視すること。Zeek が代表例。 | — |
| SOAR (Security Orchestration, Automation and Response) | アラートへの対応を自動化し、ツール同士を連携させる仕組み。 | 対象外(関連語) |
| Wazuh | オープンソースのセキュリティ基盤(SIEM / XDR)。OSSEC から派生。構成は agent、server(manager)、indexer、dashboard。 | SIEM 候補(推奨) |
| Wazuh agent | 端末に入れて、ログや状態をサーバーへ送るプログラム。 | 被害 VM に入れる |
| Wazuh rules / decoders | ログを解釈する仕組み(decoder)と、アラートの条件(rule)。XML で書き、ATT&CK の ID を付けられる。 | 検知の判定に使う |
| Elastic Stack (ELK) | Elasticsearch(保存・検索)、Logstash(取り込み)、Kibana(可視化)の組み合わせ。Beats(Winlogbeat など)でログを送る。 | 代替候補・ダッシュボード(スキル 5) |
| OpenSearch | Elasticsearch から分岐したオープンソースの検索基盤。Wazuh indexer の土台。 | — |
| Splunk | 代表的な商用 SIEM。 | 求人でよく見る名前 |
| Microsoft Sentinel | Azure 上のクラウド SIEM。 | SIEM 候補(クラウド案) |
| Suricata | オープンソースの IDS / IPS / NSM エンジン(OISF)。 | ネットワーク側の検知 |
| Zeek | オープンソースのネットワーク監視ツール(旧称 Bro)。通信をログにする。 | 任意 |
| Kibana / Grafana | ダッシュボード・可視化ツール。 | スキル 5 |

---

## 8. ログとテレメトリ

| 用語 | 意味 | 本研究とのつながり |
|---|---|---|
| Telemetry(テレメトリ) | 端末やネットワークから得られる観測データの総称。 | — |
| Log source(ログ源) | ログの出どころ(Windows イベントログ、Sysmon、ファイアウォールなど)。 | — |
| Visibility(可視性) | 攻撃の痕跡が、そもそもログに記録されるかどうか。 | 「ログがない」盲点と「ルールがない」盲点を分ける鍵 |
| Sysmon (System Monitor) | Microsoft Sysinternals の無料ツール。Windows 上の細かな動きをイベントログに記録する。設定ファイル(XML)で記録対象を選ぶ。 | 被害 VM に入れる |
| Sysmon config | 何を記録するかの設定。SwiftOnSecurity 版や Olaf Hartong の sysmon-modular が有名。 | 設定次第で網羅が変わるため、統制変数として明記する |
| Sysmon Event ID 1 | Process Create(プロセス作成)。コマンドラインや親プロセスが分かる。 | 多くの検知の基本 |
| Sysmon Event ID 3 | Network Connection(通信)。 | — |
| Sysmon Event ID 7 | Image Loaded(DLL の読み込み)。 | — |
| Sysmon Event ID 8 | CreateRemoteThread(別のプロセスへのスレッド作成)。 | — |
| Sysmon Event ID 10 | Process Access(他のプロセスへのアクセス)。LSASS へのアクセスの検知に使われる。 | T1003.001 |
| Sysmon Event ID 11 | File Create(ファイル作成)。 | — |
| Sysmon Event ID 12 / 13 / 14 | レジストリの作成・削除 / 値の設定 / 名前の変更。 | T1547.001 |
| Sysmon Event ID 22 | DNS Query(名前解決)。 | — |
| Windows Security Event Log | Windows 標準の監査ログ。例: 4624 ログオン成功、4625 ログオン失敗、4688 プロセス作成、4720 アカウント作成、1102 監査ログの消去。 | — |
| Audit policy(監査ポリシー) | Windows がどのイベントを記録するかの設定。既定では記録されないものも多い。 | 設定を記録して再現性を確保する |
| PowerShell Script Block Logging | PowerShell で実行されたスクリプトの中身を記録する機能(Event ID 4104)。 | T1059.001 の検知に重要 |
| ETW (Event Tracing for Windows) | Windows の内部イベントを取り出す仕組み。EDR がよく使う。 | — |
| AMSI (Antimalware Scan Interface) | スクリプトなどを実行前にセキュリティ製品へ渡して検査させる Windows の仕組み。 | — |
| auditd | Linux の監査デーモン。システムコールなどを記録する。 | Linux を扱う場合 |
| Syslog | ログを送るための標準的な形式・仕組み(主に Linux やネットワーク機器)。 | — |
| Log normalization(正規化) | 形式の違うログを、共通の項目名にそろえること。 | Sigma を使う前提 |
| Retention(保存期間) | ログを保存しておく期間。 | — |
