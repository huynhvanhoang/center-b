# SetCameraRenderer

## 설명
> URP Asset의 default Renderer를 변경합니다.
> Overlay Camera도 default Renderer를 변경합니다. 

## 선언
> USGFramework.Runtime.VulcanusUtility.CameraStacker

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |

## Parameter
| **형식** |   **파라미터**   |            **설명**            |
|:------:|:------------:|:----------------------------:|
| Camera | targetCamera | default Renderer 변경시킬 대상 카메라 |
|  int   |    Index     |    default Renderer Index    |

## Sample Code
```lua
function this.Start()
    local index = USGFramework.Runtime.VulcanusUtility.CameraStacker.GetDefaultRendererIndex()
    USGFramework.Runtime.VulcanusUtility.CameraStacker.SetCameraRenderer(camera, index)
end
```