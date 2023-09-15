## Dev Tools > Pipeline > 콘솔 사용 가이드 > 파이프라인 관리

### 파이프라인 생성

Pipeline은 애플리케이션 배포 흐름을 한 개 이상의 스테이지로 구성한 파이프라인으로 저장합니다. 파이프라인 생성에서는 **소스 코드 빌드** > **컨테이너 이미지 생성** > **컨테이너 이미지 업로드** > **컨테이너 이미지 배포** 순서로 동작하는 기본적인 파이프라인을 생성할 수 있으며 파이프라인 템플릿 파일을 업로드하여 파이프라인을 생성할 수도 있습니다.

![pipeline-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-01.png)

**파이프라인 관리**에서 **파이프라인 생성**을 클릭합니다. 파이프라인 생성은 아래와 같은 단계로 진행합니다.
- 파이프라인 정보 입력
- 소스 설정
- 빌드 설정
- 배포 설정
- 최종 검토 및 파이프라인 생성

#### 파이프라인 정보 입력

파이프라인 기본 정보를 입력합니다.

![pipeline-guide-33](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-33.png)

파이프라인 이름, 파이프라인 설명을 입력한 후 **다음**을 클릭합니다.

추가로 파이프라인 템플릿 파일로 파이프라인을 생성할 수도 있습니다(파이프라인 템플릿 파일은 JSON 파일을 사용합니다.).

![pipeline-guide-34](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-34.png)

파이프라인 이름, 파이프라인 설명을 입력하고 파이프라인 템플릿 파일을 업로드한 후 **다음**을 클릭합니다.

#### 소스 설정

NHN Cloud 빌드 도구에서 소스 코드를 빌드할 때 사용하는 소스 저장소를 설정합니다. NHN Cloud 빌드 도구를 사용하지 않거나 NHN Cloud 빌드 도구에서 소스 코드를 빌드하지 않으면 생략할 수 있습니다.

![pipeline-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-03.png)

스테이지 이름, 환경 설정에서 등록한 소스 저장소, 소스 코드를 빌드할 대상 브랜치(git branch)를 입력한 후 **다음**을 클릭합니다.

#### 빌드 설정

빌드 설정에서는 NHN Cloud 빌드 도구를 사용하거나 환경 설정에서 등록한 빌드 도구를 사용할 수 있습니다. 스테이지 이름을 입력하고 **빌드 도구**에서 사용할 빌드 도구를 선택합니다.

![pipeline-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-04.png)

NHN Cloud 빌드 도구를 사용하면 별도의 소프트웨어 설치 없이 소스 저장소에 저장한 애플리케이션 소스 코드를 빌드하고, 빌드한 애플리케이션으로 컨테이너 이미지를 생성하고, 생성한 컨테이너 이미지를 이미지 저장소에 업로드할 수 있습니다.
**빌드 환경 설정**에는 **소스 설정**에서 설정한 소스 코드를 사용해서 애플리케이션을 빌드하는 방법을 입력합니다. 소스 코드 빌드에 사용할 컨테이너 이미지, 빌드 머신의 성능, 빌드에 사용할 명령어를 입력할 수 있습니다.
**빌드 결과 설정**에는 빌드한 애플리케이션으로 컨테이너 이미지를 만드는 방법을 입력합니다. 컨테이너 이미지를 생성할 때 사용할 Dockerfile, 생성한 컨테이너 이미지를 업로드할 이미지 저장소, 업로드할 컨테이너 이미지의 이름과 태그를 입력할 수 있습니다.
**태그 포맷 사용** 체크 박스를 클릭하면 이미지 태그 포맷을 사용할 수 있습니다. 이미지 태그 포맷을 사용하면 생성된 이미지의 태그를 NHN Cloud 빌드 도구에서 부여하는 빌드 번호로 사용하게 됩니다. 생성되는 태그는 `_{BUILD_NUMBER}` 형식이며 BUILD_NUMBER가 빌드 번호 입니다.
빌드 번호는 빌드마다 증가하는 숫자형 데이터입니다. 이미지 태그 포맷 사용 시에는 태그가 `_{BUILD_NUMBER}` 형태로 고정됩니다.

![pipeline-guide-05](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-05.png)
NHN Cloud 빌드 도구에서 **아티팩트** 설정을 사용하여 **시작 조건**과 **종료 조건**을 설정할 수 있습니다.
시작 조건으로 설정된 **아티팩트**는 스테이지 시작 시 존재 유무를 확인하여 스테이지의 진행 여부를 결정합니다.
종료 조건으로 설정된 **아티팩트**는 스테이지의 생산물을 **아티팩트**로 설정합니다.

#### NHN Cloud 빌드 도구에서 설정 가능한 아티팩트

GitHub 및 GitLab은 브랜치를 입력하지 않을 경우 master 브랜치를 기본값으로 사용합니다.

