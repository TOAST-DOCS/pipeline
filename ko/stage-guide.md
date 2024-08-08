## Dev Tools > Pipeline > 스테이지 가이드

스테이지 가이드에서는 Pipeline의 스테이지에 대해 기본적인 내용을 설명합니다.

스테이지 추가는 파이프라인 스튜디오 화면으로 진입한 뒤 우측 상단의 **편집모드** 토글 버튼을 클릭하여 편집 모드를 활성화 합니다.
이후 왼쪽의 스테이지 추가 패널에서 **+트리 메뉴**를 클릭해 노출된 스테이지들을 드래그앤드랍 방식으로 추가할 수 있습니다.

스테이지의 상세 정보 조회 및 편집은 해당 스테이지를 클릭 후 우측 패널에서 확인이 가능합니다.

![stage-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-01.png)

스테이지는 아래의 그룹으로 구분됩니다.

- **소스**
- **빌드**
- **배포**
- **기능**

### 소스
빌드할 소스 코드를 가져오는 스테이지입니다.

#### 소스 - GitHub
**소스 저장소**는 **환경 설정**의 **소스 저장소 설정**에서 추가한 [소스 저장소](/Dev%20Tools/Pipeline/ko/environment-config/#_2)를 선택할 수 있습니다. **브랜치**에는 빌드할 대상의 소스 브랜치를 입력합니다. 

![stage-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-02.png)

#### 소스 - GitLab
**소스 저장소**는 **환경 설정**의 **소스 저장소 설정**에서 추가한 [소스 저장소](/Dev%20Tools/Pipeline/ko/environment-config/#_2)를 선택할 수 있습니다. **브랜치**에는 빌드할 대상의 소스 브랜치를 입력합니다.

![stage-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-03.png)

### 빌드
빌드를 하는 스테이지입니다.

#### 빌드 - Jenkins
사용자가 직접 구성한 Jenkins를 이용하여 빌드할 수 있습니다. **빌드 도구**는 **환경 설정**의 **빌드 도구 설정**에서 추가한 [빌드 도구](/Dev%20Tools/Pipeline/ko/environment-config/#_4)를 선택할 수 있습니다. **빌드 잡**을 선택할 수 있습니다.
**아티팩트**의 **시작 조건**과 **종료 조건**을 설정할 수 있습니다. **시작 조건**을 설정하여 스테이지 시작 여부를 결정할 수 있습니다. **종료 조건**을 설정하여 스테이지의 생성물을 아티팩트로 설정할 수 있습니다.

![stage-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-04.png)

#### 빌드 - Bake (Manifest)
사용자가 직접 구성한 Helm package file 또는 [차트 저장소](/Dev%20Tools/Pipeline/ko/environment-config/#_6)를 이용하여 빌드할 수 있습니다.

- 차트 이름은 Helm 엔진으로 구성한 결과물의 이름을 설정합니다.
- Namespace는 Helm 엔진으로 구성한 결과물의 Namespace를 설정합니다.
- 템플릿
    - 저장소 타입은 **환경 설정**의 [소스 저장소 설정](/Dev%20Tools/Pipeline/ko/environment-config/#_2) 또는 [차트 저장소 설정](/Dev%20Tools/Pipeline/ko/environment-config/#_6)에서 추가한 저장소를 선택할 수 있습니다.
    - 저장소 타입을 **GitHub 파일** 또는 **GitLab 파일**으로 지정한 경우
        - 경로는 Helm package file의 경로를 입력해야 합니다.
        - 브랜치 이름은 Github 또는 Gitlab의 브랜치를 입력합니다.
    - 저장소 타입을 **Helm 차트**로 지정한 경우
        - 차트 저장소 이름은 [차트 저장소 설정](/Dev%20Tools/Pipeline/ko/environment-config/#_6)에서 설정한 저장소 중 하나를 선택할 수 있습니다.
        - 차트 이름은 차트 저장소의 구성에서 사용할 수 있는 차트 이름을 선택할 수 있습니다.
        - 차트 버전은 차트 저장소의 구성에서 사용할 수 있는 차트 버전을 선택할 수 있습니다.
- 오버라이드
    - 저장소 정보
        - 템플릿과 동일한 방식으로 선택할 수 있습니다.
        - 템플릿을 기본으로 하여 오버라이드에서 지정한 내용으로 치환하여 빌드 결과물을 생성합니다.
    - 키(Key) / 값(Value)
        - key, value로 이루어진 값을 입력하고 특정 값을 치환하여 빌드 결과물을 생성합니다.
    - 기본 유형 치환
        - 해당 옵션을 체크하면 오버라이드 값을 주입할 때, --set-string 대신 --set을 사용합니다. --set을 사용하여 주입된 값은 Helm에 의해 기본 자료형으로 변환됩니다.
- 아티팩트
    - **아티팩트**의 **시작 조건**과 **종료 조건**을 설정할 수 있습니다. **시작 조건**을 설정하여 스테이지 시작 여부를 결정할 수 있습니다. **종료 조건**을 설정하여 스테이지의 생성물을 아티팩트로 설정할 수 있습니다.

![stage-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-05.png)

#### 빌드 - NHN Cloud 빌드 도구 v2
NHN Cloud에서 제공하는 빌드 도구를 사용할 수 있습니다.

- 빌드 환경 설정
    - 빌드 도구의 성능과 제한 시간을 설정할 수 있습니다.
- 소스 빌드 설정
    - **환경 설정**의 **이미지 저장소 설정**에서 추가한 [이미지 저장소](/Dev%20Tools/Pipeline/ko/environment-config/#_3)를 선택할 수 있습니다.
      - 빌드할 환경의 **이미지 이름** 및 **태그**를 입력하고, **빌드 명령어**를 설정합니다.

- 도커 이미지 빌드 설정
    - **Dockerfile 경로**는 Dockefile이 존재하는 경로를 입력합니다.
    - **Dockerfile 실행 경로**는 Dockerfile을 빌드할 경로를 입력합니다.
    - **이미지 저장소**를 선택하고, **이미지 이름**을 결정하면 해당 저장소로 결과물을 push합니다.
    - **태그**에는 이미지의 태그를 입력합니다. 태그 포맷을 포함하여 입력하면 입력한 태그 포맷 부분이 동적으로 치환됩니다.

- 아티팩트 설정
    - **시작 조건**을 설정하여 스테이지 시작 여부를 결정할 수 있습니다.
    - **종료 조건**을 설정하여 스테이지의 생성물을 아티팩트로 설정할 수 있습니다.


|이미지 태그 포맷 | 치환되는 형태 | 설명                                 |
| ----------- | ---------- |------------------------------------|
|{BUILD_DATE_TIME}| yyyy-MM-dd_HH_mm_ss| 연-월-일_시_분_초의 형태로 빌드 실행 시각으로 치환됩니다. |

![stage-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-06.png)

### 배포
Kubernetes 환경에 배포를 하는 스테이지입니다.

#### 배포 - Deploy
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
**스테이지 이름**, **배포 대상**, 배포에 사용할 **Manifest**를 입력합니다.
빌드 스테이지에서 태그 포맷을 사용한 경우 **Manifest**의 도커 이미지 태그 부분을 `_{BUILD_NUMBER}`로 입력하면 태그 포맷으로 빌드된 이미지 중 가장 최근 번호의 이미지로 배포할 수 있습니다.
**Manifest**를 작성하는 방법은 [Kubernetes 문서](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )를 참고하십시오.
- **Manifest 소스**를 아티팩트로 선택할 수 있습니다. 선택한 아티팩트는 Manifest 형태로 생성되어야 합니다.
    - 파이프라인에서 생성한 아티팩트를 선택할 수 있습니다.
    - 저장소에서 특정 파일을 아티팩트로 선택할 수 있습니다. 
- **아티팩트**의 **시작 조건** 및 **종료 조건**을 설정할 수 있습니다. **시작 조건**을 설정하여 스테이지 시작 여부를 결정할 수 있습니다. **종료 조건**을 설정하여 스테이지의 생성물을 아티팩트로 설정할 수 있습니다.

![stage-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-07.png)

#### 배포 - Patch
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**, 배포에 사용할 **Manifest**를 입력합니다. Patch로 기존 리소스의 정보를 수정할 수 있습니다.
- **Manifest**를 작성하는 방법은 [Kubernetes 문서](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources)를 참고하십시오.
- **선택 방법**을 **동적인 방법으로 선택**으로 설정할 경우 **클러스터**와 **선택 전략**을 입력합니다.
- 클러스터
    - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포하며, **동적인 방법으로 선택**을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
- 선택 전략
    - Newest: 해당 스테이지가 시작됐을 때 가장 최근에 배포된 리소스를 선택합니다.
    - Second Newest: 해당 스테이지가 시작됐을 때 두 번째로 최근에 배포된 리소스를 선택합니다.
    - Oldest: 해당 스테이지가 시작됐을 때 가장 오래된 리소스를 선택합니다.
    - Largest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 많은 리소스를 선택합니다.
    - Smallest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 적은 리소스를 선택합니다.

![stage-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-08.png)

#### 배포 - Scale
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**, **Replicas**를 입력합니다. Scale로 Replicas를 수정할 수 있습니다.
- **선택 방법**을 **동적인 방법으로 선택**으로 설정할 경우 **클러스터**와 **선택 전략**을 입력합니다.
- 클러스터
    - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포하며, **동적인 방법으로 선택**을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
- 선택 전략
    - Newest: 해당 스테이지가 시작됐을 때 가장 최근에 배포된 리소스를 선택합니다.
    - Second Newest: 해당 스테이지가 시작됐을 때 두 번째로 최근에 배포된 리소스를 선택합니다.
    - Oldest: 해당 스테이지가 시작됐을 때 가장 오래된 리소스를 선택합니다.
    - Largest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 많은 리소스를 선택합니다.
    - Smallest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 적은 리소스를 선택합니다.

![stage-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-09.png)

#### 배포 - Rollout undo
**환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
**Namespace**, **리소스 유형**, **리소스 이름**, **Revision Back**을 입력합니다. 지정한 Revision으로 롤백할 수 있습니다.

![stage-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-10.png)

#### 배포 - Delete
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**을 입력합니다. 해당 리소스를 삭제할 수 있습니다.
- **선택 방법**을 **동적인 방법으로 선택**으로 설정할 경우 **클러스터**와 **선택 전략**을 입력합니다.
- 클러스터
    - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포하며, **동적인 방법으로 선택**을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
- 선택 전략
    - Newest: 해당 스테이지가 시작됐을 때 가장 최근에 배포된 리소스를 선택합니다.
    - Second Newest: 해당 스테이지가 시작됐을 때 두 번째로 최근에 배포된 리소스를 선택합니다.
    - Oldest: 해당 스테이지가 시작됐을 때 가장 오래된 리소스를 선택합니다.
    - Largest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 많은 리소스를 선택합니다.
    - Smallest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 적은 리소스를 선택합니다.

![stage-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-11.png)

#### 배포 - NHN Container Service
NCS 워크로드의 템플릿을 교체할 수 있는 스테이지입니다.  
**NCS 앱키**를 입력하면 **NCS 역할**, 템플릿 리스트, 워크로드 리스트가 조회됩니다.  
변경할 템플릿을 리스트에서 선택할 수 있습니다.  
템플릿을 변경할 워크로드를 리스트에서 선택할 수 있습니다.

![stage-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-12.png)


#### 배포 - Enable
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**을 입력합니다. 해당 리소스를 활성화할 수 있습니다.
    - 활성화: 해당 리소스를 Pipeline에서 관리하며, 리소스에 트래픽을 보내도록 설정합니다.
- **선택 방법**을 **동적인 방법으로 선택**으로 설정할 경우 **클러스터**와 **선택 전략**을 입력합니다.
    - 클러스터
        - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포하며, **동적인 방법으로 선택**을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
    - 선택 전략
        - Newest: 해당 스테이지가 시작됐을 때 가장 최근에 배포된 리소스를 선택합니다.
        - Second Newest: 해당 스테이지가 시작됐을 때 두 번째로 최근에 배포된 리소스를 선택합니다.
        - Oldest: 해당 스테이지가 시작됐을 때 가장 오래된 리소스를 선택합니다.
        - Largest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 많은 리소스를 선택합니다.
        - Smallest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 적은 리소스를 선택합니다.

![stage-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-13.png)

#### 배포 - Disable
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**을 입력합니다. 해당 리소스를 비활성화할 수 있습니다.
    - 비활성화: 리소스를 삭제하지는 않지만, 더 이상 해당 리소스에 트래픽을 보내지 않도록 설정합니다.
- **선택 방법**을 **동적인 방법으로 선택**으로 설정할 경우 **클러스터**와 **선택 전략**을 입력합니다.
    - 클러스터
        - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포하며, **동적인 방법으로 선택**을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
    - 선택 전략
        - Newest: 해당 스테이지가 시작됐을 때 가장 최근에 배포된 리소스를 선택합니다.
        - Second Newest: 해당 스테이지가 시작됐을 때 두 번째로 최근에 배포된 리소스를 선택합니다.
        - Oldest: 해당 스테이지가 시작됐을 때 가장 오래된 리소스를 선택합니다.
        - Largest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 많은 리소스를 선택합니다.
        - Smallest: 해당 스테이지가 시작됐을 때 클러스터에서 Pod 수가 가장 적은 리소스를 선택합니다.

![stage-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-14.png)

### 기능
추가 기능을 제공하는 스테이지입니다.

#### 기능 - 승인 관리
**기능 - 승인 관리** 스테이지 이후의 스테이지들에 대한 **실행 관리(실행, 실행 중지)**를 승인권자가 관리할 수 있습니다.

스테이지에 요청 내용에 대해 작성할 수 있으며, 승인 관리 스테이지의 **실행 관리(실행, 실행 중지)** 기능은 해당 프로젝트의 **Pipeline APPROVAL ADMIN** 역할을 가진 사용자만 할 수 있습니다.

![stage-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-15.png)

**Pipeline APPROVAL ADMIN** 역할은 프로젝트의 멤버 관리, 역할 그룹 관리에서 부여할 수 있습니다.

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-18.png)

#### 기능 - Judgement(실행 관리)
필요에 따라 실행 관리 스테이지에 대한 **설명**, **실행 설정**값을 입력할 수 있습니다.

**실행 설정**의 유무와 상관없이 다음 스테이지에 대한 **실행 관리(실행, 실행 중지)**를 할 수 있습니다.
**실행 설정**을 추가하여 다음 스테이지의 실행을 선택할 경우 다음에 설명할 스테이지인 Precondition(실행 조건)에 설정값을 전달하여 분기 처리를 할 수 있습니다.

![stage-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-16.png)

#### 기능 - Precondition(스테이지 상태 조건)
이전 단계의 스테이지 이름과 실행 결과를 선택하여 조건을 설정할 수 있습니다.
지정한 모든 조건이 충족되어야 다음 스테이지가 실행됩니다.

![stage-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-17.png)

#### 기능 - Precondition(실행 조건)
이전 단계로 설정된 Judgement(실행 관리) 스테이지에서 전달받은 값의 **실행 조건**에 따라 뒤의 스테이지들의 실행을 결정합니다.
Judgement(실행 관리) 스테이지에서 전달받은 설정값과 **실행 조건**의 조건 값에 대해 **실행 조건 일치/실행 조건 불일치** 중 선택하여 이후 스테이지의 실행을 결정합니다.

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-18.png)

#### 기능 - Webhook
**URL**에 HTTP 메소드와 URL을 입력합니다. 필요에 따라 **요청 헤더**와 **요청 데이터**를 추가할 수 있습니다.
Webhook의 응답값이 **Fail Fast HTTP 상태 코드**에 입력한 값 중 하나라면 그 즉시 해당 스테이지를 종료합니다.

![stage-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-19.png)

#### 기능 - 타 파이프라인 실행
스테이지에서 다른 파이프라인 전체를 실행할 수 있습니다.
실행하고자 하는 **파이프라인 이름**을 선택합니다.

만약 **실행 조건**을 선택 해제할 경우 선택한 파이프라인의 실행 상태를 기다리지 않고, 다음 스테이지가 실행됩니다.

![stage-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-20.png)

#### 기능 - NHN Cloud Deploy 서비스 배포 실행
스테이지에서 NHN Cloud Deploy 서비스를 사용하여 배포를 실행할 수 있습니다.
- 배포를 실행하려는 아티팩트의 **Command Type**이 **SSH**인 경우 해당 **NHN Cloud Deploy 서비스 배포 실행** 기능을 지원하지 않으며, **Cloud Agent**인 경우에만 지원합니다. 관련된 내용은 [Deploy 사용 가이드](/Dev%20Tools/Deploy/ko/console-guide/#_8)를 참고하십시오.

**환경 설정** > **NHN Cloud 보안 설정**에서 추가한 보안 설정을 선택하고, **AppKey**에는 NHN Cloud Deploy 서비스를 사용할 Appkey를 입력합니다.

정보를 입력한 뒤 **검색**을 클릭하면 입력한 보안 설정과 Appkey에 맞는 NHN Cloud Deploy의 배포 관련 정보를 가져옵니다.

이후 NHN Cloud Deploy 서비스를 통해 배포할 **아티팩트**, **서버그룹**, **시나리오**를 선택할 수 있습니다.


**배포 제한 시간**에는 해당 스테이지의 실행 완료 대기 시간을 지정합니다. (최소 1분, 최대 600분)

**배포 상세 설정**에서는 배포할 대상에 대한 조건을 추가할 수 있습니다.

**서버 선택**에서 배포할 서버를 선택할 수 있습니다. **전체 서버**를 선택하면 전체 서버를 대상으로 배포를 진행하며, **서버 선택**을 클릭하면 배포할 서버를 선택할 수 있습니다.

**동시 서버 실행 수**에서 NHN Cloud Deploy 서비스가 동시에 몇 개의 서버를 실행할 지 선택할 수 있습니다. (기본값 1, 최대 서버 개수)

**배포 노트**에는 배포 실행 정보를 입력할 수 있습니다.

자세한 설명은 [Deploy 사용 가이드](/Dev%20Tools/Deploy/ko/reference/#_1)를 참고하십시오.

![stage-guide-21](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-stage-guide/stage-guide-21.png)

### 스테이지 공통 기능
#### 스테이지 실패 시

스테이지가 실패했을 때 파이프라인 실행에 관련된 설정을 선택할 수 있습니다.

- 전체 파이프라인 종료
    - 해당 스테이지가 실패하면 전체 파이프라인이 종료됩니다. 
- 해당 브랜치만 종료
    - 해당 스테이지가 속하는 브랜치만 종료되며 다른 브랜치의 파이프라인은 계속 진행됩니다. 
- 해당 브랜치가 종료되고, 다른 브랜치 종료 시 실패
    - 해당 스테이지가 속하는 브랜치만 종료되며 다른 브랜치의 파이프라인은 계속 진행됩니다. 하지만 해당 파이프라인의 결과는 실패로 남습니다.
- 실패를 무시하고 진행
    - 해당 스테이지가 실패해도 다음 스테이지가 진행됩니다.

![stage-guide-27](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-05-28/stage-guide-27.png)
