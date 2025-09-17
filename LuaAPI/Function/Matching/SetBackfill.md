# SetBackfill

## 설명
> 호출 이후 요청 최대 시간까지 난입 요청을 허용합니다.

## 선언
>USGFramework.Runtime.Core.USGNetwork.NetworkUtility.SetBackfill

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```X```  |
| ```Server Logic``` |  ```O```  |
> CallBack이 호출되는 조건은 다음과 같습니다.
> 1. 요청한 인원 수 만큼의 인원이 모두 접속이 되었을 경우
> 2. 요청 최대 시간이 되었지만 난입 인원 수 만큼 들어 오지않았을 경우  
> CallBack이 호출된 후 난입은 종료 됩니다.
---

## Parameter
|  **형식**   |   **파라미터**   |           **설명**            |
|:---------:|:------------:|:---------------------------:|
| Function  |   Callback   | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
|    int    |  destCount   |           난입 인원수            |
|    int    | DurationSecs |          요청 최대 시간           |

## Return
| **형식** | **파라미터** | **설명** |
|:------:|:--------:|:------:|
|  bool  |  Result  |  성공여부  |

## CallBack
| **형식** |   **파라미터**    |  **설명**   |
|:------:|:-------------:|:---------:|
|  int   |  ResultCode   | 호출 결과 코드  |
| string | ResultMessage | 호출 결과 메세지 |c
|  int   |   UserCount   | 난입한 유저 수  |

## Sample Code
```lua
--Call
  function this.SetBackfill()
     local _TestBool = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.SetBackfill(this.CallBack_Backfill,2,30)
  end
```
```lua
--CallBack
function this.CallBack_Backfill(Code,MSG,UserCount)
        print("Code :"..tostring(Code)..",MSG :"..tostring(MSG)..",UserCount :"..tostring(UserCount))
end
```