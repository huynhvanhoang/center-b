# DeleteDataStoreEntry

## 설명
> DataStore에 저장된 값이 있을 경우 값 을 삭제 합니다.

## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.DeleteDataStoreEntry

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 1. 가져올 DataStore가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
> 2. 해당 EntryKey값으로 데이터가 저장되어 있어야 정상적인 동작을 합니다.
---


## Parameter
|         **형식**          |   **파라미터**   |           **설명**            |
|:-----------------------:|:------------:|:---------------------------:|
|        Function         |   Callback   | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
|           int           | ConnectionId |        대상 유저의 커넥션ID         |
| [EntryKey](EntryKey.md) |   EntryKey   |       삭제할 값의 EntryKey       |

## CallBack
|           **형식**            |   **파라미터**   |    **설명**    |
|:---------------------------:|:------------:|:------------:|
| [ResultData](ResultData.md) |    Result    |     결과 값     |
|             int             | ConnectionId | 대상 유저의 커넥션ID |

## Sample Code
```lua
--Call
function this.Call_DeleteDataStoreEntry()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i=0, Clients.Length -1 do
                local ConnectID = Clients[i].ConnectionID
                local EntryCode =  "Test"
                local EntryKey =  "TestKey"
                local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New(EntryCode,EntryKey)
                USGFramework.Runtime.Contents.DataStoreAPI.DeleteDataStoreEntry(this.CallBack_DeleteDataStoreEntry,ConnectID,Key)
            end
        end
    end
```

```lua
function this.CallBack_DeleteDataStoreEntry(result,TargetConnectionID)
        print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
        print("@ConnectionID :".. tostring(TargetConnectionID))
end
```