| 아티팩트 종류    | 사용 조건  | 경로 또는 레퍼런스 설정 예시                                                                                                                                                                                        |
|------------|--------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHub 파일  | 시작     | https://api.github.com/repos/{organization}/{repository}/contents/{file-path} <br/> GitHub Enterprise일 때의 예시: https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLab 파일  | 시작     | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                        |
| Docker 컨테이너 이미지 | 시작, 종료 | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                        |
| HTTP 파일    | 시작 | 접근 가능한 URL                                                                                                                                                                                              |


![pipeline-guide-06](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-06.png)

환경 설정에서 추가한 빌드 도구를 사용하면 빌드 도구의 빌드 잡을 실행할 수 있습니다. 실행할 빌드 잡을 선택하면 빌드 잡의 파라미터를 추가로 입력할 수 있습니다.

![pipeline-guide-07](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-07.png)
**아티팩트** 설정을 사용하여 **시작 조건**과 **종료 조건**을 설정할 수 있습니다.
시작 조건으로 설정된 **아티팩트**는 스테이지 시작 시 존재 유무를 확인하여 스테이지의 진행 여부를 결정합니다.
종료 조건으로 설정된 **아티팩트**는 스테이지의 생산물을 **아티팩트**로 설정합니다.

#### 빌드 도구에서 설정 가능한 아티팩트

GitHub 및 GitLab은 브랜치를 입력하지 않을 경우 master 브랜치를 기본값으로 사용합니다.

| 아티팩트 종류    | 사용 조건  | 경로 또는 레퍼런스 설정 예시                                                                                                                                                                                         |
|------------|--------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHub 파일  | 시작     | https://api.github.com/repos/{organization}/{repository}/contents/{file-path}  <br/> GitHub Enterprise일 때의 예시: https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLab 파일  | 시작     | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                         |
| Docker 컨테이너 이미지 | 시작     | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                         |
| HTTP 파일    | 시작, 종료 | 접근 가능한 URL                                                                                                                                                                                               |

빌드 설정을 완료한 후 **다음**을 클릭합니다.

#### 배포 설정

배포 설정은 환경 설정에서 추가한 배포 대상에 컨테이너 이미지를 배포하는 방법을 설정합니다.

![pipeline-guide-08](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-08.png)

