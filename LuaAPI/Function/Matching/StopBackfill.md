# StopBackfill

## 설명
> [SetBackfill](SetBackfill.md) 함수로 난입을 허용하는 도중 난입을 멈추는 함수입니다.

## 선언
> USGFramework.Runtime.Core.USGNetwork.NetworkUtility.StopBackfill

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```X```  |
| ```Server Logic``` |  ```O```  |
> [SetBackfill](SetBackfill.md) 함수로 난입이 허용될 때만 동작합니다
---

## Sample Code
```lua
--Call
function this.StopBackfill()
  USGFramework.Runtime.Core.USGNetwork.NetworkUtility.StopBackfill()
end
```

