# IsOwner

## 설명

본 클라이언트가 타겟 네트워크 오브젝트의 소유권을 가졌는지 판단합니다

## 선언

NetworkUtility.IsOwner(GameObject gameObject)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

스크립트를 검사가 필요한 오브젝트에 마운트하면 소유권을 가진 네트워크 오브젝트가 초록색으로 보일 것이고, 소유권을 갖지 않은 네트워크 오브젝트는 빨간색으로 보일 것입니다
//이미지는 이렇게!!!()
![](media/images/LuaNetwork_2.png)

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| gameObject | gameObject | 소유권이 결정되어야 할 네트워크 오브젝트 | 

## Return
|**형식**| **파라미터** |                   **설명**                    |
|:---:|:--------:|:-------------------------------------------:|
|Boolean |  Owner   | Bool 반환하여 호출자에게 네트워크 오브젝트의 소유권을 가졌는지 알려 줍니다 |

---
## Sample Code

```lua
local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
local redMaterial
local greenMaterial
local meshRenderer
 
function this.Start()
    redMaterial = thisLuaComponent:GetUnityObjectPropertyValueByName("RedMaterial").UnityObject
    greenMaterial = thisLuaComponent:GetUnityObjectPropertyValueByName("GreenMaterial").UnityObject
    meshRenderer = thisGameObject:GetComponent("MeshRenderer")
end
 
function this.Update()
    if(NetworkUtility.IsOwner(thisGameObject))
    then
        meshRenderer.sharedMaterial = greenMaterial
    else
        meshRenderer.sharedMaterial = redMaterial
    end
end
```