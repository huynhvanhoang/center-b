# DeleteFranchiseeEntry

## 설명
> Franchisee에 저장된 값이 있을 경우 값 을 삭제 합니다.
## 선언
> USGFramework.Runtime.Contents.FranchiseeAPI.DeleteFranchiseeEntry
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 Franchisee 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|         **형식**          |   **파라미터**   |           **설명**            |
|:-----------------------:|:------------:|:---------------------------:|
|        Function         |   Callback   | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
|           int           | ConnectionId |        대상 유저의 커넥션ID         |
| [EntryKey](EntryKey.md) |   EntryKey   |          세팅할 엔트리 키          |
## CallBack
|           **형식**            |   **파라미터**   |    **설명**    |
|:---------------------------:|:------------:|:------------:|
| [ResultData](ResultData.md) |    Result    |     결과 값     |
|             int             | ConnectionId | 대상 유저의 커넥션ID |


## Sample Code
```lua
--Call
function this.Call_DeleteFranchiseeEntry()
    local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
    if Clients ~= nil then
        for i=0,Clients.Length - 1 do
            local ConnectID = Clients[i].ConnectionID
            local EntryCode =  "Test"
            local EntryKey =  "TestKey"
            local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New(EntryCode,EntryKey)
            USGFramework.Runtime.Contents.FranchiseeAPI.DeleteFranchiseeEntry(this.CallBack_DeleteFranchiseeEntry,ConnectID,Key)
        end
    end
end
```

```lua
--CallBack
function this.CallBack_DeleteFranchiseeEntry(result,ConnectionID)
   print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
end
```

