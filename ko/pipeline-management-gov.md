## Dev Tools > Pipeline > 콘솔 사용 가이드 > 파이프라인 관리

파이프라인은 한 개 이상의 스테이지로 구성된 애플리케이션 배포 흐름을 정의합니다.

### 파이프라인 구성

#### 파이프라인 생성

**+ 파이프라인 생성**을 클릭하여 파이프라인을 생성할 수 있으며, 파이프라인 템플릿 파일을 업로드하여 파이프라인을 생성할 수도 있습니다.
![pipeline-management-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-01.png)

**파이프라인 관리**에서 **+ 파이프라인 생성**을 클릭합니다.

![pipeline-management-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-02.png)

**파이프라인 생성** 모달 창에서 **파이프라인 이름**과 **파이프라인 설명**을 입력한 뒤 **확인**을 클릭합니다.

또는 파이프라인 템플릿 파일로 파이프라인을 생성할 수도 있습니다(파이프라인 템플릿은 JSON 파일을 사용합니다).

![pipeline-management-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-03.png)

파이프라인 템플릿 파일을 업로드한 뒤 **확인**을 클릭합니다.

#### 파이프라인 스튜디오

파이프라인 스튜디오는 사용자가 파이프라인의 기본 정보를 관리하거나 파이프라인을 구성하는 스테이지를 추가, 변경, 삭제할 수 있는 페이지입니다.

![pipeline-studio-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-1.png)

파이프라인 스튜디오 상단에는 파이프라인의 이름, 설명, 마지막 수정일, 생성자의 기본 정보가 표시됩니다.

파이프라인 스튜디오 패널에서는 해당 파이프라인을 구성하는 스테이지들을 확인할 수 있습니다.

#### 편집 모드
![pipeline-studio-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-2.png)

우측 상단의 **편집 모드** 토글을 클릭하여 편집 모드로 진입할 수 있습니다. 편집 모드에서는 스테이지 추가, 변경, 삭제 및 위치 변경을 수행할 수 있습니다.

#### 스테이지 추가
![pipeline-studio-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-3.png)

**편집 모드**를 활성화하면 좌측에 애플리케이션 배포 흐름을 구성할 때 사용할 수 있는 다양한 스테이지로 구성된 **소스**, **빌드**, **배포**, **기능** 그룹이 노출됩니다.

4개의 그룹에서 추가할 스테이지를 선택하여 드래그 앤 드롭으로 화면에 가져다 놓을 수 있습니다.

![pipeline-studio-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-4.png)

스테이지가 추가되면 해당 스테이지를 선택하여 필수 정보를 입력합니다.

![pipeline-studio-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-5.png)

이전에 실행할 스테이지와 추가할 스테이지를 연결하여 실행 순서를 설정합니다.

![pipeline-studio-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-6.png)

우측 상단의 **파이프라인 저장**을 클릭해 스테이지 추가를 완료할 수 있습니다.

#### 스테이지 편집
![pipeline-studio-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-7.png)

**편집 모드**를 활성화한 뒤 편집할 스테이지를 클릭해 스테이지를 편집할 수 있습니다.

![pipeline-studio-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-9.png)

편집을 완료한 뒤 우측 상단의 **파이프라인 저장**을 클릭해 스테이지 편집을 완료할 수 있습니다.

#### 스테이지 삭제
![pipeline-studio-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-10.png)

![pipeline-studio-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-11.png)

**편집 모드**를 활성화한 뒤 삭제할 스테이지의 우측 상단 **X**를 클릭해 스테이지를 삭제할 수 있습니다.

![pipeline-studio-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-12.png)

삭제 후 우측 상단의 **파이프라인 저장**을 클릭해 스테이지 삭제를 완료할 수 있습니다.

### 파이프라인 실행

파이프라인은 수동 또는 자동으로 실행할 수 있습니다.

#### 수동 실행

수동 실행을 사용하면 사용자가 원할 때 파이프라인을 실행할 수 있습니다.

![pipeline-management-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-12.png)

