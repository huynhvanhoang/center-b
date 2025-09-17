#  Stop Camera

Performer를 실행하면 현재 진행 중인 연출 카메라를 종료하고 비활성 상태로 전환합니다.


## Parameter

| **이름**      | **설명**                                  |
|-------------|-----------------------------------------|
| Target      | All : 모든 플레이어를 대상으로 실행된 연출 카메라를 종료합니다.  |
|             | Target : 특정 타겟을 대상으로 실행된 연출 카메라를 종료합니다. |
| Game Object | 종료할 연출 카메라를 연결합니다.                      |


## Tip

1. 카메라가 Scene Hierarchy에 배치되어 있을 경우, 설정 방식
   - Variable > Game Object를 생성합니다.
   - Game Object는 None으로 설정합니다.
   - Is user Control Data를 체크합니다.
   - Scene에서 종료할 카메라를 연결합니다.
2. 연출 카메라가 Fixed 일 경우 주의 할 점.
   - Fixed로 설정된 연출 카메라는 "Stop camera"가 적용되어 있지 않을 경우, 카메라를 전환하지 않습니다.
   - 연출 카메라를 전환하거나, 인게임 카메라로 변경할 경우 "Stop Camera"를 Script에 추가해야 합니다.


## 참고

- [연출 카메라 장치](Contents-Camera.md)
- [Variable 사용 방식](Variable.md)