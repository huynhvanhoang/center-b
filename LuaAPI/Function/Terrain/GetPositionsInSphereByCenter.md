# GetPositionsInSphereByCenter

## 설명
지정된 구체 영역 내 모든 좌표를 가져와 해당 좌표를 호출자에게 반환합니다.

## 선언
TerrainServiceUtility.GetPositionsInSphereByCenter(Vector3 center, int radius)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   | **파라미터**  |             **설명**              |
|:----------:|:---------:|:-------------------------------:|
|  Vector3   |  center  |              구체 위치          |
|  int   |  radius   |             구체 반경            |

## Return
|  **형식**   | **파라미터**  |                    **설명**                     |
|:---------:|:---------:|:---------------------------------------------:|
| Vector3[] | Positions | 지정된 구체 영역의 모든 위치를 반환합니다 |


## Sample Code
클릭한 곳에서 반경이 5 인 구체 영역의 모든 위치를 획득한 후, Console 창에 개수를 출력합니다.
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local radius = 5
 
function this.Update()
    if(Input.GetMouseButtonDown(0))
    then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            local pos = hit.point
            local positions = TerrainServiceUtility.GetPositionsInSphereByCenter(pos,radius)
            if(positions == nil) then
                print('positions are null')
            else
                print('positions: ' .. positions.Length .. ' total')
            end
        end
    end
end

```