# Collect Colliders In Range

Performer를 실행하면 Collider 범위를 설정합니다.  
아이템을 사용할 피격 범위를 설정하는 용도로 사용합니다.


## Parameter

| **이름**         | **설명**                                                           |
|----------------|------------------------------------------------------------------|
| Range Type     | Collider Type을 설정합니다                                             |
|                | - Box : Box Collider 타입을 설정합니다                                   |
|                | - Sphere : Sphere Collider 타입을 설정합니다                             |
| Center         | Collider를 지정할 대상을 설정합니다                                          |
| Size or Radius | Collider 범위를 설정합니다. (Range Type에 따라 해당 항목이 달라집니다)                |
| - Size         | - Center : Box Collider Type에서 사용되며, Collider의 대상 혹은 범위를 설정합니다.  |
| - Radius       | Collider 범위를 설정합니다. (Range Type에 따라 해당 항목이 달라집니다)                |
| Rotation       | Box Colldier일 경우에만 사용되며, Collider의 회전 값을 설정합니다.                  |
| Variable List  | 반경에 들어온 대상의 처리 결과를 저장하는 곳을 지정합니다. List Variable과 연동하여 사용할 수 있습니다 |


## Tip

1. 아이템 사용 시 피격 범위를 설정할 경우에 사용해야 합니다.
2. 피격 범위에 들어온 대상에 대한 값을 저장하고 가져오기 위해서는 List Variable 기능을 이용하여 피격된 대상에 대한 상호 작용을 처리할 수 있습니다.


# 참고

- [비주얼 스크립팅](Visual-Scripting.md) 
- [장착 아이템 장치](EquipItem-Device.md)