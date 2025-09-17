# IsMatching
## 설명
> 현재 매칭중인지에 대한 여부를 반환 하는 함수입니다.
## 선언
> USGFramework.Runtime.Contents.MatchAPI.IsMatching()
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |

### Return
| **형식** | **파라미터** |  **설명**  |
|:------:|:--------:|:--------:|
|  bool  |  Output  | 매칭 여부 체크 |

## Sample Code
```lua
--Call
  function this.CallFunction()
       local OutPut = USGFramework.Runtime.Contents.MatchAPI.IsMatching()
  end
```