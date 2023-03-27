## Dev Tools > Pipeline > コンソール使用ガイド > Dev Env Configuration

### 開発環境設定

開発環境設定を使用すると、Kubernetesの使用方法を知らないユーザーもKubernetesにコンテナイメージを配布できます。

![dev-env-config-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-01.png)

**開発環境設定**で**開発環境の作成**をクリックします。

![dev-env-config-guide-02](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-02.png)

開発環境名と開発環境の説明を入力し、基本イメージから配布するコンテナイメージを選択します。コンテナイメージのアクセスに必要な情報はイメージストアに設定します。配布対象はコンテナイメージを配布するKubernetesを選択します。サービスポートはコンテナが提供するサービスのポートを入力します。サービスポートを入力すると、コンテナサービスにアクセスできるサービスIPを自動的に割り当てます(KubernetesがLoadBalancerタイプのサービスを提供する場合)。最後に開発環境の制約事項を入力して**作成**をクリックすると開発環境を作成します。

![dev-env-config-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-03.png)

開発環境の作成中は**開発環境の状態**は**作成中**と表示されます。

![dev-env-config-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-04.png)

開発環境の作成が完了すると、**開発環境の状態**が**実行中**に変更されます。サービスIPとサービスポートを使用してコンテナサービスにアクセスできます。
