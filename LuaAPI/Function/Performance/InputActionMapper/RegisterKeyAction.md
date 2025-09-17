# RegisterKeyAction

## 설명
UnityEngine.Input.GetKey() 호출을 감시할 루아함수를 등록합니다.

## 선언
FunctionLib.InputActionMapper.RegisterKeyAction

## 주의 사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

해당 함수와 같은 방식의 함수입니다.

|           **함수명**           |                           **함수 설명**                            |
|:---------------------------:|:--------------------------------------------------------------:|
|    RegisterKeyDownAction    |       UnityEngine.Input.GetKeyUp() 호출을 감시할 루아함수를 등록합니다.        |
|     RegisterKeyUpAction     |      UnityEngine.Input.GetKeyDown() 호출을 감시할 루아함수를 등록합니다.       |
|  RegisterMouseButtonAction  |    UnityEngine.Input.GetMouseButton() 호출을 감시할 루아함수를 등록합니다.     |
|     UnregisterKeyAction     |     UnityEngine.Input.GetKey() 호출을 감시하도록 등록한 루아함수를 해제합니다.      |
|   UnregisterKeyDownAction   |   UnityEngine.Input.GetKeyDown() 호출을 감시하도록 등록한 루아함수를 해제합니다.    |
|    UnregisterKeyUpAction    |    UnityEngine.Input.GetKeyUp() 호출을 감시하도록 등록한 루아함수를 해제합니다.     |
| UnregisterMouseButtonAction | _UnityEngine.Input.GetMouseButton() 호출을 감시하도록 등록한 루아함수를 해제합니다. |


## Parameter
|            **형식**            |  **파라미터**  |             **설명**             |
|:----------------------------:|:----------:|:------------------------------:|
| KeyCode or MouseButton Index |  _KeyCode  | 확인할 KeyCode 혹은 MouseButton 인덱스 | 
| LuaComponent | _Component |루아함수를 등록하거나 해제하는 LuaComponent | 
| LuaFunction | _Function  | 입력이 들어왔을때 호출될 루아함수 | 


## Return
|**형식**|**파라미터**|**설명**|
|:---:|:---:|:---:|
|변수타입 | 변수이름 | 변수설명 |

## Sample Code
---
```lua
UpdateKeyTest = {}
 
function UpdateKeyTest.GetTable()
    local this = {}
    local thisLuaComponent = nil
    local thisGameObject = nil
    local useActionFunc = true
 
    -- Awake
    function this.Awake(luaComponentInfo)
        thisGameObject = luaComponentInfo.TargetGameObject   
        thisLuaComponent = luaComponentInfo.Owner
    end
 
 
    function this.Start()
 
        if useActionFunc == true then
 
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha1, thisLuaComponent, this.GetKeyAlpha1)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha2, thisLuaComponent, this.GetKeyAlpha2)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha3, thisLuaComponent, this.GetKeyAlpha3)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha4, thisLuaComponent, this.GetKeyAlpha4)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha5, thisLuaComponent, this.GetKeyAlpha5)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha6, thisLuaComponent, this.GetKeyAlpha6)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha7, thisLuaComponent, this.GetKeyAlpha7)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha8, thisLuaComponent, this.GetKeyAlpha8)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha9, thisLuaComponent, this.GetKeyAlpha9)
            FunctionLib.InputActionMapper.RegisterKeyAction(UnityEngine.KeyCode.Alpha0, thisLuaComponent, this.GetKeyAlpha0)
 
        end
 
    end
 
 
    function this.Update()
 
        if useActionFunc == false then
 
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha1)) then
                print("-----> this.Update / Alpha1")
            end
 
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha2)) then
                print("-----> this.Update / Alpha2")
            end
 
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha3)) then
                print("-----> this.Update / Alpha3")
            end
 
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha4)) then
                print("-----> this.Update / Alpha4")
            end
 
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha5)) then
                print("-----> this.Update / Alpha5")
            end
 
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha6)) then
                print("-----> this.Update / Alpha6")
            end
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha7)) then
                print("-----> this.Update / Alpha7")
            end
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha8)) then
                print("-----> this.Update / Alpha8")
            end
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha9)) then
                print("-----> this.Update / Alpha9")
            end
            if (UnityEngine.Input.GetKey(UnityEngine.KeyCode.Alpha0)) then
                print("-----> this.Update / Alpha0")
            end
 
        end
    end
 
    function this.GetKeyAlpha1()
        print("-----> this.Update / Alpha1")
    end
 
    function this.GetKeyAlpha2()
        print("-----> this.Update / Alpha2")
    end
 
    function this.GetKeyAlpha3()
        print("-----> this.Update / Alpha3")
    end
 
    function this.GetKeyAlpha4()
        print("-----> this.Update / Alpha4")
    end
 
    function this.GetKeyAlpha5()
        print("-----> this.Update / Alpha5")
    end
 
    function this.GetKeyAlpha6()
        print("-----> this.Update / Alpha6")
    end
 
    function this.GetKeyAlpha7()
        print("-----> this.Update / Alpha7")
    end
 
    function this.GetKeyAlpha8()
        print("-----> this.Update / Alpha8")
    end
 
    function this.GetKeyAlpha9()
        print("-----> this.Update / Alpha9")
    end
 
    function this.GetKeyAlpha0()
        print("-----> this.Update / Alpha0")
    end
 
    return this
end
```