스테이지 이름, 배포 대상, 배포에 사용할 Kubernetes Manifest를 입력한 후 **다음**을 클릭합니다. Manifest를 작성하는 방법은 [Kubernetes 문서](https://kubernetes.io/docs/concepts/workloads/controllers/deployment )를 참고하십시오.

![pipeline-guide-09](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-09.png)

빌드 설정에서 태그 포맷을 사용했다면 도커(Docker) 이미지 입력 부분에 태그를 위와 같이`_{BUILD_NUMBER}`로 입력합니다. 이미지의 태그에 `_{BUILD_NUMBER}`가 입력된 경우 가장 최신의 번호로 입력되어 배포됩니다.
태그 포맷을 사용하려면 빌드 스테이지 및 NHN Cloud 빌드 도구를 설정해야 합니다.

![pipeline-guide-10](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-10.png)
**아티팩트** 설정을 사용하여 **시작 조건**과 **종료 조건**을 설정할 수 있습니다.
시작 조건으로 설정된 **아티팩트**는 스테이지 시작 시 존재 유무를 확인하여 스테이지의 진행 여부를 결정합니다.
종료 조건으로 설정된 **아티팩트**는 스테이지의 생산물을 **아티팩트**로 설정합니다.
입력한 manifest에 **종료 조건**과 매칭되는 Kubernetes 오브젝트가 없어 스테이지가 실패하더라도 manifest가 Kubernetes 클러스터에 적용될 수 있습니다.

#### 배포 설정에서 설정 가능한 아티팩트

GitHub 및 GitLab은 브랜치를 입력하지 않을 경우 master 브랜치를 기본값으로 사용합니다.

| 아티팩트 종류    | 사용 조건  | 경로 또는 레퍼런스 설정 예시                                                                                                                                                                                          |
|------------|--------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| GitHub 파일  | 시작     | https://api.github.com/repos/{organization}/{repository}/contents/{file-path}   <br/> GitHub Enterprise일 때의 예시: https://github.mydomain.com/api/v3/repos/{organization}/{repository}/contents/{file-path} |
| GitLab 파일  | 시작     | https://gitlab.com/api/v4/projects/{project-number}/repository/files/{file-path}                                                                                                                          |
| Docker 컨테이너 이미지 | 시작 | {domain}/{dockerhub-account or image-registry-path}/{image-name}                                                                                                                                          |
| HTTP 파일    | 시작 | 접근 가능한 URL                                                                                                                                                                                                |
| kubernetes 오브젝트 | 종료 | 오브젝트의 이름                                                                                                                                                                                                  |

#### 최종 검토 및 파이프라인 생성

최종 검토에서는 파이프라인에 설정한 전체 입력 내용을 확인할 수 있습니다.

![pipeline-guide-11](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-11.png)

만약, 파이프라인 템플릿 파일로 생성했을 경우 업로드한 파일 이름을 확인할 수 있습니다.

![pipeline-guide-35](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-35.png)

입력한 내용을 확인한 후 **생성**을 클릭합니다.

![pipeline-guide-12](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-12.png)

### 파이프라인 실행

파이프라인을 실행하는 방법은 수동 실행과 자동 실행이 있습니다.

#### 수동 실행

수동 실행을 사용하면 사용자가 원할 때 파이프라인을 실행할 수 있습니다.

![pipeline-guide-13](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-13.png)

**파이프라인 관리**에서 ▶︎(수동 실행)를 클릭하고 대화 상자가 나타나면 **확인**을 클릭합니다.

#### 자동 실행

자동 실행을 사용하면 GitHub 또는 GitLab 저장소에 이벤트가 발생하거나 이미지 저장소의 컨테이너 이미지를 갱신하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다.

![pipeline-guide-14](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-14.png)

**자동 실행 설정**을 클릭한 뒤 **자동 실행 설정** 대화 상자에서 **추가**를 클릭합니다.

![pipeline-guide-15](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-15.png)

#### GitHub 자동 실행 설정

GitHub 웹훅을 사용해서 GitHub 또는 GitHub Enterprise의 저장소에 이벤트가 발생하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다. 자동 실행 유형을 GitHub으로 설정하고 저장소의 조직 또는 사용자 이름, 프로젝트 이름, 브랜치, 시크릿을 입력하고 **확인**을 클릭합니다.
태그로 자동 실행 설정을 하기 위해서는 **브랜치 또는 태그** 항목에 'refs/tags/태그명'과 같이 태그명을 입력합니다. '태그명' 부분에는 JAVA 정규 표현식을 사용할 수 있습니다.
태그로 자동 실행 설정후 NHN Cloud 빌드 도구 사용시 설정된 태그로 빌드를 수행합니다. 빌드 - Jenkins 스테이지에서 태그로 빌드를 수행하고 싶을 땐 다음과 같이 설정이 필요합니다.

Jenkins에서 다음과 같이 파라미터를 설정합니다.
![pipeline-guide-39.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-39.png)
![pipeline-guide-40.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-40.png)
Pipeline의 빌드도구 설정에서 **빌드 잡 파라미터**에 다음과 같이 입력합니다.
![pipeline-guide-41.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-41.png)

#### GitHub 웹훅 설정값

![pipeline-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-16.png)


| 항목 | 설정값 |
|---|---|
| Payload URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | 파이프라인 자동 실행 설정의 시크릿에 입력한 값 |
| event | push event, create event(태그 사용 시) |

![pipeline-guide-17](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-17.png)

#### GitLab 자동 실행 설정

GitLab 웹훅을 사용해서 GitLab 저장소에 이벤트가 발생하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다. 자동 실행 유형을 GitLab으로 설정하고 저장소의 조직 또는 사용자 이름, 프로젝트 이름, 브랜치를 입력하고 **확인**을 클릭합니다. GitLab 시크릿 설정은 추후 지원할 예정입니다.

#### GitLab 웹훅 설정값

![pipeline-guide-18](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-18.png)


| 항목 | 설정값 |
|---|---|
| URL | https://kr1-pipeline.api.nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Push events 체크 |
| Secret | 설정하지 않음 |
| SSL verification | Enable SSL verification 체크 |

#### GitLab 웹훅 설정 시 주의 사항

GitLab의 사용자 이름으로 자동 실행을 설정할 때 사용자 이름을 GitLab의 사용자 이름과 동일하게 설정해야 합니다. 사용자 이름을 다르게 설정할 경우 자동 실행이 동작하지 않을 수 있습니다.

![pipeline-guide-19](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-19.png)

#### 이미지 저장소 자동 실행 설정

![pipeline-guide-20](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-20.png)

컨테이너 이미지를 갱신했을 때 파이프라인을 자동으로 실행하려면 **자동 실행 유형**을 **이미지 저장소**로 설정합니다.
**이미지 저장소**를 **환경 설정**에서 등록한 항목으로 선택한 뒤 **이미지 이름**을 입력합니다. 이미지 이름은 NHN Cloud Container Registry의 경우 `registry명/이미지 이름`의 형태로 입력합니다.
Docker Hub의 경우 `Docker Hub 계정/이미지 이름` 형식으로 입력합니다. **태그**는 JAVA 정규 표현식을 사용할 수 있으며 입력한 태그와 매칭되는 태그가 push되었을 경우 자동 실행됩니다.
태그를 입력하지 않으면 latest를 제외한 신규 태그가 push될 경우 자동 실행됩니다.
입력을 마친 후 **확인**을 클릭합니다.

![pipeline-guide-21](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-21.png)

파이프라인을 새로 만들면 **자동 실행 방지**가 기본적으로 적용됩니다. 파이프라인을 자동으로 실행하려면 **자동 실행 방지**를 **미사용**으로 변경해야 합니다. 파이프라인을 선택한 후 하단 기본 정보의 자동 실행 방지에서 **변경**을 클릭합니다. 자동 실행 방지 설정 대화 상자에서 **미사용**을 선택한 후 **확인**을 클릭합니다.

![pipeline-guide-22](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-22.png)

실행 중인 파이프라인의 상세 정보를 확인하려면 실행 중인 파이프라인을 선택한 후 하단 기본 정보의 최근 실행 상태에서 **상세 정보**를 클릭합니다.

#### 실행 이력

파이프라인을 수동 실행, 자동 실행할 경우 실행 이력 탭에서 실행 이력을 확인할 수 있습니다.

![pipeline-guide-26](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-26.png)

### 파이프라인 관리

사용자는 파이프라인을 구성하는 스테이지를 추가, 변경, 삭제할 수 있습니다.

![pipeline-guide-23](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-23.png)

파이프라인을 선택한 후 하단의 **스테이지**를 클릭하면 스테이지 관리 화면이 나타납니다. **스테이지 추가**를 클릭하면 **스테이지 추가** 대화 상자가 나타납니다.

![pipeline-guide-24](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-24.png)

스테이지 이름, 스테이지 유형, 스테이지 유형별 입력값, 이전 단계를 설정한 후 **스테이지 추가**를 클릭해서 파이프라인에 스테이지를 추가할 수 있습니다. Pipeline은 애플리케이션 배포 흐름을 구성할 때 사용할 수 있는 다양한 스테이지 유형을 제공합니다.

![pipeline-guide-25](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-25.png)

이전 스테이지를 선택하는 방식에 따라 스테이지를 병렬로 실행할 수 있습니다. 병렬 구성한 스테이지 중 하나가 실패하면 나머지 스테이지는 실행이 취소되고 파이프라인 실행은 실패합니다.

#### 파이프라인 JSON 수정 및 다운로드
JSON 수정을 통해 파이프라인을 변경할 수 있습니다. 

![pipeline-guide-36](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-36.png)

**JSON 보기**를 클릭하여 JSON 형식으로 파이프라인을 확인할 수 있습니다.

![pipeline-guide-37](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-37.png)

**파이프라인 템플릿 다운로드**를 클릭하여 JSON 파일로 저장할 수 있습니다.

**편집**을 클릭하여 화면에서 JSON 파일을 직접 수정할 수 있습니다.

![pipeline-guide-38](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2023-09-26/pipeline-guide-38.png)

수정 후 **확인**을 클릭하면 수정된 내용이 파이프라인에 반영됩니다. 단, 입력 값이 잘못된 경우 오류 메시지를 노출합니다.

#### 실행 이력과 작업

**실행 이력**에서 실행 이력의 확인과 Judgement 스테이지의 실행 설정 선택, 스테이지 실행 중지/스테이지 실행에 대한 결정을 합니다.

![pipeline-guide-26](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-26.png)

**실행 이력**에서 현재 실행 중인 파이프라인 이력을 선택하면 다음과 같이 실행 중인 스테이지 정보들이 보입니다.

![pipeline-guide-27](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-27.png)


실행 중인 파이프라인 스테이지 중 Judgement 스테이지가 선택 대기 중 일 경우 **관리** 버튼이 보이고, 그 버튼을 누르면 다음과 같은 팝업이 뜨고 스테이지 추가, 변경 시 입력하였던 **설명**, **실행 설정**값과 **스테이지 실행 중지/스테이지 실행**을 선택할 수 있습니다.

![pipeline-guide-28](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-28.png)
![pipeline-guide-29](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-29.png)
![pipeline-guide-30](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-30.png)

만약 실행 설정값을 입력하지 않았다면 실행 설정 선택 없이 **스테이지 실행 중지/스테이지 실행**만을 선택합니다.

![pipeline-guide-31](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-31.png)

사용자의 선택에 따라 스테이지 설정대로 실행되며 실행 이력은 5초마다 갱신됩니다.

![pipeline-guide-32](http://static.toastoven.net/prod_pipeline/2023-06-20/pipeline-guide-32.png)

**스테이지 실행 중지**를 선택할 경우 해당 브랜치에 대한 실행이 중지되며 실행 중인 스테이지를 취소할 경우 선택한 파이프라인 실행 전체가 취소됩니다.
