## Dev Tools > Pipeline > 콘솔 사용 가이드 > 파이프라인 스튜디오

### 파이프라인 스튜디오

파이프라인 스튜디오는 사용자가 파이프라인의 기본 정보를 관리하거나 파이프라인을 구성하는 스테이지를 추가, 변경, 삭제할 수 있는 페이지입니다.

#### 파이프라인 관리
![pipeline-studio-guide-01](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-01.png)

파이프라인 스튜디오 상단에는 파이프라인의 이름, 설명, 마지막 수정일, 생성자의 기본 정보가 표시됩니다.

파이프라인 스튜디오 패널에서는 해당 파이프라인을 구성하는 스테이지들을 확인할 수 있습니다.

![pipeline-studio-guide-02](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-02.png)

파이프라인 이름 옆의 수정 아이콘을 클릭하여 파이프라인의 이름과 설명을 수정할 수 있습니다.

정보를 수정한 뒤 **확인**을 클릭해 수정을 완료할 수 있습니다.

![pipeline-studio-guide-03](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-03.png)

**▶ 수동 실행**을 클릭해 해당 파이프라인을 실행할 수 있으며, **■ 실행 중지**를 클릭해 실행 중인 파이프라인을 중지할 수 있습니다.

![pipeline-studio-guide-04](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-04.png)

파이프라인의 최근 실행에 대한 각 스테이지별 기본 정보와 실행 상태를 확인하려면 **최근 실행 정보**를 클릭합니다. 

![pipeline-studio-guide-05](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-05.png)

**파이프라인 버전**을 클릭하여 JSON 형식으로 파이프라인을 확인할 수 있습니다.

좌측 상단의 파이프라인 수정일이 표시된 드롭다운 버튼을 클릭해 수정일별로 확인할 수 있습니다.

우측 상단 **파이프라인 템플릿 다운로드**를 클릭해 JSON 파일로 저장할 수 있습니다.

**편집**을 클릭해 화면에서 JSON 파일을 직접 수정할 수 있습니다.

![pipeline-studio-guide-06](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-06.png)

**파이프라인 삭제**를 클릭해 해당 파이프라인을 삭제할 수 있습니다.

### 스테이지 확인
![pipeline-studio-guide-07](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-07.png)

스테이지를 클릭해 화면 우측의 **스테이지 설정** 패널에서 스테이지 정보를 확인할 수 있습니다.

![pipeline-studio-guide-18](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-18.png)

좌측 하단 버튼을 클릭해 파이프라인을 구성하는 스테이지들의 화면을 조정할 수 있습니다. 버튼에 대한 설명은 위에서부터 차례대로 다음과 같습니다.

- 자동 정렬
- 확대
- 축소
- 자동 배율 조절
- 잠금

### 편집 모드
![pipeline-studio-guide-08](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-08.png)

우측 상단의 편집 모드 토글을 클릭하여 편집 모드로 진입할 수 있습니다. 편집 모드에서는 스테이지 추가, 변경, 삭제 및 위치 변경을 수행할 수 있습니다.

### 스테이지 추가
![pipeline-studio-guide-09](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-09.png)

**편집 모드**를 활성화하면 좌측에 애플리케이션 배포 흐름을 구성할 때 사용할 수 있는 다양한 스테이지로 구성된 **소스**, **빌드**, **배포**, **기능** 그룹이 노출됩니다.

4개의 그룹에서 추가할 스테이지를 선택하여 드래그 앤 드롭으로 화면에 가져다 놓을 수 있습니다.

![pipeline-studio-guide-10](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-10.png)

스테이지가 추가되면 해당 스테이지를 선택하여 필수 정보를 입력합니다.

![pipeline-studio-guide-11](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-11.png)

이전에 실행할 스테이지와 추가할 스테이지를 연결하여 실행 순서를 설정합니다.

스테이지를 연결하는 방식에 따라 스테이지를 병렬로 실행할 수 있습니다. 병렬 구성한 스테이지 중 하나가 실패하면 나머지 스테이지는 실행이 취소되고 파이프라인 실행은 실패합니다.

![pipeline-studio-guide-12](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-12.png)

우측 상단의 **파이프라인 저장**을 클릭해 스테이지 추가를 완료할 수 있습니다.

### 스테이지 편집
![pipeline-studio-guide-13](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-13.png)

**편집 모드**를 활성화한 뒤 편집할 스테이지를 클릭해 스테이지를 편집할 수 있습니다.

![pipeline-studio-guide-14](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-14.png)

편집을 완료한 뒤 우측 상단의 **파이프라인 저장**을 클릭해 스테이지 편집을 완료할 수 있습니다.

### 스테이지 삭제
![pipeline-studio-guide-15](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-15.png)

![pipeline-studio-guide-16](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-16.png)

**편집 모드**를 활성화한 뒤 삭제할 스테이지의 우측 상단 **X**를 클릭해 스테이지를 삭제할 수 있습니다.

![pipeline-studio-guide-17](https://kr1-api-object-storage.nhncloudservice.com/v1/AUTH_2acdfabf4efe4efc8a04c00b348110c9/cdn_origin/prod_pipeline/2024-08-27/pipeline-studio-guide/pipeline-studio-guide-17.png)

삭제 후 우측 상단의 **파이프라인 저장**을 클릭해 스테이지 삭제를 완료할 수 있습니다.
