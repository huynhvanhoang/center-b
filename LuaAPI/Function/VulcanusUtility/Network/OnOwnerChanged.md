# OnOwnerChanged

## 설명

소유권이 변경되면 소유권을 가진 GameObject를 등록된 콜백으로 받습니다.

## 선언

NetworkIdentity.OnOwnerChanged(GameObject OwnerObject)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| GameObject | OwnerObject | NetworkIdentity GameObject의 Owner GameObject (권한을 가지고 있는 GameObject)를 받음. | 

---
## Sample Code
콘솔창에 소유권을 가진 GameObject의 이름을 출력합니다.
```lua
function this.Awake(luaComponentInfo)
    local eventListener = luaComponentInfo.TargetGameObject:GetComponent("NetworkIdentityEventListener")
    eventListener.OnOwnerChanged = this.OnOwnerChanged
end
 
function this.OnOwnerChanged(ownerGameObject)
    print(ownerGameObject.name);
end
```