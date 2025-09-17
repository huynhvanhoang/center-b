#  Start Camera

Performer를 실행하면 지정한 타겟(플레이어)을 대상으로 연출 카메라를 실행합니다.


## Parameter

| **이름**      | **설명**                             |
|-------------|------------------------------------|
| Target      | All : 모든 플레이어를 대상으로 연출 카메라를 실행합니다. |
|             | Target : 특정 타겟을 대상으로 연출 카메라를 실행합니다. |
| Game Object | 사용할 연출 카메라를 연결합니다.                |


## Tip

1. 카메라가 Scene Hierarchy에 배치되어 있을 경우, 설정 방식
    - Variable > Game Object를 생성합니다.
    - Game Object는 None으로 설정합니다.
    - Is user Control Data를 체크합니다.
    - Scene에서 사용할 카메라를 연결합니다.


## 참고

- [연출 카메라 장치](Contents-Camera.md)
- [Variable 사용 방식](Variable.md)