# SendLuaEventToServer

## 설명

서버에 네트워크 이벤트를 발신합니다.

## 선언

NetworkUtility.SendLuaEventToServer (string eventName, string jsonString)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |



## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| string | eventName | 이벤트 이름 | 
| string | 	jsonString | 이벤트 파라미터 | 

## Return
|**형식**| **파라미터** |**설명**|
|:---:|:--------:|:---:|
|bool |  Result  | 부울 값을 반환하여 메서드가 성공적으로 실행되었는지 호출자에게 알립니다 |

---
스크립트를 빈 오브젝트 각각에 마운트한 후 Editor 를 실행하면 서버 Console 창에 이벤트가 발신한 정보의 모든 값을 출력합니다.
## Sample Code

Sender scripting
```lua
local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
local json = require 'cjson'
 
function this.Start()
    currentBlockAsset = thisLuaComponent:GetUnityObjectPropertyValueByIndex(0).UnityObject
    local event =
    {
        myName = thisGameObject.name,
        pos = thisTransform.position,
    }
    local jsonString = json.encode(event)
    NetworkUtility.SendLuaEvent("callMyName", jsonString)
end
```

Receiver scripting
```lua
local LuaEventCenter = USGFramework.Runtime.Core.USGLuaFramework.LuaEventCenter
local json = require 'cjson'
 
function this.OnEnable()
    LuaEventCenter.StartListenToEvent("callMyName", this.OnListenToCallMyName)
end
 
function this.OnDisable()
    LuaEventCenter.StopListenToEvent("callMyName", this.OnListenToCallMyName)
end
 
function  this.OnListenToCallMyName(message)
    local target = json.decode(message);
    print('object name is ' .. target.myName)
    print('object pos is ' .. target.pos.x .. ", " .. target.pos.y .. ", " .. target.pos.z)
end
```