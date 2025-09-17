# GetBreakablePositions

## 설명
위치 컬렉션을 검색하여 해당 컬렉션에 포함된 깨지기 쉬운 복셀과 위치 정보를 호출자에게 반환합니다.

## 선언
TerrainServiceUtility.GetBreakablePositions(params Vector3[] positions)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
params 키워드를 사용하는 매개변수는 배열 유형에 직접 전달할 수 없습니다. 먼저 배열을 Table 로 변환한
다음 table.unpack 을 사용하여 매개변수를 전달하십시오.


## Parameter
| **형식**  |  **파라미터**   |      **설명**      |
|:-------:|:-----------:|:----------------:|
| Vector3[] | positions | 검색이 필요한 위치 |

## Return
|  **형식**   | **파라미터**  |                   **설명**                    |
|:---------:|:---------:|:-------------------------------------------:|
| Vector3[] | Positions |   깨지기 쉬운 복셀의 위치 정보를 포함한 vector3 배열을반환합니다.   |


## Sample Code
지정된 입방체 영역 내의 깨지기 쉬운 모든 복셀을 가져와 Console 창에 정보를 출력합니다
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
local cubeSize = UnityEngine.Vector3.one * 10
 
function this.Update()
    if(Input.GetMouseButtonDown(0))
    then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag then
            local pos = hit.point
            local positions = TerrainServiceUtility.GetPositionsInCubeByCenter(pos,cubeSize)
            local tb = {}
 
            for i = 0, positions.Length - 1 do
                table.insert(tb, positions[i])
            end
 
            local blockInfos = TerrainServiceUtility.GetBreakablePositions (table.unpack(tb))
            for i = 0, blockInfos.Length - 1 do
                if blockInfos[i] == nil then
                    print('no blocks')
                else
                    print('block position: ' .. blockInfos[i].x .. “,” .. blockInfos[i].y .. “,” .. blockInfos[i].z)
                end
            end
        end
    end
end

```