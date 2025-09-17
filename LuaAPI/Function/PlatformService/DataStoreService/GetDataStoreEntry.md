# GetDataStoreEntry

## 설명
> DataStore에 저장된 EntryValue값을 가져옵니다.
## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.GetDataStoreEntry
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 DataStore가 없을 경우 CallBack결과 값에 오류로 나타냅니다.


## Parameter
|         **형식**          |   **파라미터**   |                  **설명**                  |
|:-----------------------:|:------------:|:----------------------------------------:|
|        Function         |   Callback   |       반환된 결과를 받는 데 사용되는 콜백 메서드입니다        |
|           int           | ConnectionId |               대상 유저의 커넥션ID               |
| [EntryKey](EntryKey.md) |   EntryKey   |                가져올 엔트리 키                 |
|         string          |   FreeData   | 사용자가 원하는 데이터를 CallBack에서 그대로 사용하기 위한 데이터 |
## CallBack
|           **형식**            |   **파라미터**   |                  **설명**                  |
|:---------------------------:|:------------:|:----------------------------------------:|
| [ResultData](ResultData.md) |    Result    |                   결과 값                   |
|             int             | ConnectionId |               대상 유저의 커넥션ID               |
| [EntryValue](EntryValue.md) |  EntryValue  |                  엔트리 값                   |
|           string            |   FreeData   | 사용자가 원하는 데이터를 CallBack에서 그대로 사용하기 위한 데이터 |


## Sample Code
```lua
--Call
function this.Call_GetDataStoreEntry()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i=0,Clients.Length -1 do
                local ConnectionID = Clients[i].ConnectionID
                local Code = "Test"
                local Key = "TestKey"
                local EntryKey = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New(Code,Key)
                USGFramework.Runtime.Contents.DataStoreAPI.GetDataStoreEntry(this.CallBack_GetDataStoreEntry,ConnectionID,EntryKey,"FreeData")
            end
        end
    end
```

```lua
--CallBack
 function this.CallBack_GetDataStoreEntry(result,TargetConnectionID,entryValue,FreeData)
       print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
 
        local _Bool = entryValue.BoolValue
        local _Long =entryValue.LongValue
        local _String =entryValue.StringValue
 
        local Type = tostring(entryValue.DataType)
        print("@TargetConnectionID  :".. tostring(TargetConnectionID))
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
        print("@@"..FreeData)
    end
```
