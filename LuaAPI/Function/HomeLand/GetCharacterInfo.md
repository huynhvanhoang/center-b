# GetCharacterInfo

## 설명
> 현재 존에 접속한 특정 유저의 캐릭터 정보를 획득합니다.

## 선언
> USGFramework.Runtime.Core.USGNetwork.NetworkUtility

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |

## Parameter
| **형식** |      **파라미터**      |      **설명**       |
|:------:|:------------------:|:-----------------:|
|  int   |    ConnectionID    | 획득 하려는 유저의 커넥션 ID |

## Return
|              **형식**               |   **파라미터**    |   **설명**   |
|:---------------------------------:|:-------------:|:----------:|
| [CharacterInfo](CharacterInfo.md) | CharacterInfo | 유저의 캐릭터 정보 |

## Sample Code
```lua
function this.GetCharacterInfo()
        local Clients = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetAllClientsInfo()
        for i = 0, Clients.Length-1 do
            print("ConnectionID :"..tostring(Clients[i].ConnectionID))
 
            local CharacterInfo = USGFramework.Runtime.Core.USGNetwork.NetworkUtility.GetCharacterInfo(Clients[i].ConnectionID)
            if GetCharacterInfo then
                print("CharacterInfo".. CharacterInfo.Nicname..","..CharacterInfo.Gender)
            end
        end
 end
```