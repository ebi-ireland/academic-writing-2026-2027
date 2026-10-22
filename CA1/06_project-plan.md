# 06 Project Plan / Resources(本文を書くファイル)
対応: Proposal の Project Plan / Resources(最大 400 語・配点 10%)
採点: タイムライン(6)・体裁(4)

## 日本語下書き(英訳前・作業中)

### 1. タイムライン(週ごとのマイルストーン)
- Wk6:提案書の提出(CA1)。
- Wk7–8:ラボ構築。標的VM(Sysmon導入)とWazuhを構築してログを取り込み、Atomic Red Teamの公開テストを実行できる状態にする。成果物:テスト実行で検知ログを確認できるラボ。
- Wk9–10:測定と採点。公開テストを実行し、検知結果を3段階で採点する。戦術別の網羅率をATT&CK Navigatorでヒートマップにする。成果物:採点表、網羅率ヒートマップ。
- Wk11:盲点の整理と草稿。検知できなかった技術を盲点リストにまとめ、報告とデモの草稿を作る。時間があれば、Sigmaルールによる補強を任意で試す。成果物:盲点リスト、草稿。
- Wk12:技術報告(CA2)とデモ(CA3)を提出。

進捗はGitHub ProjectsのKanbanボードで管理し、各カードにTarget date(週)とRisk(高/中/低)を付ける。遅れやすいWazuhへのログ取り込みはWk8までに終え、測定の時間を確保する。完全な測定は次学期に継続する。

### 2. 資源
- ソフトウェア:VirtualBox、Atomic Red Team、Wazuh、Sysmon、Sigma、ATT&CK Navigator、Git/GitHub Projects。
- ハードウェア:自分のPC(Core i7-8650U、RAM 24GB)で足りるため、学科からの貸与は不要。性能が足りない場合は、VM台数を減らした軽量構成か、クラウド上のVMで代用する。
- データ:MITRE ATT&CKと公開テスト(Atomic Red Team)のみを使い、独自のデータ収集は行わない。

### 3. 図(Kanbanボード案)
列は Backlog / To Do / In Progress / Done。英文化の際はボードのスクリーンショット1枚にする。

| カード | 列(例) | マイルストーン | Target date | Risk |
|---|---|---|---|---|
| 提案書を書く・提出(CA1) | Done | 提案書 | Wk6 | 低 |
| ラボVMを構築(標的+Sysmon) | To Do | ラボ構築 | Wk7 | 中 |
| Wazuhを立ててログを取り込む | To Do | ラボ構築 | Wk8 | 高 |
| 公開テストを実行できるようにする | Backlog | ラボ構築 | Wk8 | 中 |
| 検知を3段階で採点する仕組み | Backlog | 測定と採点 | Wk9 | 中 |
| 戦術別の網羅を集計/ATT&CK Navigatorでヒートマップ | Backlog | 測定と採点 | Wk10 | 低 |
| 盲点リストを作る | Backlog | 仕上げ | Wk11 | 低 |
| 技術報告(CA2)/デモ(CA3) | Backlog | 報告・デモ | Wk12 | 中 |
