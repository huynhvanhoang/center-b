# Destroy

## 설명

네트워크 오브젝트를 소멸시킵니다. (참고: NetworkUtility.Destroy 는NetworkUtility.Instantiate 를 사용하여 생성한 네트워크 오브젝트만 소멸시킬 수 있습니다.

로컬 오브젝트를 소멸시켜야 하는 경우 UnityEngine.GameObject.Destroy 를 사용하시기 바랍니다.)



## 선언

NetworkUtility.Destroy(GameObject gameObject)

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
스크립트를 빈 오브젝트에 나누어 마운트한 후 Space 키를 누르면 네트워크 오브젝트를 생성하며, 다시 한 번 누르면 이 오브젝트를 소멸시킵니다. 이 작업은 모든 클라이언트 시스템에 동기화됩니다
![](media/images/LuaNetwork_1.png)

## Parameter
|   **형식**   |      **파라미터**       |   **설명**   |
|:---:|:---:|:---:|
| GameObject | GameObject | 소멸시킬 오브젝트 | 

## Return
|**형식**| **파라미터** |**설명**|
|:---:|:--------:|:---:|
|Boolean |  Result  | 부울 값을 반환하여 메서드가 성공적으로 실행되었는지 호출자에게 알립니다 |

---
## Sample Code

```lua
local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
local Input = UnityEngine.Input
local currentGameObject
local currentPrefab
 
function this.Start()
    currentPrefab = thisLuaComponent:GetUnityObjectPropertyValueByName("Prefab").UnityObject
end
 
function this.Update()
    if Input.GetKeyDown("space") then
        if currentGameObject == nil then
            NetworkUtility.Instantiate(currentPrefab, Vector3(0, 3, 0), Quaternion.identity, this.OnObjectSpawned)
        else
            NetworkUtility.Destroy(currentGameObject)
            currentGameObject = nil
        end
    end
end
 
function this.OnObjectSpawned(spawnedObject)
    currentGameObject = spawnedObject;
    print('OnObjectSpawned ' .. currentGameObject.name);
end
```