# GetValue
## 설명
--주어진 행과 열 이름으로 데이터를 가져옵니다.

## 선언
--DataSheet:GetValue (int rowNumber, string columnName)  
[사용법은 다음 링크를 통해 확인](DataSheet.md)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

--추가 주의사항 
## Parameter
|   **형식**   | **파라미터** |    **설명**    |
|:----------:|:--------:|:------------:|
| RowNumber  |   int    | 얻을 데이터의 행의 수 | 
| ColumnName |   int    | 얻을 데이터의 열의 수 | 

## Return
| **형식** | **파라미터** |      **설명**       |
|:------:|:--------:|:-----------------:|
| Object |  Value   | 검색 또는 요청된 데이터를 반환 |

## SampleCode

```lua
LuaDataSheetTest = {}
 
function LuaDataSheetTest.GetTable()
    local this = {}
    local GameObject = UnityEngine.GameObject
    local thisGameObject
    local thisLuaComponent
    local thisTransform
    local UnityDataSheetOre=USGFramework.Runtime.USGAsset.UnityDataSheetOre
    local KeyCode=UnityEngine.KeyCode
    local Input=UnityEngine.Input
    local dataSheet
    local rowIndex=0
    local columName='Prefab'
    local value
    local VectorX='VectorX'
    local VectorY='VectorY'
    local VectorZ='VectorZ'
    local position
    local object
 
     
    -- Awake
    function this.Awake(luaComponentInfo)
        thisGameObject = luaComponentInfo.TargetGameObject   
        thisTransform = luaComponentInfo.TargetTransform
        thisLuaComponent = luaComponentInfo.Owner  
    end
     
    -- Start is called before the first frame update
    function this.Start()
        dataSheet = thisLuaComponent:GetUnityObjectPropertyValueByIndex(0).UnityObject
         
    end
     
    -- Update is called once per frame
    function this.Update()
        if (Input.GetKeyDown(KeyCode.Space)) then
 
            if(object ~= nil)then
                GameObject.Destroy(object)
            end
 
            value = dataSheet:GetValue(rowIndex, 'Prefab')
            this.GetPositon(rowIndex)
            object = GameObject.Instantiate(value, position, Quaternion.identity)
        end
 
        if(Input.GetKeyDown(KeyCode.E)) then
            rowIndex = rowIndex + 1
            rowIndex = rowIndex % 3
        end
    end
     
    function this.GetPositon(index)
        local Vector3X = dataSheet:GetValue(index, 'VectorX')
        local Vector3Y = dataSheet:GetValue(index, 'VectorY')
        local Vector3Z = dataSheet:GetValue(index, 'VectorZ')
        position = Vector3(Vector3X, Vector3Y, Vector3Z)
    end
 
    return this
end
```