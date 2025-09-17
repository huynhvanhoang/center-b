# GetRankUserRange

## 설명
> 해당 순위 구간의 유저정보를 가져옵니다.
## 선언
> USGFramework.Runtime.Contents.LeaderboardAPI.GetRankUserRange
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
|   long   |   StartRank   |                 닉네임 넘버                 |
|   int    |    EndRank    |                  끝 순위                  |
| string[] |  Properties   |                리더보드 속성                 |
## CallBack
|                **형식**                 |  **파라미터**  | **설명**  |
|:-------------------------------------:|:----------:|:-------:|
|      [ResultData](ResultData.md)      |   Result   |  	결과값   |
| [RankCommonData](RankCommonData.md)[] | RankDatas  | 	랭크 데이터 |
|                  int                  | TotalCount | 		총 개수  |


## Sample Code
```lua
--Call
function this.Call_GetRankUserRange()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i=0,Clients.Length -1 do
                local ConnectionId = Clients[i].ConnectionID
                local ID = "LeaderBoardID"
                local KeyType = 0
                local KeyValue = "0"
                local StartRank = 1
                local EndRank = 10
                local properties = {"character_no", "rank", "score", "character_name", "profile_image", "personal_data", "prev_rank", "prev_score", "last_launch_time", "last_privilege_status"}
             
                USGFramework.Runtime.Contents.LeaderboardAPI.GetRankUserRange(this.CallBack_GetRankUserRange,ConnectionId,ID,KeyType,KeyValue,StartRank,EndRank,properties)
            end
        end
    end
```

```lua
--CallBack
function this.CallBack_GetRankUserRange(Result,RankDatas,TotalCount)m
        print("@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message))
 
        for i = 0, RankDatas.Length-1 do
            print("@NicName :"..RankDatas[i].Nickname)
            print("@NicNameNumber :"..RankDatas[i].NicknameNo)
            print("@LastLaunchTime :"..RankDatas[i].LastLaunchTime)
            print("@PersonalData :"..RankDatas[i].PersonalData)
            print("@PrevRank :"..RankDatas[i].PrevRank)
            print("@PrevScore :"..RankDatas[i].PrevScore)
            print("@ProfileImage :"..RankDatas[i].ProfileImage)
            print("@Rank :"..RankDatas[i].Rank)
            print("@Score :"..RankDatas[i].Score)
        end
    end
```
