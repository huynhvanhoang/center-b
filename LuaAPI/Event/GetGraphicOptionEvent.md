# GetGraphicOptionEvent

## 설명
> 그래픽 옵션이 변경되면 발생하는 이벤트

## 선언
> USGFramework.Runtime.Contents.Events.GetGraphicOptionEvent

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |
> Event함수들은 Start,OnDestroy 함수에서 등록과 해제를 해주어야 합니다.
> 해당 Event는 Client Logic에서만 사용 가능한 함수 입니다.
---

## Parameter
| **형식** | **파라미터** | **설명** |
|:------:|:--------:|:------:|
|  int   |  Option  | 그래픽 옵션 |

## Sample Code
```lua
--Call
   local EventCenter = nil
 
     function this.Start()
        EventCenter = USGFramework.Runtime.USGZone.EventCenter
        EventCenter.StartListenToEvent(this.OnGetGraphicOptionEvent, typeof(USGFramework.Runtime.Contents.Events.GetGraphicOptionEvent))
    end
 
    function this.OnDestroy()
        EventCenter.StopListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.GetGraphicOptionEvent))
    end
 
  function OnGetGraphicOptionEvent(Event)
        print("@EventGraphicOption :"..tostring(Event.Option))
 end
```
