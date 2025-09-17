# GetGraphicOption
## 설명
> 홈랜드 환경 설정 중 원하는 시점에 그래픽 옵션을 획득
## 선언
> USGFramework.Runtime.Contents.CommonAction.GetGraphicOption
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
## Parameter
|  **형식**   | **파라미터** |           **설명**            |
|:---------:|:--------:|:---------------------------:|
| Function  | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
## CallBack
| **형식** |   **파라미터**    | **설명** |
|:------:|:-------------:|:------:|
|  int   | GraphicOption | 그래픽 옵션 |

## Sample Code
```lua
function this.Start()
        USGFramework.Runtime.Contents.CommonAction.GetGraphicOption(this.CallBack_GetGraphicOption)
end
```

```lua
--CallBack
 function this.CallBack_GetGraphicOption(Option)
        print("Option :" ..tostring(Option));
 end
```


