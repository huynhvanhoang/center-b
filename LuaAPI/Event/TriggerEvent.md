# TriggerEvent

## 설명
> 이벤트를 트리거합니다.

## 선언
> LuaEventCenter.TriggerEvent(string eventName, string args)

## 주의사항
| **동작 여부** |          **설명**          |
|:---------:|:------------------------:|
|     O     | Client Logic에서 사용 가능합니다. |
|     X     | Server Logic에서 사용 가능합니다. |


## Parameter
| **형식** | **파라미터** |       **설명**       |
|:------:|:--------:|:------------------:|
| string |  string  |       이벤트 이름       |
|  args  |  string  | 보내려는 json 양식의 파라미터 |


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