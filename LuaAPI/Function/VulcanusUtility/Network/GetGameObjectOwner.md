# GetGameObjectOwner

## 설명

지정한 네트워크 오브젝트의 소유권을 가진 클라이언트의 ID 를 획득합니다.

## 선언

NetworkUtility.GetGameObjectOwner(GameObject gameObject, LuaFunction onGetGameObjectOwner)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
|   **형식**   |      **파라미터**       |                  **설명**                  |
|:---:|:---:|:----------------------------------------:|
| GameObject | gameObject |        소유자 ID 를 획득해야 할 네트워크 오브젝트         | 
| LuaFunction | onGetGameObjectOwner | 콜백 메서드이며 파라미터는 이 네트워크 오브젝트와 소유자의 ID 입니다. | 

## Return
|**형식**| **파라미터** |**설명**|
|:---:|:--------:|:---:|
|Boolean |  Result  | 메서드가 성공적으로 실행되었는지 여부를 호출자에게 알려주는 bool 값을 반환합니다 |

---
## Sample Code
스크립트를 빈 오브젝트에 나누어 마운트한 후 검사가 필요한 오브젝트를 클릭하면 Console 창에 이
네트워크 오브젝트의 소유권을 가진 클라이언트 ID 를 출력합니다.
```lua
local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
local Input = UnityEngine.Input
 
function this.Update()
    if Input.GetMouseButtonDown(0) then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            NetworkUtility.GetGameObjectOwner(hit.transform.gameObject, this.GetConnectionID)
        end
    end
end
 
function this.GetConnectionID(gameObject, connectionID)
    print('Target connectionID: ' .. connectionID)
end
```