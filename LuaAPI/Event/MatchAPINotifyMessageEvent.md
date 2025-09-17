# MatchAPINotifyMessageEvent

## 설명
> 알림 메세지 이벤트

## 선언
> 매칭 진행 중 유저가 존 이동을 요청했을때 선택 결과

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |
> Event함수들은 Start,OnDestroy 함수에서 등록과 해제를 해주어야 합니다.
> 해당 Event는 Client Logic에서만 사용 가능한 함수 입니다.

## Parameter
| **형식** | **파라미터** |  **설명**   |
|:------:|:--------:|:---------:|
| string | message  |  알림 메세지   |

---

## Sample Code
```lua
--Call
    local EventCenter = nil
 
    function this.Start()
        EventCenter = USGFramework.Runtime.USGZone.EventCenter
        EventCenter.StartListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPINotifyMessageEvent))
    end
 
    function this.OnDestroy()
        EventCenter.StopListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPINotifyMessageEvent))
    end
 
    function this.EventFunction(message)
        print("@message :"..tostring(message))
    end
```
