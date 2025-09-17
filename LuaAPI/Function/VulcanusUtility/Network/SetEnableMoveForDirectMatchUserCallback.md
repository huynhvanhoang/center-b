# SetEnableMoveForDirectMatchUserCallback

## 설명

해당 모드에 다이렉트매칭으로 매칭된 유저를 허용할 것인지를 응답하는 루아 함수를 설정합니다. 다이렉트 매칭시 해당 콜백 함수가 호출되며, 해당 결과에 따라 매칭 여부가 결정됩니다.

해당 API 는 서버 스크립트에서만 유효합니다.

## 선언

NetworkUtility.SetEnableMoveForDirectMatchUserCallback(LuaFunction callback)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| LuaFunction | callback | 다이렉트 매칭 성공 여부를 반환하는 루아 함수 | 

---
## Sample Code
모드에서 이미 게임이 시작 된 상태에서 특정 유저가 친구 따라가기 기능 등으로 다이렉트매칭을 할 경우 매칭이 실패 되도록 합니다.
```lua
function this.Start(luaComponentInfo)
    if NetworkUtility.IsServer() then
        NetworkUtility.SetEnableMoveForDirectMatchUserCallback(this.OnEnableMoveForDirectMatchUser)
    end
end
 
function this.OnEnableMoveForDirectMatchUser()
    if not NetworkUtility.IsServer() then return false end
    return isGameStarted == false
end
```