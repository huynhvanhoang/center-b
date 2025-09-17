# MatchAPIOpenDownloadConfirmUIEvent

## 설명
> Ugc 다운로드 여부 UI 열기

## 선언
> USGFramework.Runtime.Contents.Events.MatchAPIOpenDownloadConfirmUIEvent

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |
> Event함수들은 Start,OnDestroy 함수에서 등록과 해제를 해주어야 합니다.
> 해당 Event는 Client Logic에서만 사용 가능한 함수 입니다.

## Parameter
| **형식** | **파라미터** |         **설명**          |
|:------:|:--------:|:-----------------------:|
| string | ugcTitle |      다운로드 할 UGC 제목      |
| float  |  sizeMB  |    다운로드 할 UGC 사이즈 MB    |
| float  | duration |       다운로드 선택 시간        |
| string |  Ugcid   |      다운로드 할 UGC ID      |

## Sample Code
```lua
local EventCenter = nil
    function this.Start()
        EventCenter = USGFramework.Runtime.USGZone.EventCenter
        EventCenter.StartListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIOpenDownloadConfirmUIEvent))
    end
 
    function this.OnDestroy()
        EventCenter.StopListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIOpenDownloadConfirmUIEvent))
    end
 
    function this.EventFunction(ugcTitle,sizeMB,duration,ugcId)
        print("@ugcTitle :"..tostring(ugcTitle))
        print("@sizeMB :"..tostring(sizeMB))
        print("@duration :"..tostring(duration))
        print("@ugcId :"..tostring(ugcId))
    end
```


