# TeleportCallback

## 설명

Transform 텔레포트(강제이동) 후 추가 정보 (payload) 가 있다면 등록된 callback으로 전달 받습니다.

## 선언

NetworkUtility.TeleportCallback(Transform transform, string payload)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| Transform | transform | 콜백 메시지를 받을 GameObject의 Transform | 
| string | payload | 이동 후 전달 받은 추가 정보. | 

---
## Sample Code
텔레포트한 transform이름과 추가 전달인자(payload)를 출력합니다.
```lua
local thisTransform
  
function this.Awake(luaComponentInfo)
    thisTransform = luaComponentInfo.TargetTransform
end
  
function this.Teleport(position, rotation)
    local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
    local message = "freeze:3"
    local sendSuccess = NetworkUtility.Teleport(thisTransform, position, rotation, message)
 
    -- callback
    NetworkUtility.TeleportCallback = this.TeleportCallback
end 
 
function this.TeleportCallback(transform, payload)
    print(transform.name)
    print(payload)
end
```