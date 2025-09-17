# GetBlockAssetByPositions

## 설명
위치 컬렉션을 검색하여 해당 컬렉션에 포함된 복셀과 위치 정보를 호출자에게 반환합니다.

## 선언
TerrainServiceUtility.GetBlockAssetByPositions(params Vector3[] positions)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
params 키워드를 사용하는 매개변수는 배열 유형에 직접 전달할 수 없습니다. 먼저 배열을 Table 로 변환한
다음 table.unpack 을 사용하여 매개변수를 전달하십시오


## Parameter
| **형식**  |  **파라미터**   |      **설명**      |
|:-------:|:-----------:|:----------------:|
| Vector3[] | positions | 검색이 필요한 위치 |

## Return
|  **형식**   | **파라미터**  |                    **설명**                    |
|:---------:|:---------:|:--------------------------------------------:|
| KeyValuePair<Vector3,UnityVoxelBlockBase>[] | Positions | 복셀과 그 위치를 포함하는 키-값 쌍 배율을 반환합니다(키: 위치, 값: 복셀) |


## Sample Code
클릭한 위치의 복셀을 가져와 Console 창에 정보를 출력합니다.
```lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
local Input = UnityEngine.Input
 
function this.Update()
    if(Input.GetMouseButtonDown(0))
    then
        local camera = UnityEngine.Camera.main
        local ray = camera:ScreenPointToRay(Input.mousePosition)
        local flag, hit = UnityEngine.Physics.Raycast(ray, nil, 5000)
        if flag
        then
            local pos = hit.point
            local blockInfos = TerrainServiceUtility. GetBlockAssetByPositions(pos)
 
            for i = 0, blockInfos.Length - 1 do
                if(blockInfos[i].Value == nil) then
                    print('no blocks')
                else
                    print('block name: ' .. blockInfos[i].Value.name)
                end
            end
        end
    end
end

```