# AddRangeCameraStack

## 설명
> Main Camera에 여러개의 Overlay Camera를 등록합니다.

## 선언
> USGFramework.Runtime.VulcanusUtility.CameraStacker

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> Main Camera와 Overlay Camera는 사용자가 등록해야 합니다.
> 이미 등록된 Camera와 Main Camera는 OverLay Camera에 등록되지 않습니다.

## Parameter
|  **형식**  |   **파라미터**    |              **설명**               |
|:--------:|:-------------:|:---------------------------------:|
|  Camera  |  baseCamera   |              메인 카메라               |
| Camera[] | overlayCamera | 메인 카메라에 포함 시킬 한개 이상의 OverLay 카메라들 |

## Sample Code
```lua
function this.Sample()
    local cameras = USGFramework.Runtime.VulcanusUtility.CameraStacker.GetHomelandUICamera()
    USGFramework.Runtime.VulcanusUtility.CameraStacker.SetBaseCameraStack(mainCamera, cameras)
end
```

