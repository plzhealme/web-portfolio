
## 1. Rig Asset Manager

- rig asset들을 자유롭게 검색하고 버전 별로 불러올 수 있습니다.
- 이미 작업된 rig asset도 자유롭게 버전을 변경 할 수 있습니다.
- 같은 에셋을 중복해서 불러올 수 있습니다.
- 사용중인 리그 버전이 최신버전인지 구 버전인지도 ui로 visualize됩니다.

![툴 스크린샷 - 예시](assets/pipeline-tool-dev/haribo-rig-asset-manager.png)
*▲ 실행시 UI 예시. (프로젝트 보안상 중요한 부분은 가렸습니다.)*


---

## 2. Make Burn-in mov with FFMPEG

- artist가 dcc 툴 등에서 작업한 영상 작업물에 날짜, 컷넘버, 작업자, 설명등을 기록 할 수 있는 번인 플레이트를 생성합니다.
- Nuke 혹은 ffmpeg등의 툴로 스튜디오에서 요구하는 포맷의 번인 플레이트를 생성합니다.
- 여러 카메라에서 나온 아웃풋을 하나의 mov에 합성도 가능합니다.

![툴 스크린샷 - 예시](assets/pipeline-tool-dev/burn-in-pb-test.gif)
*▲ 일반적인 사용 예시.*
![툴 스크린샷 - 예시](assets/pipeline-tool-dev/burn-in-multi-pb-test.gif)
*▲ 여러 각도의 카메라를 동시에 넣는 예시.*

---

## 3. Custom Collision Deformer with GUI

- Collision Deformer 외부 플러그인을 간단한 GUI에 셋업해서 연동하였습니다.
- [ny_collisionDeformer](https://github.com/nazmiprinter/ny_collisionDeformer) (openSource plug-in)
![툴 스크린샷 - 예시](assets/pipeline-tool-dev/collider-tool.gif)