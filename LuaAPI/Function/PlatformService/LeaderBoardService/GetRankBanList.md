# GetRankBanList

## 설명
> 순위 차단 유저 리스트를 가져옵니다.
## 선언
> USGFramework.Runtime.Contents.LeaderboardAPI.GetRankBanList
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 LeaderBoard가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|  **형식**  |    **파라미터**     |           **설명**            |
|:--------:|:---------------:|:---------------------------:|
| Function |    Callback     | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
|   int    |  ConnectionId   |        대상 유저의 커넥션ID         |
|  string  |  LeaderboardId  |           리더보드 ID           |
|   long   | QueryNickNameNo |           닉네임 넘버            |
|   int    |    PageIndex    |          페이지 Index          |
|   int    |    	PageSize    |          페이지 Size           |
| string[] |   	Properties   |           리더보드 속성           |
## CallBack
|              **형식**              |  **파라미터**  |  **설명**  |
|:--------------------------------:|:----------:|:--------:|
|   [ResultData](ResultData.md)    |   Result   |   	결과값   |
| [RankBanInfo](RankBanInfo.md)[ ] |  BanDatas  | 	Ban 데이터 |
|               int                | TotalCount |  	총 개수   |


## Sample Code
```lua
--Call
   function this.Call_GetRankBanList()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        if Clients ~= nil then
            for i=0,Clients.Length -1 do
                local ConnectionId = Clients[i].ConnectionID
 
                local ID = "LeaderBoardID"
                local NicNameNumber = 1001
                local PageNumber = 1
                local PageSize = 20
                local properties = {"character_no", "rank", "score", "character_name", "profile_image", "personal_data", "prev_rank", "prev_score", "last_launch_time", "last_privilege_status"}
     
                USGFramework.Runtime.Contents.LeaderboardAPI.GetRankBanList(this.CallBack_GetRankBanList,ConnectionId,ID,NicNameNumber,PageNumber,PageSize,properties)
            end
        end
    end
```

```lua
--CallBack
function this.CallBack_GetRankBanList(Result,RankDatas,TotalCount)
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
