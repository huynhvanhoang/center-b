# StartListenToEvent
## 설명
> 이벤트를 모니터링하고 콜백을 바인딩할 수 있습니다. 이 API 를 사용하려면 Lua 스크립트에 USGFramework.Runtime.Core.USGLuaFramework.LuaEventCenter 를 바인딩해야 하며 사례를 참고하여 바인딩을 작성합니다

## 선언
> LuaEventCenter.StartListenToEvent(string eventName, LuaFunction callbackFunction)

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |


## Parameter
|      **형식**      |     **파라미터**     | **설명** |
|:----------------:|:----------------:|:------:|
|      string      |      string      | 이벤트 이름 |
| callbackFunction | callbackFunction | 콜백 함수  |


```lua
local LuaEventCenter = USGFramework.Runtime.Core.USGLuaFramework.LuaEventCenter
local json = require 'cjson'

function this.Start()
    local event = 
    {
    	myName = thisGameObject.name,
        pos = thisTransform.position,
    }
    local jsonString = json.encode(event)
    LuaEventCenter.TriggerEvent("callMyName", jsonString)
end
```

```lua
--Receiver
local LuaEventCenter = USGFramework.Runtime.Core.USGLuaFramework.LuaEventCenter
local json = require 'cjson'

function this.OnEnable()
    LuaEventCenter.StartListenToEvent("callMyName",this.OnListenToCallMyName)
end

function this.OnDisable()
    LuaEventCenter.StopListenToEvent("callMyName",this.OnListenToCallMyName)
end

function this.OnListenToCallMyName(message)
    local target = json.decode(message)
 	 print('object name is ' .. target.myName)
    print('object pos is ' .. target.pos.x .. ", " .. target.pos.y .. ", " .. target.pos.z)
end
```