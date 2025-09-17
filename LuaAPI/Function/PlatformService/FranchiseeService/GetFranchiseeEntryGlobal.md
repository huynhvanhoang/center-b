# GetFranchiseeEntryGlobal

## 설명
> Global함수는 모두가 접근 가능하며 공용으로 사용 가능한 함수입니다.
> Franchisee에 저장된 EntryValue값을 EntryKey를 통해 가져옵니다.
## 선언
> USGFramework.Runtime.Contents.FranchiseeAPI.GetFranchiseeEntryGlobal
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 Franchisee 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|           **형식**            | **파라미터** |           **설명**            |
|:---------------------------:|:--------:|:---------------------------:|
|          Function           | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
| [EntryValue](EntryValue.md) | EntryKey |          가져올 엔트리 키          |
## CallBack
|           **형식**            |  **파라미터**  | **설명** |
|:---------------------------:|:----------:|:------:|
| [ResultData](ResultData.md) |   Result   |  결과 값  |
| [EntryValue](EntryValue.md) | EntryValue | 엔트리 값  |


## Sample Code
```lua
--Call
function this.Call_GetFranchiseeEntryGlobal()
     local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New("Test","TestKey")
    USGFramework.Runtime.Contents.FranchiseeAPI.GetFranchiseeEntryGlobal(this.CallBack_GetFranchiseeEntryGlobal,Key)
end
```

```lua
--CallBack
function this.CallBack_GetFranchiseeEntryGlobal(result,entryValue)
    print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
 
    local _Bool = entryValue.BoolValue
    local _Long =entryValue.LongValue
    local _String =entryValue.StringValue
 
    local Type = tostring(entryValue.DataType)
    print("@ValueType  :".. tostring(Type))
    if Type == "Long" then
        print("@LongValue  :".. tostring(_Long))
    elseif Type == "String" then
        print("@StringValue  :".. tostring(_String))
    elseif Type == "Bool" then
        print("@BoolValue  :".. tostring(_Bool))
    elseif Type == "None" then
        print("@@@_Noen")
    end
end
```
