# MatchAPIGoToMatchedZoneEvent

## 설명
매칭 완료 후 존 이동 시 발생되는 이벤트

## 선언
--함수의 네임스페이스

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Sample Code
```lua
--Call
    local EventCenter = nil
 
    function this.Start()
        EventCenter = USGFramework.Runtime.USGZone.EventCenter
        EventCenter.StartListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIGoToMatchedZoneEvent))
    end
 
    function this.OnDestroy()
        EventCenter.StopListenToEvent(this.EventFunction, typeof(USGFramework.Runtime.Contents.Events.MatchAPIGoToMatchedZoneEvent))
    end
 
    function this.EventFunction()
        print("@MatchAPIGoToMatchedZoneEvent")
    end
```