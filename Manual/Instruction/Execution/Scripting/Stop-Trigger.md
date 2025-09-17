# Stop Trigger

Performer를 실행하면 진행 중인 Trigger까지만 작동하고, 이후 진행할 Trigger를 중지합니다.


## Parameter

| **이름**  | **설명**                  |
|---------|-------------------------|
| Trigger | 중지할 Trigger 오브젝트를 연결합니다 |



## Tip

1. Stop Trigger가 중간에 적용되어 있더라도 현재 진행 중인 Trigger는 끝까지 진행됩니다. 
2. 이후에 실행할 Trigger를 더 이상 실행하지 않습니다
3. Trigger에 따라, 해당 기능이 작동하지 않는 경우가 있습니다.
   - EX) Update Trigger의 경우 Stop Trigger를 설정하여도, 이후 이벤트를 받아 다시 작동하기 때문에 Stop Trigger의 영향을 받지 않습니다.


# 참고

- [비주얼 스크립팅](Visual-Scripting.md)