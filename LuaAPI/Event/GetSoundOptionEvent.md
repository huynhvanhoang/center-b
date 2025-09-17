# GetSoundOptionEvent

## 설명
> 사운드 옵션이 변경되면 발생하는 이벤트

## 선언
> USGFramework.Runtime.Contents.Events.GetSoundOptionEvent

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
| float  | SoundVol | 사운드 볼륨 |
|  bool  |   Mute   | 음속어 여부 |

## Sample Code
```lua
--Call
   local EventCenter = nil
 
   function this.Start()
       EventCenter = USGFramework.Runtime.USGZone.EventCenter
       EventCenter.StartListenToEvent(this.OnGetSoundOptionEvent, typeof(USGFramework.Runtime.Contents.Events.GetSoundOptionEvent))
   end
 
   function this.OnDestroy()
       EventCenter.StopListenToEvent(this.OnGetSoundOptionEvent, typeof(USGFramework.Runtime.Contents.Events.GetSoundOptionEvent))
   end
 
   function this.OnGetSoundOptionEvent(Event)
         local Vol = Event.SoundVol
         local Mute = Event.Mute
   
         print("Vol :"..tostring(Vol).."Mute :"..tostring(Mute))
   end
```
