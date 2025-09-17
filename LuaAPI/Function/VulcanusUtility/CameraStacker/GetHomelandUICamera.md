# GetHomelandUICamera

## 설명
> 홈랜드에서 사용하는 UI 카메라들을 가져옵니다.

## 선언
> USGFramework.Runtime.VulcanusUtility.CameraStacker

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> 홈랜드 환경에서만 동작하는 함수입니다.

## Sample Code
```lua
function this.Sample()
    local cameras = USGFramework.Runtime.VulcanusUtility.CameraStacker.GetHomelandUICamera()
    USGFramework.Runtime.VulcanusUtility.CameraStacker.SetBaseCameraStack(camera, cameras)
end
```
