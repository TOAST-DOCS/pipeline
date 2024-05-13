## Dev Tools > Pipeline > 스테이지 가이드

스테이지 가이드에서는 Pipeline의 스테이지에 대해 기본적인 내용을 설명합니다.
**파이프라인 관리** > **+파이프라인 생성**을 클릭해 파이프라인을 생성합니다. 생성한 파이프라인을 선택한 뒤 하단의 **스테이지** 탭에서 **+스테이지 추가**를 클릭해 스테이지를 추가할 수 있습니다.

![stage-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-01.png)

스테이지는 아래의 그룹으로 구분됩니다.

- **소스**
- **빌드**
- **배포**
- **기능**

### 소스
빌드할 소스 코드를 가져오는 스테이지입니다.

#### 소스 - GitHub
**소스 저장소**는 **환경 설정**의 **소스 저장소 설정**에서 추가한 [소스 저장소](/Dev%20Tools/Pipeline/ko/environment-config/#_2)를 선택할 수 있습니다. **브랜치**에는 빌드할 대상의 소스 브랜치를 입력합니다.

![stage-guide-02](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-02.png)

#### 소스 - GitLab
**소스 저장소**는 **환경 설정**의 **소스 저장소 설정**에서 추가한 [소스 저장소](/Dev%20Tools/Pipeline/ko/environment-config/#_2)를 선택할 수 있습니다. **브랜치**에는 빌드할 대상의 소스 브랜치를 입력합니다.

![stage-guide-03](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-03.png)

### 빌드
빌드를 하는 스테이지입니다.

#### 빌드 - Jenkins
사용자가 직접 구성한 Jenkins를 이용하여 빌드할 수 있습니다. **빌드 도구**는 **환경 설정**의 **빌드 도구 설정**에서 추가한 [빌드 도구](/Dev%20Tools/Pipeline/ko/environment-config/#_4)를 선택할 수 있습니다. **빌드 잡**을 선택하고 **빌드 잡 파라미터**를 입력할 수 있습니다.
**아티팩트**의 **시작 조건**과 **종료 조건**을 설정할 수 있습니다. **시작 조건**을 설정하여 스테이지 시작 여부를 결정할 수 있습니다. **종료 조건**을 설정하여 스테이지의 생성물을 아티팩트로 설정할 수 있습니다.

![stage-guide-04](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-01.png)
![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-04.png)

#### 빌드 - NHN Cloud 빌드 도구
NHN Cloud에서 제공하는 빌드 도구를 사용할 수 있습니다.

- 빌드 환경 설정
    - **환경 설정**의 **이미지 저장소 설정**에서 추가한 [이미지 저장소](/Dev%20Tools/Pipeline/ko/environment-config/#_3)를 선택할 수 있습니다.
    - 빌드할 환경의 **이미지 이름**을 선택하고, **빌드 도구 성능**과 **빌드 시간 제한(분)**, **빌드 명령어**를 설정합니다.
  
- 빌드 결과 설정
    - 빌드 결과물의 **Dockerfile 경로**를 설정하고, **Dockerfile 실행 경로**를 설정합니다.
    - **이미지 저장소**를 선택하고, **이미지 이름**을 결정하면 해당 저장소로 결과물을 push합니다.
    - **태그 포맷 사용**을 선택하면 태그 포맷으로 태그가 고정되며, `_{BUILD_NUMBER}` 형식의 동적으로 생성되는 태그로 이미지가 생성됩니다.

- 아티팩트 설정
    - **시작 조건**을 설정하여 스테이지 시작 여부를 결정할 수 있습니다.
    - **종료 조건**을 설정하여 스테이지의 생성물을 아티팩트로 설정할 수 있습니다.

![stage-guide-05](http://static.toastoven.net/prod_pipeline/2023-02-28/stage-guide-02.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-02.png)

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

![stage-guide-21.png](http://static.toastoven.net/prod_pipeline/2024-02-27/stage-guide-21.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-02.png)

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

![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-12.png)
![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-13.png)

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


![stage-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-06.png)
![stage-guide-15](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-15.png)
![stage-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/stage-guide-16.png)
![stage-guide-14](http://static.toastoven.net/prod_pipeline/2023-02-28/console-guide-05.png)

#### 배포 - Patch
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**, 배포에 사용할 **Manifest**를 입력합니다. Patch로 기존 리소스의 정보를 수정할 수 있습니다.
- **Manifest**를 작성하는 방법은 [Kubernetes 문서](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources)를 참고하십시오.
- **동적인 방법으로 선택** 시 **클러스터**와 **선택 전략**을 입력합니다.
- 클러스터
    - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포를 하게 되는데, 동적인 방법을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
- 선택 전략
    - Newest : 해당 스테이지가 시작됐을 때, 가장 최근에 배포된 리소스를 선택합니다.
    - Second Newest : 해당 스테이지가 시작됐을 때, 두 번째로 최근에 배포된 리소스를 선택합니다.
    - Oldest : 해당 스테이지가 시작됐을 때, 가장 오래된 리소스를 선택합니다.
    - Largest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 많은 리소스를 선택합니다.
    - Smallest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 적은 리소스를 선택합니다.

![stage-guide-07](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-07.png)
![stage-guide-07-2](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-07-2.png)

#### 배포 - Scale
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**, **Replicas**를 입력합니다. Scale로 Replicas를 수정할 수 있습니다.
- **동적인 방법으로 선택** 시 **클러스터**와 **선택 전략**을 입력합니다.
- 클러스터
    - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포를 하게 되는데, 동적인 방법을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
- 선택 전략
    - Newest : 해당 스테이지가 시작됐을 때, 가장 최근에 배포된 리소스를 선택합니다.
    - Second Newest : 해당 스테이지가 시작됐을 때, 두 번째로 최근에 배포된 리소스를 선택합니다.
    - Oldest : 해당 스테이지가 시작됐을 때, 가장 오래된 리소스를 선택합니다.
    - Largest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 많은 리소스를 선택합니다.
    - Smallest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 적은 리소스를 선택합니다.

![stage-guide-08](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-08.png)
![stage-guide-08-2](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-08-2.png)

#### 배포 - Rollout undo
**환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
**Namespace**, **리소스 유형**, **리소스 이름**, **Revision Back**을 입력합니다. 지정한 Revision으로 롤백할 수 있습니다.

![stage-guide-09](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-09.png)

#### 배포 - Delete
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**을 입력합니다. 해당 리소스를 삭제할 수 있습니다.
- **동적인 방법으로 선택** 시 **클러스터**와 **선택 전략**을 입력합니다.
- 클러스터
    - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포를 하게 되는데, 동적인 방법을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
- 선택 전략
    - Newest : 해당 스테이지가 시작됐을 때, 가장 최근에 배포된 리소스를 선택합니다.
    - Second Newest : 해당 스테이지가 시작됐을 때, 두 번째로 최근에 배포된 리소스를 선택합니다.
    - Oldest : 해당 스테이지가 시작됐을 때, 가장 오래된 리소스를 선택합니다.
    - Largest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 많은 리소스를 선택합니다.
    - Smallest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 적은 리소스를 선택합니다.

![stage-guide-10](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-10.png)
![stage-guide-10-2](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-10-2.png)

#### 배포 - Disable
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**을 입력합니다. 해당 리소스를 비활성화 시킬 수 있습니다.
    - 비활성화 : 리소스를 삭제하지는 않지만, 더 이상 해당 리소스에 트래픽을 보내지 않도록 설정합니다.
- **동적인 방법으로 선택** 시 **클러스터**와 **선택 전략**을 입력합니다.
    - 클러스터
        - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포를 하게 되는데, 동적인 방법을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
    - 선택 전략
        - Newest : 해당 스테이지가 시작됐을 때, 가장 최근에 배포된 리소스를 선택합니다.
        - Second Newest : 해당 스테이지가 시작됐을 때, 두 번째로 최근에 배포된 리소스를 선택합니다.
        - Oldest : 해당 스테이지가 시작됐을 때, 가장 오래된 리소스를 선택합니다.
        - Largest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 많은 리소스를 선택합니다.
        - Smallest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 적은 리소스를 선택합니다.

![stage-guide-23.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-23.png)
![stage-guide-24.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-24.png)

#### 배포 - Enable
- **환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](/Dev%20Tools/Pipeline/ko/environment-config/#_5)을 선택할 수 있습니다.
- **Namespace**, **리소스 유형**, **선택 방법**, **리소스 이름**을 입력합니다. 해당 리소스를 활성화 시킬 수 있습니다.
    - 활성화 : 해당 리소스를 Pipeline에서 관리하며, 리소스에 트래픽을 보내도록 설정합니다.
- **동적인 방법으로 선택** 시 **클러스터**와 **선택 전략**을 입력합니다.
    - 클러스터
        - replicaSet의 경우 Pipeline 내부적으로 버전을 지정하여 배포를 하게 되는데, 동적인 방법을 선택하면 특정 버전을 선택하는 것이 아니라 선택 전략에 따라 대상을 선택합니다.
    - 선택 전략
        - Newest : 해당 스테이지가 시작됐을 때, 가장 최근에 배포된 리소스를 선택합니다.
        - Second Newest : 해당 스테이지가 시작됐을 때, 두 번째로 최근에 배포된 리소스를 선택합니다.
        - Oldest : 해당 스테이지가 시작됐을 때, 가장 오래된 리소스를 선택합니다.
        - Largest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 많은 리소스를 선택합니다.
        - Smallest : 해당 스테이지가 시작됐을 때, 클러스터에서 Pod수가 가장 적은 리소스를 선택합니다.

![stage-guide-25.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-25.png)
![stage-guide-26.png](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-26.png)

#### 배포 - NHN Container Service
NCS 워크로드의 템플릿을 교체할 수 있는 스테이지입니다.  
**NCS 앱키**를 입력하면 **NCS 역할**, 템플릿 리스트, 워크로드 리스트가 조회됩니다.  
변경할 템플릿을 리스트에서 선택할 수 있습니다.  
템플릿을 변경할 워크로드를 리스트에서 선택할 수 있습니다.

![stage-guide-22.png](http://static.toastoven.net/prod_pipeline/2024-03-26/stage-guide-22.png)


### 기능
추가 기능을 제공하는 스테이지입니다.

#### 기능 - Webhook
**URL**에 HTTP 메소드와 URL을 입력합니다. 필요에 따라 **요청 헤더**와 **요청 데이터**를 추가할 수 있습니다.
Webhook의 응답값이 **Fail Fast HTTP 상태 코드**에 입력한 값 중 하나라면 그 즉시 해당 스테이지를 종료합니다.

![stage-guide-11](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-11.png)

#### 기능 - Judgement(실행 관리)
필요에 따라 실행 관리 스테이지에 대한 **설명**, **실행 설정**값을 입력할 수 있습니다.

![stage-guide-12](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-12.png)

**실행 설정**의 유무와 상관없이 다음 스테이지에 대한 **실행 관리(실행, 실행 중지)**를 할 수 있습니다.
**실행 설정**을 추가하여 다음 스테이지의 실행을 선택할 경우 다음에 설명할 스테이지인 Precondition(실행 조건)에 설정값을 전달하여 분기 처리를 할 수 있습니다.

![stage-guide-13](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-13.png)

#### 기능 - Precondition(실행 조건)
이전 단계로 설정된 Judgement(실행 관리) 스테이지에서 전달받은 값의 **실행 조건**에 따라 뒤의 스테이지들의 실행을 결정합니다.
Judgement(실행 관리) 스테이지에서 전달받은 설정값과 **실행 조건**의 조건 값에 대해 **실행 조건 일치/실행 조건 불일치** 중 선택하여 이후 스테이지의 실행을 결정합니다.

![stage-guide-14](http://static.toastoven.net/prod_pipeline/2023-06-15/stage-guide-14.png)

#### 기능 - Precondition(스테이지 상태 조건)
이전 단계의 스테이지 이름과 실행 결과를 선택하여 조건을 설정할 수 있습니다.
지정한 모든 조건이 충족되어야 다음 스테이지가 실행됩니다.

![stage-guide-28](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-28.png)

#### 기능 - 타 파이프라인 실행
스테이지에서 다른 파이프라인 전체를 실행할 수 있습니다.
실행하고자 하는 **파이프라인 이름**을 선택합니다.
![stage-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/stage-guide-15.png)

**실행 조건**을 선택 해제하면 선택한 파이프라인의 실행 상태를 기다리지 않고, 다음 스테이지가 실행됩니다.

![stage-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-08-29/stage-guide-16.png)

#### 기능 - 승인 관리
**기능 - 승인 관리** 스테이지 이후의 스테이지들에 대한 **실행 관리(실행, 실행 중지)**를 승인권자가 관리할 수 있습니다.

![stage-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-17.png)

스테이지에 요청 내용에 대해 작성할 수 있으며, 승인 관리 스테이지의 **실행 관리(실행, 실행 중지)** 기능은 해당 프로젝트의 **Pipeline APPROVAL ADMIN** 역할을 가진 사용자만 할 수 있습니다.

**Pipeline APPROVAL ADMIN** 역할은 프로젝트의 멤버 관리, 역할 그룹 관리에서 부여할 수 있습니다.

![stage-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-10-31/stage-guide-18.png)

#### 기능 - NHN Cloud Deploy 서비스 배포 실행
스테이지에서 NHN Cloud Deploy 서비스를 사용하여 배포를 실행할 수 있습니다.
- 배포를 실행하려는 아티팩트의 **Command Type**이 **SSH**인 경우 해당 **NHN Cloud Deploy 서비스 배포 실행** 기능을 지원하지 않으며, **Cloud Agent**인 경우에만 지원합니다. 관련된 내용은 [Deploy 사용 가이드](/Dev%20Tools/Deploy/ko/console-guide/#_8)를 참고하십시오.

![stage-guide-19](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/stage-guide-19.png)

**환경 설정** > **NHN Cloud 보안 설정**에서 추가한 보안 설정을 선택하고, **AppKey**에는 NHN Cloud Deploy 서비스를 사용할 Appkey를 입력합니다.

정보를 입력한 뒤 **검색**을 클릭하면 입력한 보안 설정과 Appkey에 맞는 NHN Cloud Deploy의 배포 관련 정보를 가져옵니다.

이후 NHN Cloud Deploy 서비스를 통해 배포할 **아티팩트**, **서버그룹**, **시나리오**를 선택할 수 있습니다.


**배포 제한 시간**에는 해당 스테이지의 실행 완료 대기 시간을 지정합니다. (최소 1분, 최대 600분)

![stage-guide-20](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-12-19/stage-guide-20.png)

**배포 상세 설정**에서는 배포할 대상에 대한 조건을 추가할 수 있습니다.

**서버 선택**에서 배포할 서버를 선택할 수 있습니다. **전체 서버**를 선택하면 전체 서버를 대상으로 배포를 진행하며, **서버 선택**을 클릭하면 배포할 서버를 선택할 수 있습니다.

**동시 서버 실행 수**에서 NHN Cloud Deploy 서비스가 동시에 몇 개의 서버를 실행할 지 선택할 수 있습니다. (기본값 1, 최대 서버 개수)

**배포 노트**에는 배포 실행 정보를 입력할 수 있습니다.

자세한 설명은 [Deploy 사용 가이드](/Dev%20Tools/Deploy/ko/reference/#_1)를 참고하십시오.

#### 기능 - Canary Analysis
Canary 배포를 수행할 때 사용하는 스테이지입니다. 해당 스테이지는 입력한 정보에 따라 Prometheus로 Query를 수행하고 Canary 점수를 계산합니다.
해당 점수에 따라 이 스테이지의 결과를 결정합니다. 이 점수는 100점 만점이며 점수가 낮을수록 이상 징후가 있다는 것을 의미합니다.

점수가 낮은 경우 스테이지가 실패로 끝나게 되고, 점수가 높으면 **분석 총 시간**만큼 진행한 후 성공으로 끝나게 됩니다.

해당 스테이지의 결과에 따라 후속 처리를 할 수 있도록 추가 스테이지를 구성해야할 수 있습니다.

자세한 설명은 [배포 전략 가이드](/Dev%20Tools/Pipeline/ko/deploy-strategy/)를 참고하십시오.

![stage-guide-29](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-29.png)

**지표 저장소 설정**에는 **카나리 배포 관리** > **비표 저장소 설정**에서 생성한 설정을 선택합니다.

**카니리 설정**에는 **카나리 배포 관리** > **카나리 설정**에서 생성한 설정을 선택합니다.

**분석 총 시간**은 **기능 - Canary Analysis** 스테이지가 동작하는 총 시간을 설정합니다.

**Delay**는 첫 번째 카나리 분석이 시작되기까지의 지연시간입니다.

**Interval**은 카나리 분석을 수행하는 간격입니다.

**Step**은 메트릭 시계열의 간격을 나타냅니다.

**Baseline Offset**은 카나리 분석 시작점으로부터 기준 데이터 수집까지의 오프셋입니다.

![stage-guide-30](http://static.toastoven.net/prod_pipeline/2024-05-28/stage-guide-30.png)

**Baseline**은 메트릭 카나리 설정에서 지정한 템플릿의 ${scope}에 적용되는 값이며, 분석을 위한 Baseline으로 사용됩니다.

**Baseline Location**은 메트릭 카나리 설정에서 지정한 템플릿의 ${location}에 적용되는 값이며, 분석을 위한 Baseline으로 사용됩니다.

**Canary**는 메트릭 카나리 설정에서 지정한 템플릿의 ${scope}에 적용되는 값이며, 신규 버전의 분석으로 사용됩니다.

**Canary Location**은 메트릭 카나리 설정에서 지정한 템플릿의 ${location}에 적용되는 값이며, 신규 버전의 분석으로 사용됩니다.

**Marginal**은 해당 값보다 카나리 점수가 낮으면 즉시 종료되며, 이 값보다 크면 종료되지 않습니다.

**Pass**는 Pipeline에 있는 모든 **기능 - Canary Analysis**스테이지가 실행된 후, 이 값보다 카나리 점수가 높으면 즉시 Pass로 종료됩니다.

### 스테이지 공통 기능
#### 스테이지 실패 시

스테이지가 실패했을 때 파이프라인 실행에 관련된 설정을 선택할 수 있습니다.

![stage-guide-27](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-05-28/stage-guide-27.png)

- 전체 파이프라인 종료
    - 해당 스테이지가 실패하면 전체 파이프라인이 종료됩니다. 
- 해당 브랜치만 종료
    - 해당 스테이지가 속하는 브랜치만 종료되며 다른 브랜치의 파이프라인은 계속 진행됩니다. 
- 해당 브랜치가 종료되고, 다른 브랜치 종료 시 실패
    - 해당 스테이지가 속하는 브랜치만 종료되며 다른 브랜치의 파이프라인은 계속 진행됩니다. 하지만 해당 파이프라인의 결과는 실패로 남습니다.
- 실패를 무시하고 진행
    - 해당 스테이지가 실패해도 다음 스테이지가 진행됩니다.