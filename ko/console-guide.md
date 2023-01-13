## Dev Tools > Pipeline > 콘솔 사용 가이드

콘솔 사용 가이드에서는 Pipeline을 사용하는데 필요한 기본적인 내용을 설명합니다.
- **환경 설정**
- **파이프라인 생성**
- **파이프라인 실행**
- **파이프라인 관리**
- **개발 환경 설정**

### 환경 설정

Pipeline은 애플리케이션 배포 흐름을 구성할 때 다양한 외부 시스템을 사용합니다. 환경 설정에서 Pipeline이 사용하는 외부 시스템을 추가할 수 있습니다.

Pipeline에 추가할 수 있는 외부 시스템은 아래와 같습니다.
- 소스 저장소
- 이미지 저장소
- 빌드 도구
- 배포 대상

#### 소스 저장소

소스 저장소를 추가하면 NHN Cloud 빌드 도구를 사용해서 소스 코드를 빌드할 수 있습니다. GitHub, GitLab, GitHub Enterprise와 같이 git 명령어를 사용해서 접근할 수 있는 저장소를 추가할 수 있습니다.

![console-guide-01](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-01.png)

**환경 설정**에서 **소스 저장소 설정**을 클릭하면 소스 저장소를 관리하는 화면으로 이동합니다. **소스 저장소 추가**를 클릭해서 소스 저장소를 추가할 수 있습니다. 

![console-guide-02](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-01.png)

소스 저장소 정보를 입력한 후 **소스 저장소 연결 확인**의 **확인**을 클릭합니다. GitLab 소스 저장소의 토큰 발급 시 `read_user`, `api`, `read_api` 권한이 필수로 필요합니다. 연결 확인 후 **확인**을 클릭합니다.

![console-guide-03](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-03.png)

#### 이미지 저장소

이미지 저장소를 추가하면 자격 증명이 필요한 이미지 저장소에 접근할 때 사용할 수 있습니다. NHN Cloud 빌드 도구에서 소스 코드를 빌드하는 컨테이너를 생성할 때 사용하거나 새로 생성한 컨테이너 이미지를 업로드할 때 사용할 수 있습니다. 그리고 파이프라인 자동 실행 설정에서 자동 실행을 실행시키는 컨테이너 이미지를 설정할 때 사용할 수 있습니다. 이미지 저장소에는 NHN Cloud Container Registry, Docker Hub, 그 밖에 Private Docker Registry를 추가할 수 있습니다.

![console-guide-04](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-04.png)

**환경 설정**에서 **이미지 저장소 설정**을 클릭하면 이미지 저장소를 관리하는 화면으로 이동합니다. **이미지 저장소 추가**를 클릭해서 이미지 저장소를 추가할 수 있습니다.

![console-guide-05](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-02.png)

이미지 저장소 정보를 입력한 후 **이미지 저장소 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다. 이미지 저장소 URL을 입력하지 않으면 Docker Hub로 동작합니다.

![console-guide-06](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-06.png)

#### 빌드 도구

빌드 도구를 추가하면 파이프라인에서 빌드 도구에 정의한 다양한 작업을 사용할 수 있습니다. 빌드 도구에는 Jenkins를 추가할 수 있습니다.

![console-guide-07](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-07.png)

**환경 설정**에서 **빌드 도구 설정**을 클릭하면 빌드 도구를 관리하는 화면으로 이동합니다. **빌드 도구 추가**를 클릭해서 빌드 도구를 추가할 수 있습니다.

![console-guide-08](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-03.png)

빌드 도구 정보를 입력한 후 **빌드 도구 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다.

![console-guide-09](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-09.png)

#### 배포 대상

배포 대상을 추가하면 파이프라인에서 배포 대상을 관리할 수 있습니다. 배포 대상에 컨테이너 이미지를 배포하거나 실행 중인 컨테이너를 변경할 수 있습니다. 배포 대상에는 NHN Cloud Container, Kubernetes를 추가할 수 있습니다.

![console-guide-10](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-10.png)

**환경 설정**에서 **배포 대상 설정**을 클릭하면 배포 대상을 관리하는 화면으로 이동합니다. **배포 대상 추가**를 클릭해서 배포 대상을 추가할 수 있습니다.

