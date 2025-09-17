# Collect
## 설명
> 사용하지 않는 메모리 영역을 최적화 합니다.

## 선언
> USGFramework.Runtime.Contents.MemoryAPI.Collect

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Sample Code
```lua
--Call
   function this.Start()
        USGFramework.Runtime.Contents.MemoryAPI.Collect();
    end
```