# Teleport

## 설명

게임 오브젝트의 Transform을 특정 좌표로 텔레포트(강제이동) 시킵니다.

이동시 보간(snapshot) 정보를 초기화 합니다.

## 선언

NetworkUtility.Teleport(Transform transform, Vector3 position, Quaternion quaternion, string payload = "")

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

추가 주의사항 

//이미지는 이렇게!!!()
![](media/images/Terrain_1.png)

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| Transform | transform | 이동 시키려는 GameObject의 Root Transform | 
| Vector3 | position | 이동 시키려는 world Position | 
| Quaternion | quaternion | 이동 후 회전 방향. | 
| string | payload | 이동 후 콜백으로 받을 추가 정보. | 

## Return
|**형식**| **파라미터** |                                                   **설명**                                                    |
|:---:|:--------:|:-----------------------------------------------------------------------------------------------------------:|
|Boolean |  Result  | 존 서버로 Teleport 요청 여부를 나타내는 bool 값을 반환합니다  true : 존 서버로 Teleport 요청 전송 완료.  false : 존 서버로 Teleport 요청 전송 실패. |

---
## Sample Code
지정된 좌표와 방향으로 이동합니다.
```lua
local thisTransform
 
function this.Awake(luaComponentInfo)
    thisTransform = luaComponentInfo.TargetTransform
end
 
function this.Teleport(position, rotation)
    local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
    local sendSuccess = NetworkUtility.Teleport(thisTransform, position, rotation)
end
```