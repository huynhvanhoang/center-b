# Network Lua

## 소개
네트워크 API 는 현지 클라이언트와 서버의 상호 작용을 만들어 내고, 네트워크 이벤트를 발신하며, 네트워크 오브젝트를 생성하거나 소멸시킵니다. 또한 네트워크 오브젝트의 소유권을 판단하고 획득하거나, 네트워크 오브젝트 소유자의 ID 를 획득하며 RPC 기능을 수행합니다
## 사용시 주의 사항
 *  네트워크 API 를 사용해야 하는 경우 Lua 스크립트에 NetworkUtility 를 바인딩해야 하며
```lua
  local NetworkUtility= USGFramework.Runtime.Core.USGNetwork.NetworkUtility 
```
 * 네트워크 이벤트를 사용하려면 Lua 스크립트에 EventCenter 클래스를 등록해야 합니다. ClientInfoAssignedEvent 이벤트, ClientJoinedEvent 이벤트, ClientDisconnectedEvent 이벤트는 다음과 같이 작성됩니다.
```lua
local EventCenter = USGFramework.Runtime.USGZone.EventCenter
 
local ClientInfoAssignedEvent = USGFramework.Runtime.Core.USGNetwork.Events.ClientInfoAssignedEvent
 
local ClientJoinedEvent = USGFramework.Runtime.Core.USGNetwork.Events.ClientJoinedEvent
 
local ClientDisconnectedEvent = USGFramework.Runtime.Core.USGNetwork.Events.ClientDisconnectedEvent
```
 * 네트워크 API는 ClientInfoAssignedEvent 이벤트를 수신 해야 하며 이벤트가 발생한 후에만 사용 할수 있습니다 다음은 사용 예 입니다

``` lua
local EventCenter = USGFramework.Runtime.USGZone.EventCenter
 
local ClientInfoAssignedEvent = USGFramework.Runtime.Core.USGNetwork.Events.ClientInfoAssignedEvent
 
local NetworkUtility = USGFramework.Runtime.Core.USGNetwork.NetworkUtility
local Input = UnityEngine.Input
local KeyCode = UnityEngine.KeyCode
 
local isClientReady = false
     
     
function this.Start()
    EventCenter.StartListenToEvent(function(event)
    isClientReady = true
    end, typeof(ClientInfoAssignedEvent))
end
     
function this.Update()
     if not isClientReady then
         return
     end
 
     if Input.GetKeyUp(KeyCode.Alpha1) then
            local cubePrefab = thisLuaComponent:GetUnityObjectPropertyValueByName("cubePrefab").
UnityObject
         NetworkUtility.Instantiate(cubePrefab, this.OnInstantiate, true)
     end
end
```

## List of Network APIs

* 네트워크 이벤트 API 목록

| API Function Name     | Functional Description       |
|-----------------------|------------------------------|
| SendLuaEvent          | 모든 클라이언트에게 네트워크 이벤트를 발신합니다.  |
| SendLuaEventToClients | 지정된 클라이언트에게 네트워크 이벤트를 발신합니다. |

| Event Name              | Functional Description   |
|-------------------------|--------------------------|
| ClientInfoAssignedEvent | 클라이언트 정보 등록시 발생하는 이벤트    |
| ClientJoinedEvent       | 클라이언트가 서버에 연결할때 발생하는 이벤트 |
| ClientDisconnectedEvent | 클라이언트가 연결을 끊을때 발생하는 이벤트  |

* 네트워크 오브젝트 생성/소멸 API 목록

| API Function Name | Functional Description |
|-------------------|------------------------|
| Instantiate       | 	네트워크 오브젝트를 생성합니다      |
| Destroy           | 	네트워크 오브젝트를 소멸시킵니다     |


* 네트워크 오브젝트 상호 작용 API

| API Function Name   | Functional Description      |
|---------------------|-----------------------------|
| IsOwner             | 	네트워크 오브젝트의 소유권을 판단합니다      |
| RequestForOwnership | 	네트워크 오브젝트의 소유권을 획득합니다.     |
| GetGameObjectOwner  | 	네트워크 오브젝트 소유자의 ID 를 획득합니다. |

* RPC API 목록


| API Function Name   | Functional Description      |
|---------------------|-----------------------------|
| InvokeRPC           | 	RPC 를 발신합니다      |


* 씬 로딩 API 목록

| API Function Name | Functional Description |
  |-------------------|------------------------|
| LoadScene         | 씬 로딩                   |
