# GetAllClientsInfo

## 설명
> 현재 존에 접속한 모든 유저의 ConnectionID 정보를 획득합니다.

## 선언
> USGFramework.Runtime.Core.USGNetwork.NetworkUtility

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |

## Return
|           **형식**            |  **파라미터**  | **설명** |
|:---------------------------:|:----------:|:------:|
| [ClientInfo](ClientInfo.md) | ClientInfo | 유저 정보  |

## Sample Code
```lua
--Call
function this.GetAllClientsInfo()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        for i = 0, Clients.Length-1 do
            print("ConnectionID :"..tostring(Clients[i].ConnectionID))
        end
 end
```
