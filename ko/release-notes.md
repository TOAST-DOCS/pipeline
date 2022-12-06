## Dev Tools > Pipeline > 릴리스 노트

### 2022. 12. 27.
#### 버그 수정
* [Console] Pipeline 생성시 소스설정 단계에서 소스저장소를 선택해야 이전 단계로 갈 수 있는 현상 수정

### 2022. 10. 25.
* 배포 대상 Kubernetes 연결 테스트 시간 초과 시에도 안내 메시지를 노출하도록 수정하였습니다.

### 2022. 08. 23.
* 스테이지가 없는 Pipeline을 [API](https://docs.toast.com/ko/Dev%20Tools/Pipeline/ko/api-guide/#pipeline)로 실행 시 실패 응답을 주도록 수정하였습니다.

### 2022. 07. 26.
* 기능 - Webhook 스테이지가 추가되었습니다.
* API 엔드포인트의 도메인이 api-pipeline.cloud.toast.com에서 kr1-pipeline.api.nhncloudservice.com로 변경되었습니다.

### 2022. 05. 24.
* 소스 저장소, 이미지 저장소, 빌드 도구, 배포 대상에 연결 확인 기능이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/console-guide)에서 사용 방법을 확인할 수 있습니다. 
* CloudTrail에 세부 내용이 추가되었습니다.
    * 설정 삭제 시 세부 내용 추가
    * 파이프라인 실행 관련 세부 내용 추가

### 2022. 02. 22.
* 소스 저장소에 GitLab이 추가되었습니다. [Pipeline 사용자 가이드](/Dev%20Tools/Pipeline/ko/console-guide/#_1)에서 사용 방법을 확인할 수 있습니다.

### 2022. 01. 25.
* Pipeline 실행 API가 추가되었습니다. [Pipeline API 가이드](/Dev%20Tools/Pipeline/ko/api-guide/#pipeline)에서 사용 방법을 확인할 수 있습니다.
* 발견된 이슈(원인 분석 후 개선 예정입니다.)
    * 개발 환경 생성 시 개발 환경 제약 사항에 값을 지정하면 생성에 실패하는 현상이 있습니다.

### 2021. 05. 25.
* CloudTrail과 연동합니다. Pipeline에서 발생한 이벤트를 CloudTrail에서 확인할 수 있습니다.

### 2021. 04. 27.

#### 신규 서비스 출시
* 소스 코드 빌드, 컨테이너 이미지 생성, 컨테이너 이미지 배포 등 애플리케이션 배포 흐름을 관리할 수 있는 지속적 배포(continuous deployment) 서비스입니다.
