# print
## 설명
> Vulcanus Editor에 로그를 남기기 위해 사용합니다.

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |


## Parameter
| **형식** | **파라미터** |   **설명**   |
|:------:|:--------:|:----------:|
| string |   STR    | 로그로 남길 문자열 |

## Sample Code
```lua
function this.Start()
        ---------------------
        print("Test Code")
        ---------------------
        local STR = "TestCode"
        print(STR)
        ---------------------
        local Number = 10
        print(tostring(Number))
        ---------------------
        print("Sum".."Sum")
        ---------------------
        local day = 7
        local month = 8
        local year = 2024 
        print(string.format("%02d/%02d/%02d",day,month,year))
    end
```
