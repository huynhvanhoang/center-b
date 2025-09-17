# IncrementFranchiseeEntryGlobal

## 설명
> Global함수는 모두가 접근 가능하며 공용으로 사용 가능한 함수입니다.
> Franchisee 에 저장된 Entry 값이 Long형일 경우 해당 Value를 증가 시킵니다.
## 선언
> USGFramework.Runtime.Contents.FranchiseeAPI.IncrementFranchiseeEntryGlobal
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 Franchisee 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|         **형식**          | **파라미터** |           **설명**            |
|:-----------------------:|:--------:|:---------------------------:|
|        Function         | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
| [EntryKey](EntryKey.md) | EntryKey |          가져올 엔트리 키          |
|           int           |  Amount  |        증가시킬 Value의 값        |
## CallBack
|           **형식**            |  **파라미터**  | **설명** |
|:---------------------------:|:----------:|:------:|
| [ResultData](ResultData.md) |   Result   |  결과 값  |
| [EntryValue](EntryValue.md) | EntryValue | 엔트리 값  |


## Sample Code
```lua
--Call
function this.Call_IncrementFranchiseeEntryGlobal()
   local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New("Test","TestKey")
   USGFramework.Runtime.Contents.FranchiseeAPI.IncrementFranchiseeEntryGlobal(this.CallBack_IncrementFranchiseeEntryGlobal,Key,10)
end
```

```lua
--CallBack
function this.CallBack_IncrementFranchiseeEntryGlobal(result EntryValue)
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
