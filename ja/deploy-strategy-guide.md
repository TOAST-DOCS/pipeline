## Dev Tools > Pipeline > 配布戦略ガイド

配布戦略ガイドでは、Pipelineのステージを組み合わせて様々な配布戦略を実行する方法を説明します。

## Blue/Green配布

![deploy-strategy-guide-11.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-11.png)

Blue/Green配布は、二つの同一の環境を作成する配布戦略です。一つの環境(Blue)は現在のアプリケーションバージョンを実行し、もう一つの環境(Green)は新しいアプリケーションバージョンを実行します。
Blue/Green配布戦略を使用すると、アプリケーションの可用性を高め、配布失敗時のロールバックプロセスを簡素化し、配布リスクを減らすことができます。Green環境でテストが完了すると、アプリケーショントラフィックはGreen環境に移動され、Blue環境は廃棄されます。

### ReplicaSets使用

- Pipelineはラベルを使用してトラフィックを管理するため、実行中のリソースのラベルを修正する必要があります。
Deployment Objectを修正するとロールアウトが実行されるため、Service Objectを修正せずにBlue/Green配布を実行する方法は**ReplicaSets**を使うことです。
- PipelineはReplicaSetsを配布する際、`-vNNN`サフィックスを持つ新しいReplicaSetsを配布します。またReplicaSetsのannotationsのうち`strategy.spinnaker.io/max-version-history`, `traffic.spinnaker.io/load-balancers`を必ず含める必要があります。
    - `strategy.spinnaker.io/max-version-history`: Pipelineが維持するReplicaSetsの最大数を指定します。 2以上の値を指定することでBlue/Green配布が可能です。
    - `traffic.spinnaker.io/load-balancers`: Service Objectを指定します。 PipelineがServiceのSelectorに合わせてPodのラベルを修正してアプリケーションへのトラフィックを伝達できます。指定するService ObjectはPipelineeを通じて作成されたものでなければなりません。

### Blue/Greenパイプラインの構成方法

Blue/Green配布ができるパイプラインを構成する方法は次のとおりです。
[Pipelineテンプレートガイド](/Dev%20Tools/Pipeline/ja/template-guide/)を参考してパイプラインを構成できます。

#### 1. Service作成

**配布 - Deployステージ**を追加し、Pipelineを利用してServiceを作成します。一般的にアプリケーションを配布する時、Serviceを修正することはないので、アプリケーション配布パイプラインとは違うパイプラインを作成してServiceだけあらかじめ作成します。

![deploy-strategy-guide-01.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-01.png)

- 配布 - Deployステージ
    - Service manifestの例は次のとおりです。 metadata, specなどは環境に合わせて修正して使用できます。

``` yaml
apiVersion: v1
kind: Service
metadata:
  name: my-service
  namespace: blue-green
spec:
  selector:
    frontedBy: my-service
  ports:
  - protocol: TCP
    port: 80
```

![deploy-strategy-guide-02.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-02.png)

#### 2. アプリケーション配布パイプライン構成

**配布 - Deployステージ** > **配布 - Disableステージ** 順序でパイプラインを構成します。 **配布 - Deployステージ**では新しいバージョンのアプリケーションを配布し、**配布 - Disableステージ**では旧バージョンのアプリケーションを選択できるように構成します。
![deploy-strategy-guide-03.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-03.png)

- 配布 - Deployステージ
    - ReplicaSet manifestの例は次のとおりです。 annotationsの`strategy.spinnaker.io/max-version-history`は2以上の値を指定する必要があり、`traffic.spinnaker.io/load-balancers`は上記の過程で作成したService名を指定します。

     他のmetadata, specなどは環境に合わせて修正して使用できます。

```yaml
apiVersion: apps/v1
kind: ReplicaSet
metadata:
  annotations:
    strategy.spinnaker.io/max-version-history: "2"
    traffic.spinnaker.io/load-balancers: '["service my-service"]'
  labels:
    app: myapp
  name: myapp-frontend
  namespace: blue-green
spec:
  replicas: 4
  selector:
    matchLabels:
      app: myapp
  template:
    metadata:
      labels:
        app: myapp
    spec:
      containers:
      - image: nginx:stable-alpine3.17-slim
        name: frontend
```

![deploy-strategy-guide-04.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-04.png)

- 配布 - Disableステージ
    - 配布後、古いバージョンのアプリケーションを選択します。**配布 - Disableステージ**はリソースを削除するのではなく、そのリソースにトラフィックを送らないように設定します。
     リソースを削除したい場合は、**配布 - Deleteステージ**を活用してください。
    - 選択戦略
        - Newest:当該ステージが開始された時に最も最近に配布されたリソースを選択します。
        - Second Newest:当該ステージが開始された時、2番目に最近配布されたリソースを選択します。
        - Oldest:当該ステージが開始された時、最も古いリソースを選択します。
        - Largest:当該ステージが開始された時、クラスタでPod数が一番多いリソースを選択します。
        - Smallest:当該ステージが開始された時、クラスタでPod数が一番少ないリソースを選択します。

![deploy-strategy-guide-05.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-05.png)
