# GetSyncedString

## 설명
>이전에 SetSyncedString/SetSyncedNumber에 의해 이름으로 설정된 Lua 구성 요소의 명명된 문자열 값/숫자 값을 가져옵니다. 값이 없으면 기본값이 반환됩니다


## 선언
>thisLuaComponent:GetSyncedString(string name)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
| **형식** | **파라미터** | **설명** |
|:------:|:--------:|:------:|
| string |  Value   | 가져올 문자열 값/숫자 값의 이름  |


## Return
|     **형식**     | **파라미터** |                **설명**                |
|:--------------:|:--------:|:------------------------------------:|
|string |  Result  | 	메서드가 성공적으로 호출되었는지 여부 |


---
## Sample Code
```lua
local result

function this.Start()
    result = thisLuaComponent: GetSyncedString("item")
    print("GetSyncedString result: " .. result)
end
```
