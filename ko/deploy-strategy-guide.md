## Dev Tools > Pipeline > 배포 전략 가이드

배포 전략 가이드에서는 Pipeline의 스테이지를 조합하여 여러 가지 배포 전략을 수행하는 방법을 설명합니다.

## Blue/Green 배포
Blue/Green 배포는 두 개의 동일한 환경을 생성하는 배포 전략입니다. 하나의 환경(Blue)은 현재의 애플리케이션 버전을 실행하고, 다른 하나의 환경(Green)은 새로운 애플리케이션 버전을 실행합니다.
Blue/Green 배포 전략을 사용하면 응용 프로그램 가용성을 높이고 배포 실패 시 롤백 프로세스를 단순화하여 배포 위험을 줄일 수 있습니다. Green 환경에서 테스트가 완료되면 애플리케이션 트래픽이 Green 환경으로 이동되고, Blue 환경은 폐기됩니다.

### ReplicaSets를 사용해야 합니다.
- Pipeline은 레이블을 사용해서 트래픽을 관리하며 실행 중인 리소스의 레이블을 수정해야 합니다.
Deployment Object를 수정하면 롤아웃이 실행되기 때문에 Service Object를 수정하지 않고 Blue/Green 배포를 수행할 수 있는 방법은 **ReplicaSets**을 사용하는 것입니다.
- Pipeline은 ReplicaSets을 배포할 때, `-vNNN` 접미사가 있는 새로운 ReplicaSets을 배포합니다. 또한 ReplicaSets의 annotations 중 `strategy.spinnaker.io/max-version-history`, `traffic.spinnaker.io/load-balancers` 을 반드시 포함해야 합니다.
  - `strategy.spinnaker.io/max-version-history` : Pipeline이 유지하는 ReplicaSets의 최대 개수를 지정합니다. 2 이상의 값을 줘야 Blue/Green 배포가 가능합니다.
  - `traffic.spinnaker.io/load-balancers` : Service Object를 지정합니다. Pipeline이 Service의 Selector에 맞게 Pod의 레이블을 수정하여 애플리케이션으로 트래픽 전달이 가능해집니다. 지정할 Service Object는 Pipeline을 통해 생성된 것이어야 합니다.

### Blue/Green 파이프라인 구성 방법
#### 1. Service 생성

**배포 - Deploy 스테이지**를 추가하여 Pipeline을 이용하여 Service를 생성합니다. 일반적으로 애플리케이션 배포 시 Service를 수정하지는 않으므로 애플리케이션 배포 파이프라인과 다른 파이프라인을 생성하여 Service만 미리 생성합니다.
![deploy-strategy-guide-01.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-01.png)

- 배포 - Deploy 스테이지
  - Service의 manifest의 예는 아래와 같습니다. metadata, spec 등은 환경에 맞게 수정하여 사용할 수 있습니다.
    ```yaml
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

#### 2. 애플리케이션 배포 파이프라인 구성

**배포 - Deploy 스테이지** -> **배포 - Disable 스테이지** 순서로 파이프라인을 구성합니다. **배포 - Deploy 스테이지**에서는 새로운 버전의 애플리케이션을 배포하고, **배포 - Disable 스테이지**에서는 구버전 애플리케이션을 선택할 수 있도록 구성합니다.
![deploy-strategy-guide-03.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-03.png)

- 배포 - Deploy 스테이지
  - ReplicaSet의 manifest의 예는 아래와 같습니다. annotations의 `strategy.spinnaker.io/max-version-history`는 2 이상의 값을 지정해 줘야 하고, `traffic.spinnaker.io/load-balancers`는 위 과정에서 생성한 Service 이름을 지정합니다.

    그 외의 metadata, spec 등은 환경에 맞게 수정하여 사용할 수 있습니다.
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
- 배포 - Disable 스테이지
  - 배포 후 구버전 애플리케이션을 선택합니다. **배포 - Disable 스테이지**는 리소스를 삭제하지는 않고, 더 이상 해당 리소스에 트래픽을 보내지 않도록 설정합니다.
    리소스를 삭제하고 싶으면 **배포 - Delete 스테이지**를 활용하십시오.
    ![deploy-strategy-guide-05.png](http://static.toastoven.net/prod_pipeline/2024-05-28/deploy-strategy-guide-05.png)


