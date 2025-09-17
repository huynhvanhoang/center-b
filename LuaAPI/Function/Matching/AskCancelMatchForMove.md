# AskCancelMatchForMove

## 설명
> 매칭 중 존이동 등을 문의 할때 이용, 매칭 취소 여부를 묻고, 결과를 MatchAPICancelMatchForMoveEvent 이벤트로 알림

## 선언
> USGFramework.Runtime.Contents.MatchAPI.AskCancelMatchForMove()


## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
## Sample Code
```lua
--Call
   function this.CallFunction()
      USGFramework.Runtime.Contents.MatchAPI.AskCancelMatchForMove()
    end
```