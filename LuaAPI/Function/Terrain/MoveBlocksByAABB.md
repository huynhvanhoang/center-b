# MoveBlocksByAABB

## 설명
지정된 AABB(Axis-Aligned Bounding Box) 영역 내 복셀을 지정된 위치로 이동합니다.

## 선언
TerrainServiceUtility.MoveBlocksByAABB(Vector3 minPosition, Vector3 maxPosition, Vector3 direction, float speed)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
|   **형식**   | **파라미터**  |             **설명**              |
|:----------:|:---------:|:-------------------------------:|
|  Vector3   |  minPosition   |              바운딩 박스의 최소 위치            |
|  Vector3   |  maxPosition   |              바운딩 박스의 최대 위치            |
|  Vector3   | direction | 목적지(Vector3 구조는 방향과 크기의 벡터를 포함) |
|   float    |   speed   |              이동 속도              |

## Return
| **형식** | **파라미터** |                    **설명**                     |
|:------:|:--------:|:---------------------------------------------:|
|  bool  | boolean  | 부울 값을 반환하여 메서드가 성공적으로 실행되었는지 호출자에게 알립니다 |


## Sample Code
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local direction = UnityEngine.Vector3.up * 10
local speed = 1
 
function this.Update()
    if (Input.GetMouseButtonDown(0)) then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            local pos = hit.point
            local mixPos= pos - hit.normal * 10
            local maxPos= pos + hit.normal * 10
            TerrainServiceUtility.MoveBlocksByAABB(mixPos, maxPos,direction,speed)
        end
    end
end
```