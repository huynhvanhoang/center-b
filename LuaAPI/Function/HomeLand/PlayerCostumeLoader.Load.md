# PlayerCostumeLoader.Load

## 설명
> 캐릭터 유료 의상 외형 정보 동기화

## 선언
> USGFramework.Runtime.Contents.PlayerCostumeLoader

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |


## Parameter
|   **형식**   |     **파라미터**     |      **설명**      |
|:----------:|:----------------:|:----------------:|
|    int     | thisConnectionID | 유저의 ConnectionID |
| GameObject |  currentPlayer   |    동기화 될 오브젝트    |

## Sample Code
```lua
    Test = {}
    
    function Test.GetTable()
    local this = {}
    local GameObject = UnityEngine.GameObject
    local thisGameObject
    local thisLuaComponent
    local thisTransform

    local Str = ""
    local Log = nil
    local ButtonList
    
    -- Awake
    function this.Awake(luaComponentInfo)
        thisGameObject = luaComponentInfo.TargetGameObject    
        thisTransform = luaComponentInfo.TargetTransform
        thisLuaComponent = luaComponentInfo.Owner   
    end
    
    -- Start
    function this.Start()
        this.CallPlayerCostumeLoader()
    end
    
    function this.CallPlayerCostumeLoader()
        local ConnectionID = ThisConnectionID
        USGFramework.Runtime.Contents.PlayerCostumeLoader.Load(ConnectionID,thisGameObject)
    end
    
    return this
end
```
