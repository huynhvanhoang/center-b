# SendLuaEventToClients

## 설명

NetworkUtility.SendLuaEventToClients(string eventName, string jsonString, params int[] receiversConnectionID)

## 선언

//함수의 네임스페이스

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
| **형식** |       **파라미터**        |     **설명**      |
|:------:|:---------------------:|:---------------:|
| string |       eventName       |     이벤트 이름      | 
| string |      jsonString       |    이벤트 파라미터     | 
| int[]  | receiversConnectionID | 타겟 클라이언트 ID 컬렉션 | 

## Return
| **형식**  | **파라미터** |                    **설명**                     |
|:-------:|:--------:|:---------------------------------------------:|
| Boolean |  Result  | Returns a boolean value that tells the caller |

---
## Sample Code
스크립트를 빈 오브젝트에 나누어 마운트한 후 Editor 를 실행하면, 지정된 클라이언트의 Console 창에 이벤트가 발신한 정보의 모든 값을 출력합니다

Sender scripting
```lua
local EventCenter = CommonFramework.Runtime.EventCenter
local ClientJoinedEvent = USGFramework.Runtime.Core.USGNetwork.Events.ClientJoinedEvent
local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
local json = require 'cjson'
 
function this.Start()
    EventCenter.StartListenToEvent(this.OnClientJoined, typeof(ClientJoinedEvent))
end
 
function this.OnClientJoined(event)
    local message = { senderID = event.NewClient.ConnectionID }
    local jsonString = json.encode(message)
    NetworkUtility.SendLuaEventToClients("Wellcome", jsonString, event.NewClient.ConnectionID)
end
```

Receiver scripting
```Lua
local LuaEventCenter = USGFramework.Runtime.Core.USGLuaFramework.LuaEventCenter
local json = require 'cjson'
 
function this.OnEnable()
    LuaEventCenter.StartListenToEvent("Wellcome", this.OnWellcome)
end
 
function this.OnDisable()
    LuaEventCenter.StopListenToEvent("Wellcome", this.OnWellcome)
end
 
function this.OnWellcome(message)
    local target = json.decode(message);
    print('Wellcome player: ' .. target.senderID)
end
```