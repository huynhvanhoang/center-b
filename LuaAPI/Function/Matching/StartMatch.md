# StartMatch

## 설명
> 일반 매칭을 시작합니다.

## 선언
> USGFramework.Runtime.Contents.MatchAPI.StartMatch

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |

## Parameter
|              **형식**               | **파라미터** | **설명** |
|:---------------------------------:|:--------:|:------:|
| [ReqStartMatch](ReqStartMatch.md) | ReqData  | 매칭 정보  |

## Sample Code
```lua
--Call
  function this.CallFunction()
      local UgcID = "1234567"
      local CheckZone = false
 
      local _InputData = USGFramework.Runtime.Contents.APIDataStruct.ReqStartMatch.New()
      _InputData.UgcID = UgcID
      _InputData.CheckZone = CheckZone
 
      USGFramework.Runtime.Contents.MatchAPI.StartMatch(_InputData)
  end
```
