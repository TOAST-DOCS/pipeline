## Dev Tools > Pipeline > 콘솔 사용 가이드 > 카나리 배포 관리

Pipeline에서 카나리 배포를 활용하기 위한 설정을 **카나리 배포 관리** 탭에서 확인할 수 있습니다.

## 지표 저장소 설정
지표 저장소를 추가하면 **기능 - Canary Analysis** 스테이지를 사용해서 저장된 지표를 이용하여 카나리 배포를 수행할 수 있습니다.

![canary-management-guide-01.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-01.png)

**카나리 배포 관리**에서 **지표 저장소 설정**을 클릭하면 지표 저장소를 관리하는 화면으로 이동합니다. **지표 저장소 추가**를 클릭해서 신규 지표 저장소를 추가할 수 있습니다.

![canary-management-guide-02.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-02.png)

지표 저장소 정보를 입력한 후 **지표 저장소 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다.

![canary-management-guide-03.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-03.png)

## 카나리 설정
카나리 설정을 추가하면 **기능 - Canary Analysis** 스테이지를 사용해서 저장된 지표를 이용하여 카나리 배포를 수행할 수 있습니다.
해당 설정에서 어떤 [Prometheus Query]((https://prometheus.io/docs/prometheus/latest/querying/basics/))를 사용할지 설정할 수 있습니다.
또 Query에 대해 그룹을 나눌 수 있고 그룹별 가중치를 주어 Canary 배포를 수행할 수 있습니다.

![canary-management-guide-04.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-04.png)

**카나리 배포 관리**에서 **카나리 설정**을 클릭하면 카나리 설정을 관리하는 화면으로 이동합니다. **카나리 설정 추가**를 클릭해서 신규 카나리 설정을 추가할 수 있습니다.

![canary-management-guide-05.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-05.png)

**그룹 추가**를 클릭해서 메트릭 그룹을 추가할 수 있습니다. 메트릭 그룹을 추가하면 그룹마다 가중치를 부여하여 여러 Query를 활용한 Canary 배포가 가능합니다.

**메트릭 추가**를 클릭해서 메트릭을 추가할 수 있습니다.

![canary-management-guide-06.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-06.png)

- **메트릭 이름**을 지정합니다.
- **실패 조건**은 신규 애플리케이션의 지표가 조건에 해당할 때, 애플리케이션이 비정상적인 상황으로 간주하는 설정입니다.
- **중요도**는 메트릭이 실패했을 때, 카나리 배포를 실패 처리하도록 하는 설정입니다.
- **NaN 처리 전략**은 메트릭에 대한 값이 없을 때, 무시하거나 0으로 대체하도록 하는 설정입니다.
- <strong>템플릿(PromQL)</strong>은 기존 애플리케이션과 신규 애플리케이션에 대한 지표를 확인할 수 있는 Prometheus Query를 지정합니다.
- <strong>${location}</strong>과 <strong>${scope}</strong>는 템플릿 변수로 **기능 - Canary Analysis** 스테이지에서 설정한 값으로 대체됩니다.

![canary-management-guide-07.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-07.png)

카나리 점수는 그룹별로 부여한 가중치를 활용하여 계산됩니다. 가중치의 전체 합은 **100**이 되어야 합니다.

![canary-management-guide-08.png](http://static.toastoven.net/prod_pipeline/2024-05-28/canary-management-guide-08.png)
