# GetRankUser

## 설명
> 순위 페이지 수를 가져옵니다.
## 선언
> USGFramework.Runtime.Contents.LeaderboardAPI.GetPageCount
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 LeaderBoard가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|  **형식**  |   **파라미터**    |                 **설명**                 |
|:--------:|:-------------:|:--------------------------------------:|
| Function |   Callback    |      반환된 결과를 받는 데 사용되는 콜백 메서드입니다       |
|   int    | ConnectionId  |              대상 유저의 커넥션ID              |
|  string  | LeaderboardId |                리더보드 ID                 |
|   int    |    KeyType    |          검색순위의 종류값. 현재 0만 사용           |
|  string  |   KeyValue    | 검색 종류에 따른 값. Type이 0일 시 해당값을 사용하지 않습니다 |
|   int    |   PageSize    |                페이지 Size                |
| string[] |  Properties   |                리더보드 속성                 |
## CallBack
|           **형식**            |  **파라미터**  | **설명** |
|:---------------------------:|:----------:|:------:|
| [ResultData](ResultData.md) |   Result   |  	결과값  |
|             int             | TotalCount |  총 개수  |


## Sample Code
```lua
--Call
  function this.Call_GetPageCount()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i=0,Clients.Length -1 do
                local ConnectionId = Clients[i].ConnectionID
                local ID = "LeaderBoardID"
                local KeyType = 0
                local KeyValue = "0"
                local PageSize = 20
                local properties = {"character_no", "rank", "score", "character_name", "profile_image", "personal_data", "prev_rank", "prev_score", "last_launch_time", "last_privilege_status"}
                USGFramework.Runtime.Contents.LeaderboardAPI.GetPageCount(this.CallBack_GetPageCount,ConnectionId,ID,KeyType,KeyValue,PageSize,properties)
            end
        end
    end
```

```lua
--CallBack
function this.CallBack_GetPageCount(Result,TotalCount)
    print("@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message))
    print("@TotalCount :".. tostring(TotalCount))
end
```
