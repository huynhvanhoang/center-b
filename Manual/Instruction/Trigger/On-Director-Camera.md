# On Director Camera

작동 중인 연출 카메라가 종료 될 때, 트리거를 실행합니다.


## Tip

On Director Camera Instruction은 작동이 완료될 카메라 오브젝트에 설정되어 있어야 합니다.  

설정 방식
1. 카메라가 종료되었을 때 다른 장치에 영향을 받게 할 경우 현재 작동 중인 카메라 오브젝트 하위에 On director camera 트리거를 설정합니다.
2. 트리거에 작동할 Performer로 Send Event Message를 설정합니다.
3. 카메라 작동이 종료되었을 때 실행할 장치를 연결합니다.


## 참고

- [장치간 이벤트 연결하기](Connect-Event-Between-Devices.md)
- [Send Event Message](Send-Event-Message.md)