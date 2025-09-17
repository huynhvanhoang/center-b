# 스타트라인 장치

**이름:** GD_RunStart

![](media/images/RunStart-Device.png){width="400"}

스타트라인 장치는 펭귄 진격에서 게임을 시작하는 위치로 사용할 수 있는 장치입니다.  
이벤트를 받으면 게임을 시작할 수 있도록 설정된 시간에 문을 여는 기능을 가지고 있습니다. 


## 옵션

![RunStart-Device-inspector.png](media/images/RunStart-Device-inspector.png) {width="400"}

| **이름**  | **내용**               |
|-----------------|----------------------|
| ![](../../../media/image/guidenum_01.png) Move Speed | 문이 열리는 속도를 설정합니다.    |
| ![](../../../media/image/guidenum_02.png) Position   | 문이 내려가는 위치 값을 설정합니다. |


## 기능

Receive Event Door Open : 이벤트를 받으면 장치에 구성된 문이 열립니다.


## 이벤트

On Door Open: 문이 열리면 연결된 장치는 트리거를 실행합니다


## 참고

- [비주얼 스크립팅](Visual-Scripting.md)
- [장치간 이벤트 연결하기](Connect-Event-Between-Devices.md)
- [Instruction](Instruction.md)
