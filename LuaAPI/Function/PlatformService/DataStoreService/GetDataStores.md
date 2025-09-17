# GetDataStores

## 설명
> 현재 UGC에 있는 모든 DataStore에 대한 정보를 얻어옵니다.

## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.GetDataStores

## 주의사항 
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 DataStore가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|  **형식**  |   **파라미터**    |                 **설명**                  |
|:--------:|:-------------:|:---------------------------------------:|
| Function |   Callback    |       반환된 결과를 받는 데 사용되는 콜백 메서드입니다       |
|   int    | ConnectionId  |              대상 유저의 커넥션ID               |
|   int    |    PageNum    |         현재 페이지, 1 이상, 기본값은 1입니다         |
|   int    |   PageSize    | 페이지당 데이터 양은 1 이상, 기본값은 20, 최대값은 200입니다. |
|  String  |    Prefix     |       범위를 지정하는 데 사용할 수 있는 접두사 검색        |

## CallBack
|           **형식**            |   **파라미터**   |    **설명**    |
|:---------------------------:|:------------:|:------------:|
| [ResultData](ResultData.md) |    Result    |     결과 값     |
|             int             | ConnectionId | 대상 유저의 커넥션ID |
|             int             |   PageNum    |    현재 페이지    |
|             int             |   PageSize   |   페이지 사이즈    |
|             int             |    Total     |     총 개수     |
|             int             |  TotalPages  |    총 페이지     |
| [DataStore](DataStore.md)[] | 	DataStores  |  데이터코드 리스트   |


## Sample Code 
```lua
--Call
function this.Call_GetDataStores()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i= 0 ,Clients.Length -1 do
                local ConnectionID = Clients[i].ConnectionID
                local PageNumber = 1
                local PageSize = 20
                local Prefix = ""
                USGFramework.Runtime.Contents.DataStoreAPI.GetDataStores(this.CallBack_GetDataStores,ConnectionID,PageNumber,PageSize,Prefix)
            end
        end
    end
```

```lua
--CallBack
function this.CallBack_GetDataStores(result,TargetConnectionID,pageNo,pageSize,total,totalPage,dataStores)
        print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
        print("@TargetConnectionID :".. tostring(TargetConnectionID))
        print("@PageNO :".. tostring(pageNo))
        print("@PageSize :".. tostring(pageSize))
        print("@Total :".. tostring(total))
        print("@TotalPage :".. tostring(totalPage))
        for i = 0, dataStores.Length - 1 do
            print("@DataStore Code :".. dataStores[i].DatastoreCode)
            print("@DataStore CreatedAt :".. dataStores[i].CreatedAt)
        end 
    end
```