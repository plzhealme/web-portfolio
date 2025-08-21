# ShotGrid 기반 스튜디오 파이프라인 시스템 구축

### Summary
- 보편적 영상 프로덕션 (Animation & VFX Film)에서 진행되는 프로젝트를 효율적으로 매니징합니다.
- 각 Department에서 나오는 data들의 유효성 검사와 Publish 절차를 자동화하여 부서 간 작업이 유기적으로 진행되도록 돕습니다.
- web-hook, action-menu-item 등을 이용해 management와 artist의 반복작업을 효율적으로 개선합니다.

---

## 1. Experiences

기본으로 배포되는 Shotgrid에서 각 스튜디오에서 요구사항에 맞춰 커스텀된 솔루션을 제공합니다.

- **파이프라인 아키텍처 설계**: 프로젝트 초기 단계에서부터 최종 결과물까지의 데이터 모델을 정의하고, ShotGrid 스키마를 최적화하여 워크플로우의 기반을 다졌습니다. 각 부서의 요구사항을 반영하여 커스텀 엔티티(Entity)와 필드(Field)를 설계하고, 전체 프로덕션의 데이터 표준화를 주도했습니다.

- **프로세스 자동화의 핵심, 이벤트 시스템 활용**: Action Menu Item과 Webhook을 유기적으로 결합하여 프로덕션의 병목 현상을 제거하는 자동화 시스템을 구축했습니다. 
    - **ex 1.** 특정 task의 status가 변경 될 때 연결 된 task의 artist들에게 자동 이메일
    - **ex 2.** web에서 선택 된 아이템들을 외주사에 전달하기 위해 정해진 포맷으로 데이터 패키징    

- **ShotGrid Toolkit(Sgtk) 커스터마이징**: Maya, Nuke, Houdini 등 각 DCC 환경에 최적화된 툴 개발을 위해 Toolkit의 핵심 설정과 앱을 깊이 있게 커스터마이징했습니다. 아티스트가 파이프라인의 존재를 잊고 작업에만 몰입할 수 있는 직관적인 UI/UX의 런처, 퍼블리셔, 로더를 개발하여 데이터 정합성을 확보하고 작업 효율을 극대화했습니다.

## 2. Tools

구현 했던 툴들의 간단한 예시입니다.
프로젝트의 보안상 민감한 이미지는 가렸습니다.

### 2-1. Version Packaging Manager

수퍼바이저 혹은 디렉터가 컨펌한 버전을 패키징해서 벤더사에 정해진 데이터셋으로 보내야 하는 프로세스가 있었습니다.

- web-browser에서 선택한 아이템들을 기준으로 데이터를 패키징합니다.
- 편집실에서 사용하는 툴에 맞춰 mov를 mxf, subtitle version 등 다양한 포맷과 여러 convert 공정을 거친 파일을 생성해 정해진 디렉토리에 저장합니다.

![툴 스크린샷 - 예시](assets/explain-ami-exam-a.png)
*▲ 툴의 프로세스를 간략하게 이미지로 설명했습니다.*

### 2-2. Custom Notification & Emailing Automation

Shotgrid에서 기본적으로 제공하는 notification은 조건이나 이메일의 포맷을 커스텀하기가 어려워서 web-hook과 Fast-api등을 활용해 notification을 자동화하였습니다.

![툴 스크린샷 - 예시](assets/shotgrid-notification.png)
*▲ 툴의 프로세스를 간략하게 이미지로 설명했습니다.*

- Web-hook에서 감지하는 이벤트의 조건은 상세하게 설정 가능합니다.    
- Data Query & Processing도 다양한 처리가 가능합니다.
- Notification의 형태도 email, slack, google chat등 다양한 형태로 가능합니다.