![console-guide-11](http://static.toastoven.net/prod_pipeline/2022-05-24/console-guide-04.png)

배포 대상 이름과 배포 대상 설명을 입력하고 Kubeconfig 파일을 선택한 후 **배포 대상 연결 확인**의 **확인**을 클릭합니다. 연결 확인 후 **확인**을 클릭합니다.

![console-guide-12](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-12.png)


#### Pipeline IP
Pipeline과 연동한 시스템이 정상적으로 동작하지 않으면 ACL을 확인하시기 바랍니다. Pipeline이 사용하는 IP 주소는 **211.56.1.0/27**입니다.

| 서비스 | CIDR |
|---|---|
| Pipeline | 211.56.1.0/27 |

### 파이프라인 생성

Pipeline은 애플리케이션 배포 흐름을 한 개 이상의 스테이지로 구성한 파이프라인으로 저장합니다. 파이프라인 생성에서는 **소스 코드 빌드** > **컨테이너 이미지 생성** > **컨테이너 이미지 업로드** > **컨테이너 이미지 배포** 순서로 동작하는 기본적인 파이프라인을 생성할 수 있습니다.

![console-guide-13](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-13.png)

**파이프라인 관리**에서 **파이프라인 생성**을 클릭합니다. 파이프라인 생성은 아래와 같은 단계로 진행합니다.
- 파이프라인 정보 입력
- 소스 설정
- 빌드 설정
- 배포 설정
- 최종 검토 및 파이프라인 생성

#### 파이프라인 정보 입력

파이프라인 기본 정보를 입력합니다.

![console-guide-14](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-14.png)

파이프라인 이름, 파이프라인 설명을 입력한 후 **다음**을 클릭합니다.

#### 소스 설정

NHN Cloud 빌드 도구에서 소스 코드를 빌드할 때 사용하는 소스 저장소를 설정합니다. NHN Cloud 빌드 도구를 사용하지 않거나 NHN Cloud 빌드 도구에서 소스 코드를 빌드하지 않으면 생략할 수 있습니다.

![console-guide-15](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-15.png)

스테이지 이름, 환경 설정에서 등록한 소스 저장소, 소스 코드를 빌드할 브랜치를 입력한 후 **다음**을 클릭합니다.

#### 빌드 설정

빌드 설정에서는 NHN Cloud 빌드 도구를 사용하거나 환경 설정에서 등록한 빌드 도구를 사용할 수 있습니다. 스테이지 이름을 입력하고 **빌드 도구**에서 사용할 빌드 도구를 선택합니다.

![console-guide-16](http://static.toastoven.net/prod_pipeline/2023-01-13/console-guide-01.png)

NHN Cloud 빌드 도구를 사용하면 별도의 소프트웨어 설치 없이 소스 저장소에 저장한 애플리케이션 소스 코드를 빌드하고, 빌드한 애플리케이션으로 컨테이너 이미지를 생성하고, 생성한 컨테이너 이미지를 이미지 저장소에 업로드할 수 있습니다.
**빌드 환경 설정**에는 **소스 설정**에서 설정한 소스 코드를 사용해서 애플리케이션을 빌드하는 방법을 입력합니다. 소스 코드 빌드에 사용할 컨테이너 이미지, 빌드 머신의 성능, 빌드에 사용할 명령어를 입력할 수 있습니다.
**빌드 결과 설정**에는 빌드한 애플리케이션으로 컨테이너 이미지를 만드는 방법을 입력합니다. 컨테이너 이미지를 생성할 때 사용할 Dockerfile, 생성한 컨테이너 이미지를 업로드할 이미지 저장소, 업로드할 컨테이너 이미지의 이름과 태그를 입력할 수 있습니다.
**태그 포맷 사용** 체크 박스를 클릭하면 이미지 태그 포맷을 사용 할 수 있습니다. 이미지 태그 포맷을 사용하면 생성된 이미지의 태그를 NHN Cloud 빌드도구에서 부여하는 빌드 번호로 사용하게 됩니다. 생성되는 태그는 `_{BUILD_NUMBER}` 형식이며 BUILD_NUMBER가 빌드 번호 입니다.
빌드 번호는 빌드마다 증가하는 숫자형 데이터 입니다. 이미지 태그 포맷 사용 시에는 태그가 `_{BUILD_NUMBER}` 형태로 고정됩니다.

![console-guide-17](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-17.png)

환경 설정에서 추가한 빌드 도구를 사용하면 빌드 도구의 빌드 잡을 실행할 수 있습니다. 실행할 빌드 잡을 선택하면 빌드 잡의 파라미터를 추가로 입력할 수 있습니다.

빌드 설정을 완료한 후 **다음**을 클릭합니다.

#### 배포 설정

배포 설정은 환경 설정에서 추가한 배포 대상에 컨테이너 이미지를 배포하는 방법을 설정합니다.

![console-guide-18](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-18.png)

스테이지 이름, 배포 대상, 배포에 사용할 Manifest를 입력한 후 **다음**을 클릭합니다. Manifest를 작성하는 방법은 [Kubernetes 문서](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )를 참고하십시오.

![console-guide-38](http://static.toastoven.net/prod_pipeline/2023-01-13/console-guide-02.png)

빌드 설정에서 태그 포맷을 사용 했다면 도커 이미지 입력 부분에 태그를 위와 같이`_{BUILD_NUMBER}`로 입력합니다. 이미지의 태그에 `_{BUILD_NUMBER}`가 입력된 경우 가장 최신의 번호로 입력되어 배포 됩니다.
태그 포맷을 사용하기 위해서는 빌드 스테이지 및 NHN Cloud 빌드 도구 설정이 필요 합니다.

#### 최종 검토 및 파이프라인 생성

최종 검토에서는 파이프라인에 설정한 전체 입력 내용을 확인할 수 있습니다.

![console-guide-19](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-19.png)

입력한 내용을 확인한 후 **생성**을 클릭합니다.

![console-guide-20](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-20.png)

### 파이프라인 실행

파이프라인을 실행하는 방법은 수동 실행과 자동 실행이 있습니다.

#### 수동 실행

수동 실행을 사용하면 사용자가 원할 때 파이프라인을 실행할 수 있습니다.

![console-guide-21](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-21.png)

**파이프라인 관리**에서 ▶︎(수동 실행)를 클릭하고 대화 상자가 나타나면 **확인**을 클릭합니다.

#### 자동 실행

자동 실행을 사용하면 GitHub Repository에 이벤트가 발생하거나 이미지 저장소의 컨테이너 이미지를 갱신하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다.

![console-guide-22](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-22.png)

**자동 실행 설정**을 클릭한 뒤 **자동 실행 설정** 대화 상자에서 **추가**를 클릭합니다.

![console-guide-23](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-23.png)

GitHub 웹훅을 사용해서 GitHub 또는 GitHub Enterprise의 Repository에 이벤트가 발생하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다. 자동 실행 유형을 GitHub으로 설정하고 Repository의 조직 혹은 사용자 이름, 프로젝트 이름, 브랜치, 시크릿을 입력하고 **확인**을 클릭합니다.

![console-guide-24](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-24.png)

GitHub 또는 GitHub Enterprise의 Repository에서 웹훅을 설정합니다.

| 항목 | 설정값 |
|---|---|
| Payload URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | 파이프라인 자동 실행 설정의 시크릿에 입력한 값 |

![console-guide-35](http://static.toastoven.net/prod_pipeline/2022-02-15/console-guide-02.png)

GitLab 웹훅을 사용해서 GitLab Repository에 이벤트가 발생하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다. 자동 실행 유형을 GitLab으로 설정하고 Repository의 조직 혹은 사용자 이름, 프로젝트 이름, 브랜치를 입력하고 **확인**을 클릭합니다. GitLab 시크릿 설정은 추후 지원할 예정입니다.

![console-guide-36](http://static.toastoven.net/prod_pipeline/2022-02-15/console-guide-03.png)
GitLab Repository에서 웹훅을 설정합니다.

| 항목 | 설정값 |
|---|---|
| URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Push events 체크 |
| Secret | 설정하지 않음 |
| SSL verification | Enable SSL verification 체크 |


![console-guide-37](http://static.toastoven.net/prod_pipeline/2022-07-26/console-guide-01.png)
GitLab의 사용자 이름으로 자동 실행 설정 시 GitLab의 사용자 이름과 Full name이 다른 경우 자동 실행이 동작하지 않을 수 있으니 같은 값으로 설정해야 합니다.


![console-guide-25](http://static.toastoven.net/prod_pipeline/2023-01-13/console-guide-03.png)

컨테이너 이미지를 갱신했을 때 파이프라인을 자동으로 실행하려면 자동 실행 유형을 이미지 저장소로 설정합니다. 
환경 설정에서 등록한 이미지 저장소를 선택한 후 이미지 이름을 입력합니다. 이미지 이름은 NHN Cloud Container Registry의 경우 `registry명/이미지이름`의 형태로 입력합니다.
DockerHub의 경우 `도커허브계정/이미지이름` 형식으로 입력합니다. 태그는 JAVA 정규 표현식이 사용 가능하며 입력한 태그와 매칭되는 태그가 push 되었을 경우 자동실행 됩니다.
태그를 입력하지 않을 시 latest를 제외한 신규 태그가 push되었을 경우 자동실행 됩니다.
입력을 마친 후 **확인**을 클릭합니다.

![console-guide-26](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-26.png)

파이프라인을 새로 만들면 **자동 실행 방지**를 **사용**으로 설정합니다. 파이프라인을 자동으로 실행하려면 **자동 실행 방지**를 **미사용**으로 변경해야 합니다. 파이프라인을 선택한 후 하단 기본 정보의 자동 실행 방지에서 **변경**을 클릭합니다. 자동 실행 방지 설정 대화 상자에서 **미사용**을 선택한 후 **확인**을 클릭합니다.

![console-guide-27](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-27.png)

실행 중인 파이프라인의 상세 정보를 확인하려면 실행 중인 파이프라인을 선택한 후 하단 기본 정보의 최근 실행 상태에서 **상세 정보**를 클릭합니다.

### 파이프라인 관리

사용자는 파이프라인을 구성하는 스테이지를 추가, 변경, 삭제할 수 있습니다.

![console-guide-28](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-28.png)

파이프라인을 선택한 후 하단의 **스테이지**를 클릭하면 스테이지 관리 화면이 나타납니다. **스테이지 추가**를 클릭하면 **스테이지 추가** 대화 상자가 나타납니다.

![console-guide-29](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-29.png)

스테이지 이름, 스테이지 유형, 스테이지 유형별 입력값, 이전 단계를 설정한 후 **스테이지 추가**를 클릭해서 파이프라인에 스테이지를 추가할 수 있습니다. Pipeline은 애플리케이션 배포 흐름을 구성할 때 사용할 수 있는 다양한 스테이지 유형을 제공합니다.

![console-guide-30](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-30.png)

이전 스테이지를 선택하는 방식에 따라 스테이지를 병렬로 실행할 수 있습니다. 병렬 구성한 스테이지 중 하나가 실패하면 나머지 스테이지는 실행이 취소되고 파이프라인 실행은 실패합니다.

### 개발 환경 설정

개발 환경 설정을 사용하면 Kubernetes 사용법을 모르는 사용자도 Kubernetes에 컨테이너 이미지를 배포할 수 있습니다.

![console-guide-31](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-31.png)

**개발 환경 설정**에서 **개발 환경 생성**을 클릭합니다. 

![console-guide-32](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-32.png)

개발 환경 이름과 개발 환경 설명을 입력하고 기본 이미지에서 배포할 컨테이너 이미지를 선택합니다. 컨테이너 이미지 접근에 필요한 정보는 이미지 저장소에 설정합니다. 배포 대상은 컨테이너 이미지를 배포할 Kubernetes를 선택합니다. 서비스 포트는 컨테이너가 제공하는 서비스의 포트를 입력합니다. 서비스 포트를 입력하면 컨테이너 서비스에 접근할 수 있는 서비스 IP를 자동으로 할당(Kubernetes가 LoadBalancer 타입의 서비스를 제공할 경우)합니다. 마지막으로 개발 환경 제약 사항을 입력한 후 **생성**을 클릭하면 개발 환경을 생성합니다.

![console-guide-33](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-33.png)

개발 환경이 생성되는 동안 **개발 환경 상태**는 **생성 중**으로 표시됩니다.

![console-guide-34](http://static.toastoven.net/prod_pipeline/2021-04-27/console-guide-34.png)

개발 환경 생성이 완료되면 **개발 환경 상태**가 **실행 중**으로 변경됩니다. 서비스 IP와 서비스 포트를 사용해서 컨테이너 서비스에 접근할 수 있습니다.
