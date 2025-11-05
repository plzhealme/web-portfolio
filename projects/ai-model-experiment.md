> ai model을 직접 생성하는 것이 아닌 공개된 모델들을 조합해서 여러 프로세스의 자동화를 실험했습니다.

## Auto Rotoscope

- [GroundingDino (객체 검출 ai)](https://github.com/IDEA-Research/GroundingDINO)
- [Samurai (객체 추적 ai)](https://github.com/yangchris11/samurai)

> 객체를 검출하는 ai model과 객체를 추적하는 ai model을 이용해서 특정 객체 마스크를 자동으로 생성하는 스크립트입니다. \
> `GroundingDino`를 이용해서 context를 통해 객체의 범위를 먼저 특정합니다. 그 이후 해당 객체의 범위와 이미지 시퀀스를 'Samurai'를 통해 마스크를 생성하는 절차를 가집니다. 
>  

- [Auto Rotoscope](https://github.com/plzhealme/auto_rotoscope)
- 자세한 세팅이나 코드는 위 깃허브 주소에서 확인하실 수 있습니다.

![실행 예시](assets/ai-model-experiment/a_man.gif) (군중 테이크에서 인물 검출)
![실행 예시](assets/ai-model-experiment/a_red_car.gif) (트래픽 테이크에서 특정 객체 검출)

<table align="center" border="0" style="border: none; border-collapse: collapse;">
  <tr>
    <td style="padding: 0;">
      <video autoplay loop muted playsinline width="600">
        <source src="assets/ai-model-experiment/composed_car_bbox.mp4" type="video/mp4">
        <source src="assets/ai-model-experiment/composed_car_bbox.webm" type="video/webm">
        Your browser does not support the video tag.
      </video>
    </td>
    <td style="padding: 0;">
      <video autoplay loop muted playsinline width="600">
        <source src="assets/ai-model-experiment/composed_man_bbox.mp4" type="video/mp4">
        <source src="assets/ai-model-experiment/composed_man_bbox.webm" type="video/webm">
        Your browser does not support the video tag.
      </video>
    </td>
  </tr>
</table>

(위 예제의 결과물입니다.\)
