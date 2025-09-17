# SetRankUser

## 설명
> 유저 랭킹 정보 저장합니다.
## 선언
> USGFramework.Runtime.Contents.LeaderboardAPI.SetRankUser
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 LeaderBoard가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|   **형식**   |   **파라미터**    |            **설명**             |
|:----------:|:-------------:|:-----------------------------:|
|  Function  |   Callback    |  반환된 결과를 받는 데 사용되는 콜백 메서드입니다  |
|    int     | ConnectionId  |         대상 유저의 커넥션ID          |
|   string   | LeaderboardId |            리더보드 ID            |
|    long    |     Score     |              점수               |
|   string   | PersonalData  | 사용자 정의 개인 데이터, 데이터 제한 최대 256  |
|   string   |   	Customs    |     커스텀 랭킹에 점수를 등록할때 설정값      |
## CallBack
|           **형식**            | **파라미터** | **설명** |
|:---------------------------:|:--------:|:------:|
| [ResultData](ResultData.md) |  Result  |  	결과값  |


## Sample Code
```lua
--Call
  function this.Call_SetRankUser()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i=0,Clients.Length -1 do
                local ConnectionId = Clients[i].ConnectionID
                local ID = "LeaderBoardID"
                local Score = 10
                local PersonalData = ""
                local Customs = ""
                USGFramework.Runtime.Contents.LeaderboardAPI.SetRankUser(this.CallBack_SetRankUser,ConnectionId,ID,Score,PersonalData,Customs)
            end
        end
    end
```

```lua
--CallBack
function this.CallBack_SetRankUser(Result)
   print("@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message))
end
```

