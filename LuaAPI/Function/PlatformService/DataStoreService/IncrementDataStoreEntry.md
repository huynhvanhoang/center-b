# IncrementDataStoreEntry

## 설명
> DataStore에 저장된 Entry 값이 Long형일 경우 해당 Value를 증가 시킵니다.

## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.IncrementDataStoreEntry

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 DataStore가 없을 경우 CallBack결과 값에 오류로 나타냅니다.  
> Value가 Long형일 때만 정상적인 동작이 가능합니다.
---


## Parameter
|         **형식**          |   **파라미터**   |             **설명**             |
|:-----------------------:|:------------:|:------------------------------:|
|        Function         |   Callback   |  반환된 결과를 받는 데 사용되는 콜백 메서드입니다   |
|           int           | ConnectionId |          대상 유저의 커넥션ID          |
| [EntryKey](EntryKey.md) |   EntryKey   |           가져올 엔트리 키            |
|           int           |    Amount    | 현재 Value가 Long형 일 때 값을 증가 시킬 량 |

## CallBack
|           **형식**            |   **파라미터**   |    **설명**    |
|:---------------------------:|:------------:|:------------:|
| [ResultData](ResultData.md) |    Result    |     결과 값     |
|             int             | ConnectionId | 대상 유저의 커넥션ID |
| [EntryValue](EntryValue.md) |  EntryValue  |    엔트리 값     |

## Sample Code
```lua
--Call
function this.Call_IncrementDataStoreEntry()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i=0,Clients.Length - 1 do
                local ConnectID = Clients[i].ConnectionID
                local EntryCode = "Test"
                local EntryKey =  "TestKey"
                local Amount =  5
                local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New(EntryCode,EntryKey)
                USGFramework.Runtime.Contents.DataStoreAPI.IncrementDataStoreEntry(this.CallBack_IncrementDataStoreEntry,ConnectID,Key,Amount)
            end
        end
    end
```

```lua
--CallBack
function this.CallBack_IncrementDataStoreEntry(result,TargetConnectionID,EntryValue)
        print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
 
        local _Bool = EntryValue.BoolValue
        local _Long =EntryValue.LongValue
        local _String =EntryValue.StringValue
 
        local Type = tostring(EntryValue.DataType)
        print("@TargetConnectionID  :".. tostring(TargetConnectionID))
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
