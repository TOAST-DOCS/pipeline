## Dev Tools > Pipeline > コンソール使用ガイド > 配布対象モニター

### 配布対象モニタリング

Pipelineで配布して作成された結果物を**配布対象モニタリング** メニューで確認できます。

## 配布対象

**配布対象モニタリング**で**配布対象**はPipelineでKubernetesに配布したワークロードを確認できるページです。
![deploy-target-monitoring-guide-01.png](..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-01.png)
配布したワークロードのすべてのリストとワークロード名および該当ワークロードに属するPodの数と状態が表示されます。
検索ワード入力後、検索ボタンをクリックすると入力した文字列で配布対象を検索します。
配布対象テーブルで**配布対象名**をクリックすると、選択した配布対象に属するワークロードを確認できるページに移動します。

![deploy-target-monitoring-guide-02.png](..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-02.png)
選択した配布対象クラスタの名前空間のうち、Pipelineで配布したワークロードの名前空間が表示されます。
検索ワードを入力して検索ボタンをクリックすると、入力した文字列で名前空間を検索します。
名前空間を選択すると、選択した名前空間に属するワークロードリストが表示されます。

![deploy-target-monitoring-guide-03.png](..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-03.png)
ワークロードに属するパッドの数と現在動作中のパッドの数が%で表示されます。ワークロードを選択すると、選択したワークロードのPodのリストが表示され、動作状態を左側の点の色で確認することができます。
選択したワークロード及びPodの基本情報が右側に表示されます。


左の点の色別のPodの状態

| 色 | 状態 |
| --- |------|
| 緑 | 実行中 |
| 赤 | 停止 |



![deploy-target-monitoring-guide-04.png](..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-04.png)
Podを選択した場合、コンソールログおよび接続されたサービスの情報も確認できます。
Podの中でサービスと連結されたPodの場合、右側に見えるロードバランサーアイコンが作成されます。ロードバランサーアイコンを選択すると**ネットワーク**タブに移動します。

**配布対象モニタリング**でサービスと連結されたワークロードを確認するためには、Manifestでセレクタを指定するのではなく、'traffic.spinnaker.io/load-balancers'アノテーションを追加する必要があります。

![deploy-target-monitoring-guide-08.png](..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-08.png)

## ネットワーク

**配布対象モニタリング**の**ネットワーク**はPipelineでKubernetesに配布したサービスを確認できるページです。

![deploy-target-monitoring-guide-05.png]( ..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-05.png)
配布したサービスの全てのリストとサービスに接続されたパッドの数や状態が公開されます。
検索語入力後、検索ボタンをクリックすると、入力した文字列で配布対象を検索します。
配布対象テーブルで**配布対象名**をクリックすると、ネームスペース選択ページに移動します。

![deploy-target-monitoring-guide-06.png](..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-06.png)

選択した配布対象クラスターの名前空間の中でPipelineで配布したサービスの名前空間が表示されます。
検索語入力後、検索ボタンをクリックすると、入力した文字列でネームスペースを検索します。
名前空間を選択すると、選択した名前空間に属するサービスのリストが公開されます。

![deploy-target-monitoring-guide-07.png](..%2Fimages%2F2023-06-27%2Fdeploy-target-monitoring-guide-07.png)

サービスを選択すると、サービスに属するワークロードのリストが表示されます。ワークロードを選択すると、選択したワークロードの情報が**配布対象**タブのように右側に表示されます。
