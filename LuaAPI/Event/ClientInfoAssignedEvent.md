# ClientInfoAssignedEvent

## 설명

클라이언트가 할당될 때 트리거되며 콜백 메서드의 매개변수에는 로컬 클라이언트ConnectionID 가 있습니다.
이 이벤트는 ClientInfoJoinedEvent 전에 트리거되며 로컬 클라이언트에서만 트리거됩니다.

## 선언

EventCenter.StartListenToEvent(this.OnClientInfoAssigned,typeof(ClientInfoAssignedEvent))

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| this.OnClientInfoAssigned | this.OnClientInfoAssigned	 |The method to be called | 
|ClientInfoAssignedEvent | ClientInfoAssignedEvent | Event type | 

---
## Sample Code
임의의 객체에 스크립트를 마운트하고, 클라이언트가 연결되면 콘솔 창에
클라이언트의 ConnectionId 가 출력됩니다.
```lua
Local LuaEventCenter = USGFramework.Runtime.Core.USGLuaFramework.LuaEventCenter
local ClientInfoAssignedEvent = USGFramework.Runtime.Core.USGNetwork.Events.ClientInfoAssignedEvent
 
function this.Start()
   EventCenter.StartListenToEvent(this.OnClientInfoAssigned,typeof(ClientInfoAssignedEvent))
end
 
function this.OnDestroy()
    EventCenter.StopListenToEvent(this.OnClientInfoAssigned,typeof(ClientInfoAssignedEvent))
end
 
function this.OnClientInfoAssigned(event)
    local thisConnectionID = event.MyClientInfo.ConnectionID
    print(thisConnectionID)
end
```