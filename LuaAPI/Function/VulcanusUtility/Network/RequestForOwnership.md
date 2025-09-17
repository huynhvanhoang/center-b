# RequestForOwnership

## 설명

지정한 네트워크 오브젝트의 소유권을 획득합니다. (참고: Scene 오브젝트는 소유권을 바꿀 수 없습니다.)

## 선언

NetworkUtility.RequestForOwnership(GameObject gameObject)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| gameObject | gameObject | 소유권을 획득해야 할 네트워크 오브젝트 | 

## Return
|**형식**| **파라미터** |                  **설명**                  |
|:---:|:--------:|:----------------------------------------:|
|Boolean |  Result  |bool 값을 반환하여 메서드가 성공적으로 실행되었는지 호출자에게 알립니다 |

---
## Sample Code
스크립트를 빈 오브젝트에 나누어 마운트한 후, 빨간색 오브젝트를 클릭하면 초록색으로 바뀌고 초록색 오브젝트를 클릭하면 아무런 변화가 일어나지 않습니다. (참고: 이 사용 사례는 IsOwner 사용 사례와 함께 적용해야 합니다.)
```lua
local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
local Input = UnityEngine.Input
 
function this.Update()
    if(Input.GetMouseButtonDown(0)) then
        local camera = UnityEngine.Camera.main
        local ray  = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
         
        if flag then
            print('pick from lua, point: '..tostring(hit.point))
            NetworkUtility.RequestForOwnership(hit.transform.gameObject)
        end
    end
end
```