## Dev Tools > Pipeline > 콘솔 사용 가이드 > 배포 대상 관리

### 배포 대상 관리

Pipeline으로 배포하여 생성된 결과물을 **배포 대상 관리** 메뉴에서 확인할 수 있습니다.

## 배포 대상

**배포 대상 관리 > 배포 대상**은 Pipeline으로 Kubernetes에 배포한 워크로드를 확인할 수 있는 페이지입니다.
![deploy-target-monitoring-guide-01.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-01.png)
배포한 워크로드의 모든 목록과 워크로드 이름 및 해당 워크로드에 속한 파드의 수와 상태가 노출됩니다.
검색어 입력 후 검색 버튼 클릭 시 입력한 문자열로 배포 대상을 검색합니다.
배포 대상 테이블에서 **배포 대상 이름**을 클릭하면 선택한 배포 대상에 속한 워크로드들을 확인할 수 있는 페이지로 이동합니다.

![deploy-target-monitoring-guide-02.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-02.png)
선택한 배포 대상 클러스터의 네임스페이스 중 Pipeline으로 배포한 워크로드들의 네임스페이스가 노출됩니다.
검색어 입력 후 검색 버튼 클릭 시 입력한 문자열로 네임스페이스를 검색합니다.
네임스페이스 선택 시 선택한 네임스페이스에 속한 워크로드 목록이 노출됩니다.

![deploy-target-monitoring-guide-09.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-09.png)
워크로드에 속한 파드의 개수와 현재 동작 중인 파드가 %로 표시됩니다. 워크로드 선택 시 선택한 워크로드의 파드의 목록이 나타나며 동작 상태를 왼쪽의 점의 색으로 확인할 수 있습니다.
선택한 워크로드 및 파드의 기본 정보가 오른쪽에 노출됩니다.


왼쪽 점의 색에 따른 파드의 상태

| 색깔 | 상태   |
| --- |------|
| 초록 | 실행 중 |
| 빨강 | 정지   |



![deploy-target-monitoring-guide-10.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-10.png)
파드를 선택한 경우 콘솔 로그 및 연결된 서비스의 정보도 확인할 수 있습니다.
파드 중 서비스와 연결된 파드의 경우 우측에 보이는 로드 밸런서 아이콘이 생성됩니다. 로드 밸런서 아이콘 선택 시 **네트워크**탭으로 이동합니다.

**배포 대상 관리**에서 서비스와 연결된 워크로드를 확인하기 위해서는 Manifest에서 셀렉터를 지정하는 것이 아니라 'traffic.spinnaker.io/load-balancers' 어노테이션을 추가하여야 확인할 수 있습니다.

![deploy-target-monitoring-guide-08.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-08.png)

**워크로드 관리**를 클릭하면 선택한 워크로드에 따라 가능한 관리 작업의 리스트가 노출됩니다. 모든 작업은 워크로드가 실행 중인 클러스터에 실제로 적용됩니다. 
![deploy-target-monitoring-guide-11.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-11.png)

실행한 작업은 **관리 이력** 탭에서 확인할 수 있습니다.
**관리 이력**은 네임스페이스와 워크로드의 이름을 기준으로 저장되며 최근 10건만 노출됩니다. 삭제 작업의 경우 수행 후 워크로드도 삭제되므로 삭제한 이력은 확인할 수 없습니다.

![deploy-target-monitoring-guide-12.png](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/deploy-target-management-guide-12.png)

관리 작업의 종류

| 관리 작업    | 설명                      | 가능한 워크로드 |
|----------|-------------------------| --- |
| 수정       | 워크로드의 manifest를 수정 및 적용 | 모든 워크로드 |
| 삭제       | 워크로드를 클러스터에서 제거         | 모든 워크로드 |
| 서비스 활성   | 워크로드와 서비스를 연결           | 레플리카셋|
| 서비스 비활성  | 워크로드와 서비스의 연결 해제        | 레플리카셋|
| 스케일 인/아웃 | 워크로드의 파드 수 조절           | 디플로이먼트, 레플리카셋, 스테이트풀셋|
| 롤백       | 워크로드의 이전 버전으로 롤백        | 디플로이먼트|
| 파드 재시작   | 워크로드의 파드들을 재시작          | 디플로이먼트 |
| 배포 일시 중지 | 롤백, 파드 재시작 작업을 일시 중지    | 디플로이먼트 |
| 배포 재시작   | 일시 중지된 배포를 재시작          | 디플로이먼트 |



## 네트워크

**배포 대상 관리 > 네트워크**는 Pipeline으로 Kubernetes에 배포한 서비스를 확인할 수 있는 페이지입니다.

![deploy-target-monitoring-guide-05.png]( http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-05.png)
배포한 서비스들의 모든 목록과 서비스에 연결된 파드의 수 및 상태가 노출됩니다.
검색어 입력 후 검색 버튼 클릭 시 입력한 문자열로 배포 대상을 검색합니다.
배포 대상 테이블에서 **배포 대상 이름**을 클릭하면 네임스페이스 선택 페이지로 이동합니다.

![deploy-target-monitoring-guide-06.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-06.png)

선택한 배포 대상 클러스터의 네임스페이스 중 Pipeline으로 배포한 서비스들의 네임스페이스가 노출됩니다.
검색어 입력 후 검색 버튼 클릭 시 입력한 문자열로 네임스페이스를 검색합니다.
네임스페이스 선택 시 선택한 네임스페이스에 속한 서비스들의 목록이 노출됩니다.

![deploy-target-monitoring-guide-07.png](http://static.toastoven.net/prod_pipeline/2023-06-27/deploy-target-monitoring-guide-07.png)

서비스를 선택하면 서비스에 속한 워크로드 목록이 노출됩니다. 워크로드 선택 시 선택한 워크로드의 정보가 **배포 대상** 탭에서와 같이 오른쪽에 노출됩니다. 