**파이프라인 관리**에서 **▶︎ 실행**을 클릭한 뒤 **파이프라인 실행** 모달 창이 나타나면 내용을 확인하고 **확인**을 클릭합니다.

#### 자동 실행

자동 실행을 사용하면 GitHub 또는 GitLab 저장소에 이벤트가 발생하거나 이미지 저장소의 컨테이너 이미지를 갱신하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다.

![management-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-04.png)
![management-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-05.png)

**자동 실행 설정**을 클릭한 뒤 **자동 실행 설정** 모달 창에서 **추가**를 클릭합니다.


* GitHub 자동 실행 설정
![management-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-06.png)



GitHub 웹훅을 사용해서 GitHub 또는 GitHub Enterprise의 저장소에 이벤트가 발생하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다. **자동 실행 유형**을 **GitHub**으로 설정하고 저장소의 **조직명 혹은 사용자 이름**, **프로젝트 이름**, **브랜치 또는 태그**, **시크릿**을 입력하고 **확인**을 클릭합니다.

태그로 자동 실행을 설정하려면 **브랜치 또는 태그** 항목에 `refs/tags/태그명`과 같이 태그명을 입력합니다. `태그명` 부분에는 JAVA 정규 표현식을 사용할 수 있습니다.

태그로 자동 실행 설정 후 NHN Cloud 빌드 도구 사용 시 설정된 태그로 빌드를 수행합니다. 빌드 - Jenkins 스테이지에서 태그로 빌드를 수행하려면 다음과 같이 설정해야 합니다.

Jenkins에서 다음과 같이 파라미터를 설정합니다.
![pipeline-guide-39.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-39.png)
![pipeline-guide-40.png](http://static.toastoven.net/prod_pipeline/2023-09-26/pipeline-guide-40.png)


Pipeline의 빌드 도구 설정에서 **빌드 잡 파라미터**에 다음과 같이 입력합니다.

![management-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-10.png)

* GitHub 웹훅 설정값

![pipeline-guide-16](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-16.png)


| 항목 | 설정값 |
|---|---|
| Payload URL | https://kr1-pipeline.api.gov-nhncloudservice.com/webhooks/git/github |
| Content type | application/json |
| Secret | 파이프라인 자동 실행 설정의 시크릿에 입력한 값 |
| event | push event, create event(태그 사용 시) |

특정 파일이 Push되었을 때만 자동 실행되도록 설정할 수 있습니다(최대 5개).

![management-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-13.png)

**소스 저장소 이름**은 환경 설정에서 등록한 소스 저장소를 선택합니다.
**GitHub 파일 경로**는 선택한 소스 저장소에서 파일이 포함된 경로를 입력합니다.

* GitLab 자동 실행 설정

![management-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-07.png)

GitLab 웹훅을 사용해서 GitLab 저장소에 이벤트가 발생하면 파이프라인을 자동으로 실행하게 설정할 수 있습니다. **자동 실행 유형**을 **GitLab**으로 설정하고 저장소의 **조직명 혹은 사용자 이름**, **프로젝트 이름**, **브랜치 또는 태그**를 입력하고 **확인**을 클릭합니다. GitLab 시크릿 설정은 추후 지원할 예정입니다.

* GitLab 웹훅 설정값

![pipeline-guide-18](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-18.png)


| 항목 | 설정값 |
|---|---|
| URL | https://kr1-pipeline.api.gov-nhncloudservice.com/webhooks/git/gitlab |
| Trigger | Push events 체크 |
| Secret | 설정하지 않음 |
| SSL verification | Enable SSL verification 체크 |

* GitLab 웹훅 설정 시 주의 사항

GitLab의 사용자 이름으로 자동 실행을 설정할 때 사용자 이름을 GitLab의 사용자 이름과 동일하게 설정해야 합니다. 사용자 이름을 다르게 설정할 경우 자동 실행이 동작하지 않을 수 있습니다.

![pipeline-guide-19](http://static.toastoven.net/prod_pipeline/2023-03-28/pipeline-guide-19.png)

* 이미지 저장소 자동 실행 설정

![management-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-08.png)

컨테이너 이미지를 갱신했을 때 파이프라인을 자동으로 실행하려면 **자동 실행 유형**을 **이미지 저장소**로 설정합니다.
**이미지 저장소**를 **환경 설정**에서 등록한 항목으로 선택한 뒤 **이미지 이름**을 입력합니다. 이미지 이름은 NHN Cloud Container Registry의 경우 `registry명/이미지 이름`의 형태로 입력합니다.
Docker Hub의 경우 `Docker Hub 계정/이미지 이름` 형식으로 입력합니다. **태그**는 JAVA 정규 표현식을 사용할 수 있으며 입력한 태그와 매칭되는 태그가 push되었을 경우 자동 실행됩니다.
태그를 입력하지 않으면 latest를 제외한 신규 태그가 push될 경우 자동 실행됩니다.
입력을 마친 후 **확인**을 클릭합니다.

![management-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-management-guide/management-guide-09.png)

파이프라인을 새로 만들면 **자동 실행**의 토글 스위치가 꺼진 상태로 적용됩니다. 파이프라인을 자동으로 실행하려면 **자동 실행** 토글 스위치를 클릭해 활성화해야 합니다. 

### 파이프라인 관리

사용자는 파이프라인의 기본 정보를 수정할 수 있습니다.
![pipeline-studio-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-13.png)

파이프라인 이름 옆의 수정 아이콘을 클릭하여 파이프라인의 이름과 설명을 수정할 수 있습니다.

정보를 수정한 뒤 **확인**을 클릭해 수정을 완료할 수 있습니다.

![pipeline-studio-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-14.png)

**▶ 수동 실행**을 클릭해 해당 파이프라인을 실행할 수 있으며, **■ 실행 중지**를 클릭해 실행 중인 파이프라인을 중지할 수 있습니다.


#### 최근 실행 정보 확인

파이프라인의 최근 실행에 대한 각 스테이지별 기본 정보와 실행 상태를 확인하려면 **최근 실행 정보**를 클릭합니다.

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/guide-16.png)

#### 파이프라인 JSON 다운로드

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-03-25/guide-17.png)

