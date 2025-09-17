# MatchAPIAdditionalWaitingEvent

## 설명
> Ugc 추가 모집 온/오프

## 선언
> USGFramework.Runtime.Contents.Events.MatchAPIAdditionalWaitingEvent

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |
> Event함수들은 Start,OnDestroy 함수에서 등록과 해제를 해주어야 합니다.
> 해당 Event는 Client Logic에서만 사용 가능한 함수 입니다.
---

## Parameter
| **형식** | **파라미터** |   **설명**   |
|:------:|:--------:|:----------:|
|  bool  | isActive | 추가 모집 온/오프 |

## Sample Code
```lua
--Call
   local EventCenter = nil
 
    function this.Start()
        EventCenter = USGFramework.Runtime.USGZone.EventCenter
        EventCenter.StartListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIAdditionalWaitingEvent))
    end
 
    function this.OnDestroy()
        EventCenter.StopListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIAdditionalWaitingEvent))
    end
 
    function this.EventFunction(isActive)
        print("@isActive :"..tostring(isActive))
    end
```
