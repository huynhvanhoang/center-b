# MoveBlocksBySphere

## 설명
지정된 구체 영역 내 복셀을 지정된 위치로 이동합니다.

## 선언
TerrainServiceUtility.MoveBlocksBySphere(Vector3 center, int radius, Vector3 direction, float speed)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
| **형식**  | **파라미터**  |             **설명**              |
|:-------:|:---------:|:-------------------------------:|
| Vector3 |  center   |              구체 위치              |
|   int   |  radius   |              구체 반경              |
| Vector3 | direction | 목적지(Vector3 구조는 방향과 크기의 벡터를 포함) |
|  float  |   speed   |              이동 속도              |

## Return
| **형식** | **파라미터** |                    **설명**                     |
|:------:|:--------:|:---------------------------------------------:|
|  bool  | boolean  | 메서드가 성공적으로 실행되었는지 여부를 호출자에게 알려주는 Bool값을 반환합니다 |


## Sample Code
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local sphereRadius = 5
local direction = UnityEngine.Vector3.up * 10
local speed = 1
 
function this.Update()
    if(Input.GetMouseButtonDown(0)) then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            local pos = hit.point
            TerrainServiceUtility. MoveBlocksBySphere(pos, sphereRadius, direction, speed)
        end
    end
end
```