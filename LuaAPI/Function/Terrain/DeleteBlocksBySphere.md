# DeleteBlocksBySphere

## 설명
지정된 구체 영역의 복셀을 삭제합니다. 호출자는 깨지기 쉬운 복셀만 삭제할지 선택할 수 있습니다

## 선언
TerrainServiceUtility.DeleteBlocksBySphere(Vector3 center, int radius, bool onlyBreakable = false)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
|       **형식**        |  **파라미터**  |   **설명**   |
|:-------------------:|:----------:|:----------:|
|Vector3 | center | 구체 위치 |
|int | radius | 구체 반경 |
|bool | onlyBreakable | (선택가능) 깨지기 쉬운 복셀만 삭제할지 여부 |

## Return
| **형식** | **파라미터** |                 **설명**                  |
|:------:|:--------:|:---------------------------------------:|
|  bool  | boolean  | 부울 값을 반환하여 메서드가 성공적으로 실행되었는지 호출자에게 알립니다 |


## Sample Code
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local sphereRadius = 5
 
function this.Update()
    if(Input.GetMouseButtonDown(0)) then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
         
        if flag then
            local pos = hit.point
            TerrainServiceUtility. DeleteBlocksBySphere (pos, sphereRadius)
        end
    end
end
```