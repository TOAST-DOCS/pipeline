## Dev Tools > Pipeline > 콘솔 사용 가이드 > 환경 설정

### 환경 설정

Pipeline은 애플리케이션 배포 흐름을 구성할 때 다양한 외부 시스템을 사용합니다. 환경 설정에서 Pipeline이 사용하는 외부 시스템을 추가할 수 있습니다.

Pipeline에 추가할 수 있는 외부 시스템은 아래와 같습니다.
- 소스 저장소
- 이미지 저장소
- 빌드 도구
- 배포 대상
- 차트 저장소

### 소스 저장소

소스 저장소를 추가하면 NHN Cloud 빌드 도구를 사용해서 소스 코드를 빌드할 수 있습니다. GitHub, GitLab, GitHub Enterprise와 같이 git 명령어를 사용해서 접근할 수 있는 저장소를 추가할 수 있습니다.

![env-config-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-01.png)

**환경 설정**에서 **소스 저장소 설정**을 클릭하면 소스 저장소를 관리하는 화면으로 이동합니다. **소스 저장소 추가**를 클릭해서 신규 소스 저장소를 추가할 수 있습니다.

![env-config-guide-02](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-02.png)

소스 저장소 정보를 입력한 후 **소스 저장소 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다.
- GitHub 소스 저장소의 토큰 발급 시 `repo` 권한이 필요합니다.
- GitLab 소스 저장소의 토큰 발급 시 `read_user`, `api`, `read_api` 권한이 필요합니다.

![env-config-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-03.png)

### 이미지 저장소

이미지 저장소를 추가하면 자격 증명이 필요한 이미지 저장소에 접근할 때 사용할 수 있습니다. NHN Cloud 빌드 도구에서 소스 코드를 빌드하는 컨테이너를 생성할 때 사용하거나 새로 생성한 컨테이너 이미지를 업로드할 때 사용할 수 있습니다. 그리고 파이프라인 자동 실행 설정에서 자동 실행을 실행시키는 컨테이너 이미지를 설정할 때 사용할 수 있습니다. 이미지 저장소에는 NHN Cloud Container Registry, Docker Hub, 그 밖에 사설 이미지 저장소를 추가할 수 있습니다. Docker Hub를 사용하는 경우 이미지 저장소 URL을 생략할 수 있습니다.

![env-config-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-04.png)

**환경 설정**에서 **이미지 저장소 설정**을 클릭하면 이미지 저장소를 관리하는 화면으로 이동합니다. **이미지 저장소 추가**를 클릭해서 신규 이미지 저장소를 추가할 수 있습니다.

![env-config-guide-05](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-05.png)

이미지 저장소 정보를 입력한 후 **이미지 저장소 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다. 이미지 저장소 URL을 입력하지 않으면 Docker Hub로 동작합니다.

![env-config-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-06.png)

### 빌드 도구

빌드 도구를 추가하면 파이프라인에서 빌드 도구에 정의한 다양한 작업을 사용할 수 있습니다. 빌드 도구에는 Jenkins를 추가할 수 있습니다. `NHN Cloud 빌드 도구` 를 사용하는 경우 빌드 도구 추가 작업을 생략할 수 있습니다.

![env-config-guide-07](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-07.png)

**환경 설정**에서 **빌드 도구 설정**을 클릭하면 빌드 도구를 관리하는 화면으로 이동합니다. **빌드 도구 추가**를 클릭해서 신규 빌드 도구를 추가할 수 있습니다.

![env-config-guide-08](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-08.png)

빌드 도구 정보를 입력한 후 **빌드 도구 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다.

![env-config-guide-09](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-09.png)

### 배포 대상

배포 대상을 추가하면 파이프라인에서 배포 대상을 관리할 수 있습니다. 배포 대상에 컨테이너 이미지를 배포하거나 실행 중인 컨테이너를 변경할 수 있습니다. 배포 대상에는 NHN Cloud Container, Kubernetes를 추가할 수 있습니다.

![env-config-guide-10](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-10.png)

**환경 설정**에서 **배포 대상 설정**을 클릭하면 배포 대상을 관리하는 화면으로 이동합니다. **배포 대상 추가**를 클릭해서 신규 배포 대상을 추가할 수 있습니다.

![env-config-guide-11](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-11.png)

배포 대상 이름과 배포 대상 설명을 입력하고 Kubeconfig 파일을 선택한 후 **배포 대상 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다.

![env-config-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-12.png)

### 차트 저장소

차트 저장소를 추가하면 **빌드 - Bake (Manifest)** 스테이지를 사용해서 Helm 차트를 빌드할 수 있습니다. [차트 저장소 가이드](https://helm.sh/docs/topics/chart_repository/)에서 차트 저장소의 구성 방법을 확인할 수 있습니다.

![env-config-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-13.png)

**환경 설정**에서 **차트 저장소 설정**을 클릭하면 차트 저장소를 관리하는 화면으로 이동합니다. **차트 저장소 추가**를 클릭해서 신규 차트 저장소를 추가할 수 있습니다.

![env-config-guide-14](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-14.png)

차트 저장소 정보를 입력한 후 **차트 저장소 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다.

![env-config-guide-15](http://static.toastoven.net/prod_pipeline/2023-03-28/env-config-guide-15.png)


### Pipeline IP
파이프라인과 연동한 시스템이 정상적으로 동작하지 않으면 ACL을 확인하십시오. 파이프라인이 사용하는 IP 주소는 **211.56.1.0/27**입니다.

| 서비스 | CIDR |
|---|---|
| Pipeline | 211.56.1.0/27 |