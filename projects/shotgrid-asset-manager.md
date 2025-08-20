# 샷건(ShotGrid) 기반 에셋 관리 시스템 고도화

### TL;DR
- **문제**: 기존 에셋 퍼블리시 시스템의 잦은 오류와 느린 속도.
- **해결**: 데이터 유효성 검증 자동화, 비동기 처리 도입으로 안정성 및 속도 개선.
- **결과**: 데이터 오류율 90% 감소, 아티스트 평균 대기 시간 30% 단축.

---

## 1. 프로젝트 배경 및 문제 정의

기존에 사용하던 사내 에셋 관리 툴은 Maya에서 ShotGrid(구 Shotgun)로 데이터를 퍼블리시할 때 여러 문제점을 안고 있었습니다.

- **잦은 데이터 누락**: 네이밍 규칙, 필수 메타데이터 등을 수동으로 확인해야 해서 휴먼 에러 발생률이 높았습니다.
- **느린 처리 속도**: 대용량 파일을 퍼블리시할 때 Maya UI가 그대로 멈춰버려(Blocking) 아티스트의 작업 흐름을 방해했습니다.
- **복잡한 사용법**: 직관적이지 않은 UI로 인해 신규 입사자 교육에 많은 시간이 소요되었습니다.

> 이러한 문제들은 아티스트의 소중한 작업 시간을 낭비시키고, 파이프라인 전체의 데이터 무결성을 해치는 주요 원인이었습니다.

## 2. 나의 해결책 및 구현 과정

이 문제를 해결하기 위해 크게 세 가지 목표를 설정하고 툴을 재설계 및 개발했습니다.

### 2-1. Pre-Publish Validator (사전 유효성 검사기)

퍼블리시 실행 전, 현재 씬의 모든 데이터를 자동으로 검사하는 Validator를 구현했습니다.

- 네이밍 규칙, 경로, 텍스처 해상도, 폴리곤 수 등 프로젝트 규칙에 맞는 커스텀 검사 항목 추가
- 문제가 발견되면 어떤 에셋에 어떤 문제가 있는지 명확한 리포트 제공

![툴 스크린샷 - Validator UI](../assets/validator_ui.png)
*▲ Validator가 에러를 감지하고 사용자에게 리포트하는 UI 화면*

### 2-2. 비동기(Asynchronous) 퍼블리시 도입

`threading` 모듈을 사용하여 무거운 퍼블리시 작업을 별도의 스레드에서 처리하도록 구현했습니다.

```python
# 예시 코드
import threading
from PySide2 import QtCore

class Publisher(QtCore.QObject):
    finished = QtCore.Signal()

    def publish_logic(self, data):
        # ... (시간이 오래 걸리는 실제 퍼블리시 코드) ...
        print("Publishing finished!")
        self.finished.emit()

    def run_in_thread(self, data):
        thread = threading.Thread(target=self.publish_logic, args=(data,))
        thread.start()