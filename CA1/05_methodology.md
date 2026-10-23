# 05 Methodology(本文を書くファイル)※最重要
対応: Proposal の Methodology(最大 750 語・配点 30%)
採点: 研究設計(8)/ 評価・成功指標(4)/ ツール(6)/ 倫理・法・環境(6)/ 正当化・実現可能性(6)

## English(提出版・Word フォーム本文)

Research Design Methods
This study is an experiment and measurement study. Existing detection methods are not compared with each other. Instead, attack techniques are reproduced in a controlled environment, and the detection result for each technique is measured. The independent variable is the ATT&CK technique, and the dependent variable is the detection result.

The isolated lab on a personal PC has five parts:
A victim Windows VM
Sysmon, which collects telemetry
A Wazuh agent
A Wazuh manager
Atomic Red Team, which reproduces the attacks

The measurement repeats the following loop. (1) Select a target technique. (2) Run the technique with Atomic Red Team. (3) Record the Sysmon logs, the rule matches, and the Wazuh alerts. (4) Judge and record the result, then move to the next technique. The Sysmon configuration is fixed for all trials and treated as a controlled variable. Therefore, differences in results come from the techniques and rules, not from the configuration.

Evaluation & Success Measures
After each run, the result is diagnosed in three stages:
Stage 1: the activity is recorded in the Sysmon logs.
Stage 2: a Sigma rule matches the log.
Stage 3: an alert appears in Wazuh.
If Stage 3 is reached, the result is detected. If Stage 1 is reached but Stage 3 is not, the result is telemetry-only. If Stage 1 is not reached and no log is produced, the result is missed.

The successful measures are the overall detection rate, the coverage by ATT&CK tactic, and the identification of blind spots. There are two types of blind spot. Telemetry-only is a rule gap: a log is produced, but no rule detects the activity. A rule gap is fixed by adding rules. Missed is a visibility gap: the activity never appears in the logs. A visibility gap is fixed by reviewing the telemetry settings. This distinction is the main strength of the evaluation. The results are shown in colour in ATT&CK Navigator. The project succeeds if blind spots are shown with evidence and the same procedure can reproduce the results.

Tools & Techniques
Wazuh is an open-source platform that handles log collection, rule evaluation, and alerts together. Wazuh runs on a personal PC at no cost.
Sigma is a vendor-neutral rule format that shows the source and target technique of each rule, which improves reproducibility.
Sysmon provides the detailed Windows telemetry that detection needs, such as process creation and network connections.
Atomic Red Team offers small tests that map one-to-one to ATT&CK techniques. These tests suit measurement per technique.
ATT&CK Navigator shows tactic coverage and blind spots at a glance.
GitHub controls the versions of the configuration, rules, results, and scripts. This keeps the work history.
GitHub Projects (Kanban) manages the trial of each technique and each increment as tasks in the same place as the repository.

Software Development Methodology
This project uses incremental development. First, a minimal proof of concept (PoC) is built, in which one technique goes through one full cycle of run, record, and judge. After that, more techniques and tactics are added in small steps. At the end of each increment, the results are checked and the next scope is decided. This keeps rework small and progress easy to check.

Ethical, Legal & Environmental Considerations
All attack reproduction is done in a lab that is isolated from external networks. This study does not touch the systems or data of any real organisation, and no personal data is handled. All tools are public, legitimate tools, and the licence terms are followed. This study is limited to evaluating the detection ability of defenders. The results will not include details that could help misuse. This study evaluates not only detection performance but also computational cost and resource consumption, thereby incorporating the perspective of sustainable detection.


Justification & Feasibility
This project runs on a personal PC, so no extra cost or outside permission is needed. The scope is limited to a small set of techniques and tactics, and the goal for this semester is to complete the PoC. Rather than narrowing the scope, the project prioritises the accuracy and reproducibility of the measurements.

Ethical Approval
The study does not collect data from people, so ethics review is expected to be unnecessary. This point will be confirmed at the ethics workshop.

Does this project require ethical approval?      Yes ☐        No ☒

---

## 日本語下書き(英訳前・作業中)

### Research Design & Methods(目安 約200語)
本研究は実験・測定型とする。既存の検知手法を他手法と比較するのではなく、同一の統制環境で攻撃技術を再現し、その検知結果を測定する。独立変数はATT&CKの攻撃技術(Atomic Red Teamのテスト)、従属変数は各技術に対する検知結果である。

