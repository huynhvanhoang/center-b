# OnAuthorityChanged

## 설명

권한이 변경되면 권한 유무를 등록된 콜백으로 받습니다.

## 선언

NetworkIdentity.OnAuthorityChanged(bool IsAuthority)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| bool | IsAuthority | NetworkIdentity GameObject의 권한의 유무를 bool 타입으로 받음. | 

---
## Sample Code
콘솔창에 권한 유무를 출력합니다.
```lua
function this.Awake(luaComponentInfo)
    local eventListener = luaComponentInfo.TargetGameObject:GetComponent("NetworkIdentityEventListener")
    eventListener.OnAuthorityChanged = this.OnAuthorityChanged
end
 
function this.OnAuthorityChanged(authority)
    print(authority);
end
```