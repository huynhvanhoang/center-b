# Terrain
## 소개

터레인 API 는 구현 효과에 따라 복셀 추가, 복셀 삭제, 복셀 이동, 좌표 가져오기, 복셀 가져오기 등 다섯 가지 API 로 분류됩니다

### 사용 시 주의사항

Terrain API를 사용하려면 아래와 같이 Lua 스크립트에 TerrainServiceUtility를 등록해야 합니다

```Lua
local TerrainServiceUtility = USGFramework.Runtime.USGVoxelTerrain.ServiceFunctions.TerrainServiceUtility
```

| API Function Name                         | Functional Description                                                                                             |
|-------------------------------------------|--------------------------------------------------------------------------------------------------------------------|
| [AddBlocks](AddBlocks.md)                 | 지정된 위치에 복셀을 추가합니다                                                                                                  |
| [AddBlocksByCube](AddBlocksByCube.md)     | 	지정된 입방체 영역에 복셀을 추가합니다                                                                                             |
| [AddBlocksBySphere](AddBlocksBySphere.md) | 지정된 구체 영역에 복셀을 추가합니다.                                                                                              |
| [AddBlocksByAABB](AddBlocksByAABB.md)     | 호출자가 대각선의 두 점을 지정하면, 이 함수는 입방체 영역을 생성한 후, 이 영역에 복셀을 추가합니다. Ps: AABB 는 축이 정렬된 경계 상자입니다. (Axis-Aligned Bounding Box) |

| API Function Name                                         | Functional Description                                                                    |
|-----------------------------------------------------------|-------------------------------------------------------------------------------------------|
| [DeleteBlocks](DeleteBlocks.md)                           | 지정된 위치의 복셀을 삭제합니다.                                                                        |
| [DeleteOnlyBreakableBlocks](DeleteOnlyBreakableBlocks.md) | 	지정된 위치에서 깨지기 쉬운 복셀만 삭제합니다                                                                |
| [DeleteBlocksByCube](DeleteBlocksByCube.md)               | 지정된 입방체 영역의 복셀을 삭제합니다. 호출자는 깨지기 쉬운 복셀만 삭제할지 선택할 수 있습니다.                                   |
| [DeleteBlocksBySphere](DeleteBlocksBySphere.md)           | 지정된 구체 영역의 복셀을 삭제합니다. 호출자는 깨지기 쉬운 복셀만 삭제할지 선택할 수 있습니다.                                    |
| [DeleteBlocksByAABB](DeleteBlocksByAABB.md)               | 호출자가 대각선의 두 점을 지정하면 이 함수는 입방체 영역을 생성한 후, 이 영역의 복셀을 삭제합니다. 호출자는 깨지기 쉬운 복셀만 삭제할지 선택할 수 있습니다 |


| API Function Name                           | Functional Description                                     |
|---------------------------------------------|------------------------------------------------------------|
| [MoveBlocks](MoveBlocks.md)                 | 복셀을 지정된 위치로 이동합니다.                                         |
| [MoveBlocksByCube](MoveBlocksByCube.md)     | 지정된 입방체 영역 내 복셀을 지정된 위치로 이동합니다.                            |
| [MoveBlocksBySphere](MoveBlocksBySphere.md) | 지정된 구체 영역 내 복셀을 지정된 위치로 이동합니다.                             |
| [MoveBlocksByAABB](MoveBlocksByAABB.md)     | 지정된 AABB(Axis-Aligned Bounding Box) 영역 내 복셀을 지정된 위치로 이동합니다 |

| API Function Name                                               | Functional Description                     |
|-----------------------------------------------------------------|---------------------------------|
| [GetPositionsInCubeByCenter](GetPositionsInCubeByCenter.md)     | 지정된 입방체 영역 내 모든 좌표를 가져와 해당 좌표를 호출자에게 반환합니다|
| [GetPositionsInSphereByCenter](GetPositionsInSphereByCenter.md) | 지정된 구체 영역 내 모든 좌표를 가져와 해당 좌표를 호출자에게 반환합니다.|
| [GetPositionsInCubeByAABB](GetPositionsInCubeByAABB.md)           | 지정된 AABB 영역 내 모든 좌표를 가져와 이 좌표를 호출자에게 반환합니다 |

| API Function Name                                       | Functional Description                     |
|---------------------------------------------------------|---------------------------------|
| [GetBlockAssetByPositions](GetBlockAssetByPositions.md) | 위치 컬렉션을 검색하여 해당 컬렉션에 포함된 복셀과 위치 정보를 호출자에게 반환합니다.|
| [GetBreakablePositions](GetBreakablePositions.md)       | 위치 컬렉션을 검색하여 해당 컬렉션에 포함된 깨지기 쉬운 복셀과 위치 정보를 호출자에게 반환합니다 |

LuaManager 를 초기화하는 데는 시간이 걸리기 때문에, 터레인 API 와 네트워크 생성 기능이 정상적으로 실행될 수 있도록 Awake 와 Start 에 작성하지 말고 이벤트를 사용하거나 Input 트리거를 감지할 수 있도록 Update 에 작성해야 합니다.
