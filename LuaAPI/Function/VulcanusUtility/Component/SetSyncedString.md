# SetSyncedString
GetSyncedString
## 설명
> 데이터 동기화를 위해 서버로 전달되는 현재 Lua스크립트(thisLuaComponent)에 대해 명명된 문자열/숫자값을 설정합니다.
>자주 변경되고 최신 값만 중요한 데이터에 대한 보다 효율적인 데이터 동기화 메커니즘으로 사용해야 합니다. 자주 변경되지 않거나 데이터 변경 순서가 중요한 데이터의 경우 RPC를 대신 사용합니다.

## 선언
>thisLuaComponent: SetSyncedString(string name, string value)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
| **형식** | **파라미터** | **설명** |
|:------:|:--------:|:------:|
| string |  name    | 동기화할 문자열 값/숫자 값의 이름  |
| string |   value    | 동기화할 문자열 값/숫자 값  |


## Return
|     **형식**     |  **파라미터**   |                **설명**                |
|:--------------:|:-----------:|:------------------------------------:|
|Result | bool | 	메서드가 성공적으로 호출되었는지 여부 |



---
## Sample Code
```lua
local result

function this.Start()
    if USGFramework.Runtime.Core.USGNetwork.NetworkUtility.IsServer() == false then
        result = thisLuaComponent:SetSyncedString("item", "item1")
        print("SetSyncedString result: "..tostring(result))
    end
end
```
