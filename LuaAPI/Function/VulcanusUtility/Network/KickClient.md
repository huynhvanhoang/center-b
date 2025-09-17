# KickClient

## 설명

해당 모드에서 필요한 인원이 모두 차서 게임을 시작한 후에 진입한 유저 같이, 특정 유저를 강제로 퇴장 시키고 싶을 때 호출합니다.

해당 API 는 서버 스크립트에서만 유효합니다.

## 선언

NetworkUtility.KickClient(int connectionId)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
|   **형식**   |      **파라미터**       |        **설명**         |
|:---:|:---:|:---------------------:|
| int | connectionId |타겟 클라이언트의 ConnectionID | 

---
## Sample Code
모드에서 설정한 최대 유저 수 까지 진입 대기 상태에서 일정 시간이 흐른 후 게임을 시작한 이후에 들어오는 유저들은 강제로 존에서 퇴장 시킵니다.
```lua
function this.Start()
   EventCenter.StartListenToEvent(this.OnClientJoined,typeof(ClientJoinedEvent))
end
 
function this.OnDestroy()
    EventCenter.StopListenToEvent(this.OnClientJoined,typeof(ClientJoinedEvent))
end
 
function this.OnClientJoined(event)
    if not NetworkUtility.IsServer() then return end
     
    if isGameStarted then
        NetworkUtility.KickClient(event.NewClient.ConnectionID)
    end
end
```