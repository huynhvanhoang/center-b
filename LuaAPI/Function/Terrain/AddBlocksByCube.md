# AddBlocksByCube

## 설명
지정된 입방체 영역에 복셀을 추가합니다.


## 선언
TerrainServiceUtility. AddBlocksByCube (UnityVoxelBlockBase blockAsset, Vector3 center, Vector3 size)
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

클릭한 위치에서 크기가 10x10x10 인 입방체 영역에 복셀을 추가합니다.
먼저, Lua Behaviour 컴포넌트에 복셀 리소스를 추가합니다

터레인 API 를 사용하기 위해 TerrainServiceUtility 를 바인딩해야 하며, 사용자 입력을 감지하려면 UnityEngine.Input 을 바인딩해야 합니다.
UnityEngine.KeyCode(키보드 입력 감지가 필요할 시 등록)
![](media/images/Terrain_1.png)

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:----------:|:-------------------:|:----------:|
| UnityVoxelBlockBase | blockAsset | 추가해야 하는 복셀 |
| Vector3 |center | 입방체 위치 |
| Vector3 |size | 입방체 크기 |

## Return
|     **형식**     |  **파라미터**   |                **설명**                |
|:--------------:|:-----------:|:------------------------------------:|
|bool |boolean | 	부울 값을 반환하여 메서드가 성공적으로 실행되었는지 호출자에게 알립니다|

---
## Sample Code
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local blockAsset
local cubeSize = UnityEngine.Vector3.one * 10
 
function this.Start()
    blockAsset = thisLuaComponent:GetUnityObjectPropertyValueByIndex(0).UnityObject
end
 
function this.Update()
    if(Input.GetMouseButtonDown(0))
    then
        local camera = UnityEngine.Camera.main
        local ray  = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            local pos = hit.point
            TerrainServiceUtility.AddBlocksByCube(blockAsset, pos, cubeSize)
        end
    end
end
```