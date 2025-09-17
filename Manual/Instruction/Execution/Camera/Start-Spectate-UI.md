# Start Spectate UI

Performer를 실행하면 지정한 타겟(플레이어)을 대상으로 관전 카메라 UI를 실행합니다.


## Parameter

| **이름**      | **설명**                                    |
|-------------|-------------------------------------------|
| Target      | All : 모든 플레이어를 대상으로 실행된 관전 카메라 UI를 실행합니다  |
|             | Target : 특정 타겟을 대상으로 실행된 관전 카메라 UI를 실행합니다 |


## Tip

1. 관전 상태에서 플레이 상태로 전환하기
    - Character를 리스폰합니다.
    - End Spectate UI를 종료하고, On Character controller 실행합니다.
    - HUD UI Visible 스크립트를 이용하여 UI를 표시합니다.


## 참고

- [리스폰 스크립트](Respawn.md)
- [캐릭터 컨트롤러 켜기](Start-Character-Controller.md)
- [HUD UI Visible](Set-HUDUI-Visible.md)