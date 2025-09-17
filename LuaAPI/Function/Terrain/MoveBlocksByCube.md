# MoveBlocksByCube


## 설명
지정된 입방체 영역 내 복셀을 지정된 위치로 이동합니다.

## 선언
TerrainServiceUtility.MoveBlocksByCube(Vector3 center, Vector3 size, Vector3 direction, float speed)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
params 키워드를 사용하는 매개변수는 배열 유형에 직접 전달할 수 없습니다. 먼저 배열을 Table 로 변환한 다음 table.unpack 을
사용하여 매개변수를 전달하십시오.


## Parameter
| **형식**  | **파라미터**  |             **설명**              |
|:-------:|:---------:|:-------------------------------:|
| Vector3 |  center   |             입방체 위치              |
| Vector3 |   size    |             입장체 크기              |
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
local moveDirection = UnityEngine.Vector3.up * 10
local moveSpeed = 1
function this.Update()
    if(Input.GetMouseButtonDown(0)) then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            local pos = hit.point
            TerrainServiceUtility.MoveBlocks(moveDirection, moveSpeed, pos)
        end
    end
end
```