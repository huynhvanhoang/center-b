# AddCameraStack

## 설명
> Main Camera에 Overlay Camera를 등록합니다.

## 선언
> USGFramework.Runtime.VulcanusUtility.CameraStacker

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> Main Camera와 Overlay Camera는 사용자가 등록해야 합니다.
> 동일한 Overlay Camera를 중복 요청시 overlay 순서를 변경해주기 위해 지웠다가 다시 추가합니다.

## Parameter
| **형식** |   **파라미터**    |          **설명**           |
|:------:|:-------------:|:-------------------------:|
| Camera |  baseCamera   |          메인 카메라           |
| Camera | overlayCamera | 메인 카메라에 포함 시킬 OverLay 카메라 |

## Sample Code
```lua
function this.Sample()
    USGFramework.Runtime.VulcanusUtility.CameraStacker.SetBaseCameraStack(mainCamera, uiCamera)
end
```

