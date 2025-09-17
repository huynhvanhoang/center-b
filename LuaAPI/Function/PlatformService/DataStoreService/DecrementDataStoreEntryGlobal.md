# DecrementDataStoreEntryGlobal

## 설명
> Global함수는 모두가 접근 가능하며 공용으로 사용 가능한 함수입니다.
> DataStore에 저장된 Entry 값이 Long형일 경우 해당 Value를 감소 시킵니다.

## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.DecrementDataStoreEntryGlobal
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 1. 가져올 DataStore가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
> 2. Value가 Long형일 때만 정상적인 동작이 가능합니다.
---


## Parameter
|         **형식**          | **파라미터** |           **설명**            |
|:-----------------------:|:--------:|:---------------------------:|
|        Function         | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
| [EntryKey](EntryKey.md) | EntryKey |          세팅할 엔트리 키          |
|           int           |  Amount  |           감소 시킬 량           |
## CallBack
|           **형식**            |  **파라미터**  |  **설명**  |
|:---------------------------:|:----------:|:--------:|
| [ResultData](ResultData.md) |   Result   |   결과 값   |
| [EntryValue](EntryValue.md) | EntryValue | 변경된 결과 값 |


## Sample Code
```lua
--Call
function this.Call_DecrementDataStoreEntryGlobal()
       local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New("Test","TestKey")
        USGFramework.Runtime.Contents.DataStoreAPI.DecrementDataStoreEntryGlobal(this.CallBack_DecrementDataStoreEntryGlobal,Key,10)
end
```

```lua
--CallBack
function this.CallBack_DecrementDataStoreEntryGlobal(result,EntryValue)
        print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
 
        local _Bool = EntryValue.BoolValue
        local _Long =EntryValue.LongValue
        local _String =EntryValue.StringValue
 
        local Type = tostring(EntryValue.DataType)
        print("@ValueType  :".. tostring(Type))
        if Type == "Long" then
            print("@LongValue  :".. tostring(_Long))
        elseif Type == "String" then
            print("@Key is not of type Long.")
        elseif Type == "Bool" then
            print("@Key is not of type Long.")
        elseif Type == "None" then
            print("@Key is not of type Long.")
        end
    end
```
