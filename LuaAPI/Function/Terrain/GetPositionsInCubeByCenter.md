# GetPositionsInCubeByCenter

## 설명
지정된 입방체 영역 내 모든 좌표를 가져와 해당 좌표를 호출자에게 반환합니다

## 선언
TerrainServiceUtility.GetPositionsInCubeByCenter(Vector3 center, Vector3 size)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   | **파라미터**  |             **설명**              |
|:----------:|:---------:|:-------------------------------:|
|  Vector3   |  center  |              입장체 위치            |
|  Vector3   |  size   |             입방체 크기            |

## Return
|  **형식**   | **파라미터**  |                    **설명**                     |
|:---------:|:---------:|:---------------------------------------------:|
| Vector3[] | Positions | 지정된 입방체 영역의 모든 위치를 반환합니다 |


## Sample Code
클릭한 곳에서 크기가 10 인 입방체 영역의 모든 위치를 획득한 후, Console
창에 개수를 출력합니다.
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local cubeSize = UnityEngine.Vector3.one * 10

function this.Update()
    if(Input.GetMouseButtonDown(0)) then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
	
        if flag then
            local pos = hit.point
            local positions = TerrainServiceUtility.GetPositionsInCubeByCenter(pos,cubeSize)

            if(positions == nil)then
                print('positions are null')
            else
                print('positions: ' .. positions.Length .. ' total')
            end
        end
    end
end


```