# CloseRoom

## 설명

해당 모드에 유저 진입을 막고 싶을 때 호출합니다. Room 이 Close 되면 더 이상 해당 모드에 진할 수 없게 됩니다.

해당 API 는 서버 스크립트에서만 유효합니다.

## 선언

NetworkUtility.CloseRoom()

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

---
## Sample Code
모드에서 설정한 최대 유저 수 까지 진입 대기 상태에서 일정 시간이 흐른 후 게임을 시작한 경우 CloseRoom API 를 호출 후 게임을 시작 합니다. 이 후 매칭 되는 유저, 혹은 이미 매칭 되서 진입 중이던 유저들은 존 진입에 실패합니다.
```lua
function this.Start()
   EventCenter.StartListenToEvent(this.OnClientJoined,typeof(ClientJoinedEvent))
end
 
function this.OnDestroy()
    EventCenter.StopListenToEvent(this.OnClientJoined,typeof(ClientJoinedEvent))
end
 
function this.OnClientJoined(event)
    if not NetworkUtility.IsServer() then return end
    userCount = userCount + 1
    if userCount >= kMaxUserCount then
        NetworkUtility.StopBackfill()
        NetworkUtility.CloseRoom()
    end
end
```