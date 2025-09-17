# ClientDisconnectedEvent

## 설명

클라이언트가 서버와 연결을 끊을 때 트리거되며, 콜백 메서드의 매개변수는 서버에 연결된 클라이언트의 ConnectionID 를 갖게 됩니다. 이 이벤트는 이벤트를 수신하는 모든 클라이언트에서 트리거됩니다.

## 선언

EventCenter.StartListenToEvent(this.OnClientDisconnected,typeof(ClientDisconnectedEvent))

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| Function | this.OnClientDisconnected | 호출 방법 | 
| FunctionType | ClientDisconnectedEvent | 이벤트 유형 | 

---
## Sample Code
임의의 객체에 스크립트를 마운트하고, 클라이언트가 연결되면 콘솔 창에
클라이언트의 ConnectionId 가 출력됩니다
```lua

local EventCenter = USGFramework.Runtime.USGZone.EventCenter
local ClientInfoAssignedEvent = USGFramework.Runtime.Core.USGNetwork.Events.ClientDisconnectedEvent
 
function this.Start()
   EventCenter.StartListenToEvent(this.OnClientDisconnected,typeof(ClientDisconnectedEvent))
end
 
function this.OnDestroy()
    EventCenter.StopListenToEvent(this.OnClientDisconnected,typeof(ClientDisconnectedEvent))
end
 
function this.OnClientDisconnected(event)
    local DisConnectedConnectionID = event.DisconnectedClient.ConnectionID
    print(DisConnectedConnectionID)
end

```