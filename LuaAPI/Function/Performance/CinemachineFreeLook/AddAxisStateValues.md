# SetAxisStateInputValues

## 설명
CinemachineFreeLook 카메라 Axis struct 값을 루아 스택 사용 최소화를 위해 추가한 함수
CinemachineFreeLook 카메라 AxisStateInput 값을 설정합니다.

## 선언
FunctionLib.CinemachineFreeLook.SetAxisStateInputValues


## 주의 사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |


## Parameter
|     **형식**     | **파라미터** |            **설명**            |
|:--------------:|:--------:|:----------------------------:|
| freelookCamera |  Value   | CinemachineFreeLook Instance | 
|      int       |    X     |         Axis X value         | 
|      int       |    y     |         Axis Y value         | 


## Sample Code
---

```lua
function this.Start
    local data = json.decode(message)
    FunctionLib.CinemachineFreeLook.SetAxisStateInputValues(_freeLookCamera, 0 , 0)
    FunctionLib.CinemachineFreeLook.AddAxisStateValues(_freeLookCamera,data.xValue,data.yValue)
    FunctionLib.CinemachineFreeLook.SetAxisStateValues(_freeLookCamera,data.xValue,data.yValue) 
end
```