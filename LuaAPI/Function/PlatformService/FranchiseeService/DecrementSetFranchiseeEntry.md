# DecrementSetFranchiseeEntry

## 설명
> Franchisee 저장된 EntryValue 값이 Long형일 경우 해당 Value를 감소 시킵니다.

## 선언
> USGFramework.Runtime.Contents.FranchiseeAPI.DecrementFranchiseeEntry

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 Franchisee 없을 경우 CallBack결과 값에 오류로 나타냅니다.

## Parameter
|         **형식**          |   **파라미터**   |           **설명**            |
|:-----------------------:|:------------:|:---------------------------:|
|        Function         |   Callback   | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
|           int           | ConnectionId |        대상 유저의 커넥션ID         |
| [EntryKey](EntryKey.md) |   EntryKey   |          가져올 엔트리 키          |
|           int           |    Amount    |           감소 시킬 량           |
## CallBack
|           **형식**            |   **파라미터**   |    **설명**    |
|:---------------------------:|:------------:|:------------:|
| [ResultData](ResultData.md) |    Result    |     결과 값     |
|             int             | ConnectionId | 대상 유저의 커넥션ID |
| [EntryValue](EntryValue.md) |  EntryValue  |    엔트리 값     |


## Sample Code
```lua
--Call
function this.Call_DecrementSetFranchiseeEntry()
    local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
    if Clients ~= nil then
        for i=0,Clients.Length -1 do
            local ConnectID = Clients[i].ConnectionID
            local EntryCode = "Test"
            local EntryKey =  "TestKey"
            local Amount =  5
            local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New(EntryCode,EntryKey)
            USGFramework.Runtime.Contents.FranchiseeAPI.DecrementFranchiseeEntry(this.CallBack_DecrementSetFranchiseeEntry,ConnectID,Key,Amount)
        end
    end
end
```

```lua
--CallBack
function this.Call_DecrementSetFranchiseeEntry()
    local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
    if Clients ~= nil then
        for i=0,Clients.Length -1 do
            local ConnectID = Clients[i].ConnectionID
            local EntryCode = "Test"
            local EntryKey =  "TestKey"
            local Amount =  5
            local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New(EntryCode,EntryKey)
            USGFramework.Runtime.Contents.FranchiseeAPI.DecrementFranchiseeEntry(this.CallBack_DecrementSetFranchiseeEntry,ConnectID,Key,Amount)
        end
    end
end
```
