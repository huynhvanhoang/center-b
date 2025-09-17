# Attach Object

Performer를 실행하면 지정된 캐릭터(플레이어) 파츠 위치에 오브젝트를 부착합니다.  
버프 혹은 장착 아이템 장치를 사용할 경우에 추가로 파츠를 붙여야 할 경우에 사용됩니다.


## Parameter

| **이름**          | **설명**                                |
|-----------------|---------------------------------------|
| Target Player   | 부착할 대상을 설정합니다.                        |
| Attach Object   | 부착할 오브젝트를 설정합니다.                      |
| Attach to       | 부착할 파츠 위치를 설정합니다.(캐릭터에 붙일 경우에 사용됩니다.) |
| Offset Position | 부착 시 위치할 포치션 값(X,Y,Z)을 설정합니다.         |
| Offset Rotation | 부착 시 회전 값을 설정합니다                      |


## Tip

1. 버프나 장착 아이템을 사용했을 때 추가로 오브젝트를 붙여야 할 경우 아래와 같이 파라미터를 설정해야 합니다.
    - Target을 Vulcanus Object Owner로 설정합니다.
    - Vuclanus Object Owner 하위 파라미터의 게임 오브젝트를 제공할 장치를 등록합니다.


## 참고
- [장착 아이템 장치](EquipItem-Device.md)
- [버프 장치](Buff-System.md)
- [Variable 사용 방식](Variable.md)
