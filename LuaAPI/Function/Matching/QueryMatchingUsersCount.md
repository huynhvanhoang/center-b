# QueryMatchingUsersCount

## 설명
> 현재 존에 매칭된 유저 수를 획득합니다.

## 선언
> USGFramework.Runtime.Core.USGNetwork.NetworkUtility.QueryMatchingUsersCount

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
## Parameter
|  **형식**  | **파라미터** |           **설명**            |
|:--------:|:--------:|:---------------------------:|
| Function | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |

## Callback
| **형식** |      **파라미터**       |           **설명**            |
|:------:|:-------------------:|:---------------------------:|
|  int   |  enteredUsersCount  |    현재 존에 매칭되어 진입 한 유저 수     |
|  int   | reservedUsersCount  | 현재 존에 매칭 예약되어 앞으로 진입 할 유저 수 |

## Sample Code
```lua
--Call
 function this.Start()
        NetworkUtility.QueryMatchingUsersCount(this.OnCallbackMatchingUsersCount)
 end
```
```lua
--CallBack
function this.OnCallbackMatchingUsersCount(enteredUsersCount, reservedUsersCount)
    print("OnCallbackMatchingUsersCount " .. tostring(enteredUsersCount) .. ', ' .. tostring(reservedUsersCount))
end
```