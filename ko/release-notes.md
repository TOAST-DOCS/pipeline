## Dev Tools > Pipeline > 릴리스 노트

### 2023. 10. 31.
* 승인 없이 이후 스테이지를 실행하지 못하도록 관리하는 **기능 - 승인 관리** 스테이지가 추가되었습니다. [Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#-)에서 자세한 설명을 확인할 수 있습니다.
* 파이프라인 템플릿 가이드 내 샘플 시나리오가 추가되었습니다. [Pipeline 템플릿 가이드](/Dev%20Tools/Pipeline/ko/template-guide/#_2)에서 사용 방법 및 템플릿 파일을 다운로드할 수 있습니다.

### 2023. 09. 26.
* 파이프라인 템플릿 기능이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/template-guide/#_1)에서 사용 방법을 확인할 수 있습니다.
    * 파이프라인 생성 시 템플릿 파일(JSON 형식)을 업로드하여 생성할 수 있습니다.
    * **JSON 보기** > **파이프라인 템플릿 다운로드**로 파이프라인 템플릿 파일을 다운로드할 수 있습니다.
* Github 자동 실행 설정의 **브랜치 혹은 태그** 항목에서 태그를 사용할 수 있게 되었습니다. 태그로 자동 실행 시 태그를 사용하여 빌드를 수행합니다.

### 2023. 08. 29.
* 다른 파이프라인 전체를 실행할 수 있는 **기능 - 타 파이프라인 실행** 스테이지가 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#_4)에서 사용 방법을 확인할 수 있습니다.
* Pipeline 서비스에서 제공하던 개발 환경 기능은 더 이상 제공되지 않습니다. 개발 환경 기능은 AI EasyMaker 서비스의 노트북으로 이용할 수 있습니다. 자세한 내용은 [AI EasyMaker 사용자 가이드](https://docs.nhncloud.com/ko/Machine%20Learning/AI%20EasyMaker/ko/console-guide/#_2)에서 확인할 수 있습니다.
* **배포 대상 모니터링**의 명칭이 **배포 대상 관리**로 변경됩니다.
* **배포 대상 관리**에 Pipeline을 통해 클러스터에 배포된 워크로드를 관리하고 이력을 확인할 수 있는 기능이 추가되었습니다.

### 2023. 06. 27.
* 배포 - Deploy 스테이지에서 배포한 결과물을 확인할 수 있는 배포 대상 모니터링 기능이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/deploy-target-monitoring)에서 사용 방법을 확인할 수 있습니다.
    * 배포 대상 모니터링에서는 Kubernetes의 워크로드 및 서비스를 확인할 수 있습니다.
* 파이프라인 분기 처리를 할 수 있는 [기능 - Judgement(실행 관리)] 및 [기능 - Precondition(실행 조건)] 스테이지가 추가되었습니다. [Pipeline 스테이지 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#-judgement)에서 스테이지 설명을, [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/pipeline-management/#_15)에서 사용 방법을 확인할 수 있습니다.

### 2023. 03. 28.
* Helm 차트를 이용하여 배포할 결과물을 만들 수 있는 빌드 - Bake (Manifest) 스테이지가 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/stage-guide/#-bake-manifest)에서 사용 방법을 확인할 수 있습니다.
* 빌드 - Bake (Manifest) 스테이지에서 사용할 수 있는 차트 저장소 설정이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/environment-config/#_6)에서 사용 방법을 확인할 수 있습니다.
* 배포 - Deploy 스테이지에서 Manifest를 아티팩트로 선택할 수 있는 기능이 추가되었습니다.

### 2023. 02. 28.
* 외부 저장소의 리소스를 파이프라인 스테이지의 시작 또는 종료 조건으로 사용할 수 있는 아티팩트 기능이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/pipeline-management/#_1)에서 사용 방법을 확인할 수 있습니다.

### 2023. 01. 31.
* 빌드 스테이지에서 이미지 태그 포맷을 사용하여 동적으로 생성되는 태그를 부여할 수 있는 기능이 추가되었습니다.
* 배포 스테이지에서 이미지 태그 포맷을 사용하여 동적으로 생성된 태그 중 가장 최신의 태그로 배포할 수 있는 기능이 추가되었습니다.
* 이미지 자동 실행의 동작 방식이 다음과 같이 변경되었습니다.
    * 자동 실행 설정 중 태그값이 필수값에서 제외되었습니다.
    * 입력된 태그와 정규 표현식으로 매칭된 태그가 push 될 때 자동 실행되도록 변경되었습니다.  
    * 태그를 입력하지 않으면 latest를 제외한 태그로 push 될 때 자동 실행되도록 변경되었습니다.

### 2022. 12. 27.
* Pipeline 생성 시 소스 설정 단계에서 소스 저장소를 선택해야 이전 단계로 갈 수 있는 문제를 수정하였습니다.

### 2022. 10. 25.
* 배포 대상 Kubernetes 연결 테스트 시간 초과 시에도 안내 메시지를 노출하도록 수정하였습니다.

### 2022. 08. 23.
* 스테이지가 없는 Pipeline을 [API](/Dev%20Tools/Pipeline/ko/api-guide/#pipeline)로 실행 시 실패 응답을 주도록 수정하였습니다.

### 2022. 07. 26.
* 기능 - Webhook 스테이지가 추가되었습니다.
* API 엔드포인트의 도메인이 api-pipeline.cloud.toast.com에서 kr1-pipeline.api.nhncloudservice.com로 변경되었습니다.

### 2022. 05. 24.
* 소스 저장소, 이미지 저장소, 빌드 도구, 배포 대상에 연결 확인 기능이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/environment-config)에서 사용 방법을 확인할 수 있습니다. 
* CloudTrail에 세부 내용이 추가되었습니다.
    * 설정 삭제 시 세부 내용 추가
    * 파이프라인 실행 관련 세부 내용 추가

### 2022. 02. 22.
* 소스 저장소에 GitLab이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/environment-config/#_2)에서 사용 방법을 확인할 수 있습니다.

### 2022. 01. 25.
* Pipeline 실행 API가 추가되었습니다. [Pipeline API 가이드](/Dev%20Tools/Pipeline/ko/api-guide/#pipeline)에서 사용 방법을 확인할 수 있습니다.
* 발견된 이슈(원인 분석 후 개선 예정입니다.)
    * 개발 환경 생성 시 개발 환경 제약 사항에 값을 지정하면 생성에 실패하는 현상이 있습니다.

### 2021. 05. 25.
* CloudTrail과 연동합니다. Pipeline에서 발생한 이벤트를 CloudTrail에서 확인할 수 있습니다.

### 2021. 04. 27.

#### 신규 서비스 출시
* 소스 코드 빌드, 컨테이너 이미지 생성, 컨테이너 이미지 배포 등 애플리케이션 배포 흐름을 관리할 수 있는 지속적 배포(continuous deployment) 서비스입니다.
