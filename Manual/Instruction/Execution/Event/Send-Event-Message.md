# Send Event Message

Performer를 실행하면 작성한 이벤트 메시지를 생성합니다.


## Parameter

| 제목      | 내용                |
|---------|-------------------|
| Message | 사용할 메시지를 입력합니다.   |
| Params  | 메시지에 파라미터를 첨부합니다. |


## Tip

1. Send event Message는 장치간 이벤트를 연결하기 위해 사용하는 기능입니다.
2. 장치의 Performer가 실행된 직후에 이벤트를 생성합니다.
3. 이때, 생성된 이벤트 메시지를 다른 장치에서 트리거 이벤트로 사용할 수 있습니다.
4. 다른 장치에서 사용하고 싶을 경우에는 "On Receive Event Trigger"가 설정되어 있어야 하며, Scene에서 장치와 장치를 연결해야 합니다.
5. 사용 예시
    - 폭발 Effect 생성 시 이벤트를 발송하고자 할 경우
      - 폭발이 생성되는 Performer 하위에 Send Event Message를 작성합니다.
      - 이벤트를 받을 장치의 트리거를 "On Receive Event Trigger"로 설정합니다.
      - Scene에서 장치와 장치를 연결하고, 받고자 하는 이벤트를 연결합니다.


## 참고

- [비주얼 스크립팅](Visual-Scripting.md)
- [장치 간 이벤트 연결하기](Connect-Event-Between-Devices.md)
- [On Receive Event Trigger](Receive-Event-Trigger.md)