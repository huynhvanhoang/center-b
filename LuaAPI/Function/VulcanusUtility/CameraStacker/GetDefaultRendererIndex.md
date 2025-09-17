# GetDefaultRendererIndex

## 설명
> URP Asset의 default Renderer Index를 가져옵니다.
> Index를 가져오는데 실패하면 -1를 반환합니다.

## 선언
> USGFramework.Runtime.VulcanusUtility.CameraStacker

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Sample Code
```lua
function this.Sample()
    local index = USGFramework.Runtime.VulcanusUtility.CameraStacker.GetDefaultRendererIndex()
    USGFramework.Runtime.VulcanusUtility.CameraStacker.SetCameraRenderer(camera, index)
end
```
