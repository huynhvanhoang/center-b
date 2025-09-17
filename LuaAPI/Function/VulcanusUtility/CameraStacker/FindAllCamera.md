# FindAllCamera

## 설명
> Scene에 있는 모든 카메라들을 가져옵니다.

## 선언
> USGFramework.Runtime.VulcanusUtility.CameraStacker

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> 함수 호출 시점에 Active된 Scene에서 가져옵니다.

## Sample Code
```lua
function this.Sample()
    local allCamera = USGFramework.Runtime.VulcanusUtility.CameraStacker.FindAllCamera()
    USGFramework.Runtime.VulcanusUtility.CameraStacker.SetBaseCameraStack(mainCamera, allCamera)
end
```