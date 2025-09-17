# MatchAPIFailMatchEvent

## 설명
> Ugc 매칭 실패 이벤트

## 선언
> USGFramework.Runtime.Contents.Events.MatchAPIFailMatchEvent

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |
> Event함수들은 Start,OnDestroy 함수에서 등록과 해제를 해주어야 합니다.
> 해당 Event는 Client Logic에서만 사용 가능한 함수 입니다.
---

## Sample Code
```lua
--Call
    local EventCenter = nil
 
    function this.Start()
        EventCenter = USGFramework.Runtime.USGZone.EventCenter
        EventCenter.StartListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIFailMatchEvent))
    end
 
    function this.OnDestroy()
        EventCenter.StopListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIFailMatchEvent))
    end
 
    function this.EventFunction()
        print("@MatchAPIFailMatchEvent")
    end
```


