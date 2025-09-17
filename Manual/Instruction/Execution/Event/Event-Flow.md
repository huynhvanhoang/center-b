# Flow

Performer를 실행하면 작성한 플로우 장치에 Script에 설정한 기능을 요청합니다.


## Flow Type

Performer로 제공하는 Flow 타입은 3가지로 분류됩니다

| **이름**   | **설명**                                   |
|----------|------------------------------------------|
| End Flow | 플로우 장치에 입력한 플로우의 종료를 요청합니다.              |
| End Game | 플로우 장치에 현재 진행 중인 스테이지 종료를 요청합니다.         |
| End Room | 플로우 장치에 이후 라운드 여부 관계 없이 즉시 게임 종료를 요청합니다. |


## Parameter

| **Performer 이름** | **파라미터 이름** | **설명**                 |
|------------------|-------------|------------------------|
| End Flow         | Message     | 종료할 플로우 장치의 이름을 설정합니다. |


## Tip

1. End flow에 입력한 String이 현재 진행 중인 플로우 이름과 같지 않다면, 인스트럭션은 작동하지 않습니다.


## 참고

- [비주얼 스크립팅](Visual-Scripting.md)
- [장치 간 이벤트 연결하기](Connect-Event-Between-Devices.md)
- [플로우 장치](System-Flow.md)
- [게임 종료 장치](Contents-Game-End-Device.md)