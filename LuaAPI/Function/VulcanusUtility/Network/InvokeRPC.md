# InvokeRPC

## 설명

서버를 불러내 모든 클라이언트에 호출하고 수신하는 메서드입니다. (참고: 네트워크오브젝트만 RPC 를 발신할 수 있습니다.)

## 선언

LuaEventCenter.InvokeRPC(string functionName, string args)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| string | functionName | 	호출할 메서드 이름 | 
| string | args | 호출에 필요한 파라미터 | 

## Return
|**형식**| **파라미터** |                 **설명**                  |
|:---:|:--------:|:---------------------------------------:|
|Boolean |  Result  | 부울 값을 반환하여 메서드가 성공적으로 실행되었는지 호출자에게 알립니다 |

---
## Sample Code
스크립트를 임의로 선택한 네트워크 오브젝트에 마운트한 후 Space 키를 누르면 모든 클라이언트의 Console 창에 이 네트워크 오브젝트의 명칭을 출력합니다
```lua
local Input = UnityEngine.Input
local json = require 'cjson'
 
function this.Update()
    if Input.GetKeyDown("space") then
        local event = { myName = thisGameObject.name }
        local jsonString = json.encode(event)
        thisLuaComponent:InvokeRPC('RPCCounter', jsonString)
    end
end
 
function this.RPCCounter(message)
    local target = json.decode(message);
    print('name: ' .. target.myName)
end
```