検証環境は、自分のPC上に構築する隔離ラボで、次の5部品から成る。
- 被害Windows VM(攻撃対象の仮想マシン)
- テレメトリ収集用のSysmon
- Wazuhエージェント
- Wazuhマネージャ(検知・アラート基盤)
- 攻撃再現ツールのAtomic Red Team

測定は次のループで繰り返す。(1)対象技術を選ぶ、(2)Atomic Red Teamで実行する、(3)Sysmonログ、ルール一致、Wazuhアラートを記録する、(4)結果を判定して記録し、次の技術へ進む。Sysmonの設定は全試行で固定し、統制変数として扱う。これにより、検知結果の差が設定の違いではなく技術とルールの差に由来することを担保する。

### Evaluation & Success Measures(目安 約120語)
各技術の実行後、観測がどの段階まで進むかを次の3段階で診断する。
- 段階1(テレメトリ):実行の痕跡がSysmonログに記録される
- 段階2(ルール一致):Sigmaルールがそのログに一致する
- 段階3(アラート):Wazuh上でアラートとして提示される

判定は到達した段階で決める。段階3に到達すれば Detected、段階1には到達するが段階3に至らなければ Telemetry-only、段階1に到達しなければ(ログが出なければ) Missed とする。

成功指標は、全体の検知率に加え、ATT&CKの戦術別の網羅率と盲点の特定とする。盲点は2種類に区別する。Telemetry-onlyはルール欠落(ログは出るが検知ルールがない)で、ルールの追加で対処する。Missedは可視性欠落(そもそもログに現れない)で、テレメトリ設定の見直しで対処する。この区別が本研究の評価の強みとなる。結果はATT&CK Navigator上で色分けして可視化する。盲点が根拠付きで示されること、および同一手順で再現できることを、本プロジェクトの達成基準とする。

### Tools & Techniques(目安 約150語)
各ツールは目的に即して選定した。
- Wazuh:オープンソースで、ログ収集・ルール評価・アラートを一つの基盤で扱える。自分のPCで稼働でき、費用もかからない。
- Sigma:ベンダー非依存の検知ルール形式で、ルールの出典と対象技術が明確になり、評価の再現性を高める。
- Sysmon:プロセス生成やネットワーク接続など、検知に必要な詳細なWindowsテレメトリを提供する。
- Atomic Red Team:ATT&CKの技術に1対1で対応する小規模なテストを提供し、技術単位の測定に適する。
- ATT&CK Navigator:戦術別の網羅と盲点を一目で示せる。
- Git(GitHub):設定、ルール、結果、スクリプトをバージョン管理し、再現性と作業履歴を確保する。
- GitHub Projects(Kanban):技術ごとの試行と増分の進捗をタスクとして管理し、リポジトリと同じ場所で追跡できる。

### Software Development Methodology(目安 約60語)
インクリメンタル開発を採用する。最初に1つの技術で「実行→記録→判定」の一巡が動く最小のPoCを作り、その後に対象技術と戦術を増分で広げる。各増分の終わりに結果を確認して次の範囲を決めるため、手戻りが小さく、学期中の進捗も確認しやすい。

### Ethical, Legal & Environmental Considerations(目安 約120語)
攻撃の再現はすべて、外部ネットワークから隔離したラボ内で行う。実在の組織のシステムやデータには触れず、個人情報も扱わない。使用するツールはいずれも公開された正規のものであり、ライセンス条件を遵守する。本研究は防御側の検知力を評価する目的に限定し、結果の公開では悪用を助長する詳細を載せない責任ある取り扱いを行う。環境面では、本研究は検知性能だけでなく計算コスト・資源消費も評価し、持続可能な検知の観点を含める。

### Justification & Feasibility(目安 約100語)
全体が個人のPC上で完結するため、追加の費用や外部の許可に依存せず、実現可能である。範囲は対象とする技術と戦術を絞って限定し、今学期はPoCの完成までを目標とする。範囲を絞る代わりに、測定の厳密さと再現性を優先する。

### Ethical Approval(目安 約20語)
人を対象とするデータ収集を行わないため、倫理審査は不要と想定する。この点は第5週の倫理ワークショップで確認する。
