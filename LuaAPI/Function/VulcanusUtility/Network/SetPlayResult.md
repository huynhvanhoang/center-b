# SetPlayResult

## 설명

해당 모드의 게임 결과를 설정합니다. 해당 API 를 호출 할 경우 유저가 모드를 나가는 시점에 모드 진행 시간 값과 같이 플레이 로그로 전달됩니다.

해당 API 는 서버 스크립트에서만 유효합니다.

## 선언

NetworkUtility.SetPlayResult(int connectionId, string playResult)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   |      **파라미터**       |           **설명**           |
|:---:|:---:|:--------------------------:|
| int | connectionId |   타겟 클라이언트의 ConnectionID   | 
| string | playResult | 게임 결과에 대한 값 "win", "lost"  | 

---
## Sample Code
파티로얄 게임의 모든 라운드 종료 후 최종 승리한 유저에겐 "win" 결과를, 패배한 유저들은 "lost" 결과를 전달합니다.
```lua
function this.OnPlayResult(winner)
    local clients = NetworkUtility.GetAllClientsInfo()
    for i = 0, clients.Length - 1 do
        if winner == clients[i].ConnectionID then
            NetworkUtility.SetPlayResult(winner, "win")
        else
            NetworkUtility.SetPlayResult(winner, "lost")
        end
    end
end
```