**파이프라인 버전**을 클릭하여 JSON 형식으로 파이프라인을 확인할 수 있습니다.

좌측 상단의 파이프라인 수정일이 표시된 드롭다운 버튼을 클릭해 수정일별로 확인할 수 있습니다.

우측 상단 **파이프라인 템플릿 다운로드**를 클릭해 JSON 파일로 저장할 수 있습니다.

#### 파이프라인 알림
파이프라인 시작, 완료, 실패에 대한 Email, SMS 알림을 관리하는 기능입니다.

![pipeline-management-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-03-25/pipeline-management-guide-13.png)

**파이프라인 알림**을 클릭하여 알림을 설정할 수 있습니다.

**프로젝트 설정** > **알림 관리**에서 알림 수신자 관리가 가능합니다.

알림 수신 대상 및 알림 방법(Email, SMS)에 대한 설정은 [알림 관리 가이드](https://docs.gov-nhncloud.com/ko/nhncloud/ko/console-guide-gov/#_34)를 참고하세요.

#### 파이프라인 실행 이력
파이프라인 스튜디오에서 **실행 이력**을 클릭하면 최근 10개의 이력을 확인할 수 있습니다.
![pipeline-management-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-04-15/pipeline-management-guide-14.png)

![pipeline-management-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2025-04-15/pipeline-management-guide-15.png)

실행 이력 모달 창의 좌측 영역에서 확인할 실행 이력을 선택하면 우측 영역에 각 스테이지의 상세 정보가 표시됩니다.

**상태** 열에서 파이프라인의 실행 상태를 확인할 수 있으며, **취소**를 클릭해 파이프라인 실행을 취소할 수 있습니다.

**기능 - 승인 관리**, **기능 - Judgement(실행 관리)** 등의 스테이지는 **관리**를 클릭하여 파이프라인의 실행 관리를 할 수 있습니다.