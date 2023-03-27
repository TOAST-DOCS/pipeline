## Dev Tools > Pipeline > 콘솔 사용 가이드 > 개발 환경 설정

### 개발 환경 설정

개발 환경 설정을 사용하면 Kubernetes 사용법을 모르는 사용자도 Kubernetes에 컨테이너 이미지를 배포할 수 있습니다.

![dev-env-config-guide-01](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-01.png)

**개발 환경 설정**에서 **개발 환경 생성**을 클릭합니다.

![dev-env-config-guide-02](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-02.png)

개발 환경 이름과 개발 환경 설명을 입력하고 기본 이미지에서 배포할 컨테이너 이미지를 선택합니다. 컨테이너 이미지 접근에 필요한 정보는 이미지 저장소에 설정합니다. 배포 대상은 컨테이너 이미지를 배포할 Kubernetes를 선택합니다. 서비스 포트는 컨테이너가 제공하는 서비스의 포트를 입력합니다. 서비스 포트를 입력하면 컨테이너 서비스에 접근할 수 있는 서비스 IP를 자동으로 할당합니다.(Kubernetes가 LoadBalancer 타입의 서비스를 제공할 경우) 마지막으로 개발 환경 제약 사항을 입력한 후 **생성**을 클릭하면 개발 환경을 생성합니다.

![dev-env-config-guide-03](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-03.png)

개발 환경이 생성되는 동안 **개발 환경 상태**는 **생성 중**으로 표시됩니다.

![dev-env-config-guide-04](http://static.toastoven.net/prod_pipeline/2023-03-28/dev-env-config-guide-04.png)

개발 환경 생성이 완료되면 **개발 환경 상태**가 **실행 중**으로 변경됩니다. 서비스 IP와 서비스 포트를 사용해서 컨테이너 서비스에 접근할 수 있습니다.
