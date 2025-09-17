# GetPositionsInCubeByAABB

## 설명
지정된 AABB 영역 내 모든 좌표를 가져와 이 좌표를 호출자에게 반환합니다.

## 선언
TerrainServiceUtility.GetPositionsInCubeByAABB(Vector3 minPosition, Vector3 maxPosition)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
| **형식**  |  **파라미터**   |      **설명**      |
|:-------:|:-----------:|:----------------:|
| Vector3 | minPosition | 바운딩 박스의 최소 위치box |
| Vector3 | maxPosition | 바운딩 박스의 최대 위치box |

## Return
|  **형식**   | **파라미터**  |                    **설명**                     |
|:---------:|:---------:|:---------------------------------------------:|
| Vector3[] | Positions |바운딩 박스에 있는 모든 위치를 반환합니다|


## Sample Code
마우스 클릭으로 상자영역의 모든 위치를 가져온후 콘솔창에 개수를 출력.
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local direction = UnityEngine.Vector3.up * 10
local speed = 1
 
function this.Update()
    if (Input.GetMouseButtonDown(0))
    then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            local pos = hit.point
            local mixPos= pos - hit.normal * 10
            local maxPos= pos + hit.normal * 10
            local positions = TerrainServiceUtility. GetPositionsInCubeByAABB(mixPos, maxPos)
            if(positions == nil) then
                print('positions are null')
            else
                print('positions: ' .. positions.Length .. ' total')
            end
        end
    end
end

```