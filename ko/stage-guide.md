## Dev Tools > Pipeline > 스테이지 가이드

스테이지 가이드에서는 Pipeline의 스테이지에 대해 기본적인 내용을 설명합니다.
**파이프라인 관리** > **+파이프라인 생성**을 클릭해 파이프라인을 생성합니다. 생성한 파이프라인을 선택한 뒤 하단의 **스테이지** 탭에서 **+스테이지 추가**를 클릭해 스테이지를 추가할 수 있습니다.

![stage-guide-01](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-01.png)

스테이지는 아래의 그룹으로 구분됩니다.
- **소스**
- **빌드**
- **배포**
- **기능**

### 소스
빌드할 소스 코드를 가져오는 스테이지입니다.

#### 소스 - GitHub
**소스 저장소**는 **환경 설정**의 **소스 저장소 설정**에서 추가한 [소스 저장소](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)를 선택할 수 있습니다. **브랜치**에는 빌드할 대상의 소스 브랜치를 입력합니다.

![stage-guide-02](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-02.png)

#### 소스 - GitLab
**소스 저장소**는 **환경 설정**의 **소스 저장소 설정**에서 추가한 [소스 저장소](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)를 선택할 수 있습니다. **브랜치**에는 빌드할 대상의 소스 브랜치를 입력합니다.

![stage-guide-03](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-03.png)

### 빌드
빌드를 하는 스테이지입니다.

#### 빌드 - Jenkins
사용자가 직접 구성한 Jenkins를 이용하여 빌드할 수 있습니다. **빌드 도구**는 **환경 설정**의 **빌드 도구 설정**에서 추가한 [빌드 도구](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)를 선택할 수 있습니다. **빌드 잡**을 선택하고 **빌드 잡 파라미터**를 입력할 수 있습니다.

![stage-guide-04](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-04.png)

#### 빌드 - NHN Cloud 빌드 도구
NHN Cloud에서 제공하는 빌드 도구를 사용할 수 있습니다.
- 빌드 환경 설정
  - **환경 설정**의 **이미지 저장소 설정**에서 추가한 [이미지 저장소](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)를 선택할 수 있습니다.
  - 빌드할 환경의 **이미지 이름**을 선택하고, **빌드 도구 성능**과 **빌드 시간 제한(분)**, **빌드 명령어**를 설정합니다.
  
- 빌드 결과 설정
  - 빌드 결과물의 **Dockerfile 경로**를 설정하고, **Dockerfile 실행 경로**를 설정합니다.
  - **이미지 저장소**를 선택하고, **이미지 이름**을 결정하면 해당 저장소로 결과물을 push합니다.
  - **태그 포맷 사용**을 선택하면 태그 포맷으로 태그가 고정되며 `_{BUILD_NUMBER}`형식으로 동적으로 생성되는 태그로 이미지가 생성됩니다.

![stage-guide-05](http://static.toastoven.net/prod_pipeline/2023-01-13/stage-guide-01.png)

### 배포
Kubernetes 환경에 배포를 하는 스테이지입니다.

#### 배포 - Deploy
**환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)을 선택할 수 있습니다.
**스테이지 이름**, **배포 대상**, 배포에 사용할 **Manifest**를 입력합니다.
빌드 스테이지에서 태그 포맷을 사용 했다면 **Manifest**의 도커 이미지 태그 부분을 `_{BUILD_NUMBER}`로 입력하면 태그 포맷으로 빌드된 이미지 중 가장 최근 번호의 이미지로 배포 할 수 있습니다.
**Manifest**를 작성하는 방법은 [Kubernetes 문서](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )를 참고하십시오.

![stage-guide-06](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-06.png)

#### 배포 - Patch
**환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)을 선택할 수 있습니다.
**Namespace**, **리소스 유형**, **리소스 이름**, 배포에 사용할 **Manifest**를 입력합니다. Patch로 기존 리소스의 정보를 수정할 수 있습니다.
**Manifest**를 작성하는 방법은 [Kubernetes 문서](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#patching-resources)를 참고하십시오.

![stage-guide-07](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-07.png)

#### 배포 - Scale
**환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)을 선택할 수 있습니다.
**Namespace**, **리소스 유형**, **리소스 이름**, **Replicas**를 입력합니다. Scale로 Replicas를 수정할 수 있습니다.

![stage-guide-08](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-08.png)

#### 배포 - Rollout undo
**환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)을 선택할 수 있습니다.
**Namespace**, **리소스 유형**, **리소스 이름**, **Revision Back**을 입력합니다. 지정한 Revision으로 롤백할 수 있습니다.

![stage-guide-09](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-09.png)

#### 배포 - Delete
**환경 설정**의 **배포 대상 설정**에서 추가한 [배포 대상](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/console-guide/#_1)을 선택할 수 있습니다.
**Namespace**, **리소스 유형**, **리소스 이름**을 입력합니다. 해당 리소스를 삭제할 수 있습니다.

![stage-guide-10](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-10.png)

### 기능
추가 기능을 제공하는 스테이지입니다.

#### 기능 - Webhook
**URL**에 HTTP 메소드와 URL을 입력합니다. 필요에 따라 **요청 헤더**와 **요청 데이터**를 추가할 수 있습니다.
Webhook의 응답값이 **Fail Fast HTTP 상태 코드**에 입력한 값 중 하나라면 그 즉시 해당 스테이지를 종료합니다.

![stage-guide-11](http://static.toastoven.net/prod_pipeline/2022-08-23/stage-guide-11.png)
