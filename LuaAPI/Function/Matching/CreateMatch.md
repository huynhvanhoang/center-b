# CreateMatch
## 설명
> 존 생성을 요청합니다.
## 선언
> USGFramework.Runtime.Contents.MatchAPI.CreateMatch
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
### Parameter
|              **형식**               | **파라미터** |   **설명**   |
|:---------------------------------:|:--------:|:----------:|
| [ReqCreateZone](ReqCreateZone.md) | ReqData  | 요청할 UGC 정보 |

## Sample Code
```lua

--Call
     function this.CallFunction()
      local _inputData = USGFramework.Runtime.Contents.APIDataStruct.ReqCreateZone.New()
      _inputData.UgcID ="1234567"
      _inputData.IsPrivate =false
      _inputData.CheckZone =false
 
      USGFramework.Runtime.Contents.MatchAPI.CreateMatch(_inputData)
    end
```

