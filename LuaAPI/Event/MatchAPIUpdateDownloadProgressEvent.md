# MatchAPIUpdateDownloadProgressEvent

## 설명
> Ugc 다운로드 진행 UI 갱신

## 선언
> USGFramework.Runtime.Contents.Events.MatchAPIUpdateDownloadProgressEvent

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |
> Event함수들은 Start,OnDestroy 함수에서 등록과 해제를 해주어야 합니다.
> 해당 Event는 Client Logic에서만 사용 가능한 함수 입니다.

## Parameter
| **형식** |  **파라미터**  |     **설명**     |
|:------:|:----------:|:--------------:|
| string |   ugcId    | 다운로드 진행 UGC ID |
| ulong  | currBytes  | 다운로드 진행된 bytes |
| ulong  | totalBytes |  다운로드 총 bytes  |

---
## Sample Code
```lua
--Call
    local EventCenter = nil
 
    function this.Start()
        EventCenter = USGFramework.Runtime.USGZone.EventCenter
        EventCenter.StartListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIUpdateDownloadProgressEvent))
    end
 
    function this.OnDestroy()
        EventCenter.StopListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIUpdateDownloadProgressEvent))
    end
 
    function this.EventFunction(ugcId,currBytes,totalBytes)
        print("@ugcId :"..tostring(ugcId))
        print("@currBytes :"..tostring(currBytes))
        print("@totalBytes :"..tostring(totalBytes))
    end
```
