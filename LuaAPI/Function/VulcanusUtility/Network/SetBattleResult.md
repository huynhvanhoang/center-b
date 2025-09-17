# SetBattleResult

## 설명

해당 라운드의 게임 결과를 설정합니다. 해당 API 를 호출하는 시점에 유저의 modFight 로그를 전달합니다.

해당 API 는 서버 스크립트에서만 유효합니다.

## 선언

NetworkUtility.SetBattleResult(int connectionId, string battleResult)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
|   **형식**   |      **파라미터**       |           **설명**            |
|:---:|:---:|:---------------------------:|
| int | connectionId |   타겟 클라이언트의 ConnectionID    | 
| string | battleResult | 라운드 결과에 대한 값 "win", "lost"  | 

---
## Sample Code
파티로얄 게임의 한 라운드 종료 시 해당 라운드에서 승리한 유저에겐 "win" 결과를, 패배한 유저들은 "lost" 결과를 전달합니다.
```lua
function this.OnRoundResult(winUsers, lostUsers)
    for i = 0, winUsers.Length - 1 do
        NetworkUtility.SetBattleResult(winUsers[i], "win")
    end
 
    for i = 0, lostUsers.Length - 1 do
        NetworkUtility.SetBattleResult(lostUsers[i], "lost")
    end
end
```