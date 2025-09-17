# Knockback

Performer를 실행하면 지정한 오브젝트에 뒤로 밀쳐내는 효과를 적용합니다.


## Parameter

| **이름**      | **설명**                                                                    |
|-------------|---------------------------------------------------------------------------|
| Game Object | 넉백 대상을 설정합니다                                                              |
| Direction   | 힘이 적용되는 방향을 설정합니다                                                         |
| Force       | 적용되는 힘의 양을 설정합니다                                                          |
|             | - Foward Direction : 오브젝트가 현재 바라보고 있는 앞쪽 방향으로 힘을 부여합니다.                   |
|             | - From To Direction : 출발점에서 목적지로의 방향으로 힘을 부여합니다. From과 To 지점을 입력할 수 있습니다. |
|             | - Vector3 Direction : 지정된 X,Y,Z 값으로 밀어냅니다                                 |
| Force Mode  | 적용되는 힘의 유형을 설정합니다                                                         |
|             | - Force : 일반적인 힘을 적용합니다. Rigidbody의 값에 따라 가속도가 달라집니다.                     |
|             | - Acceleration : 입력한 값을 가속도에 직접 적용합니다.                                    |
|             | - Impulse : 짧은 시간 동안 빠르게 힘을 줘서 대상을 밀거나 튕깁니다.                             |
|             | - Velocity Change : Rigidbody 값과 관계없이 물체의 속도를 즉시 변화시킵니다.                  |


## Tip


## 참고

- [기믹 장치](Gimmick-toc.md)
- [기믹 장치 사용 방식](Gimmick.md)