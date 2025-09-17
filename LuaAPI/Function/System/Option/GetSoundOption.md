# GetSoundOption
## 설명
> 홈랜드 환경 설정 중 원하는 시점에 사운드 옵션을 획득
## 선언
> USGFramework.Runtime.Contents.CommonAction.GetSoundOption
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
| **형식** | **파라미터** | **설명** |
|:------:|:--------:|:------:|
| float  |   Vol    |   볼륨   |
|  bool  |   Mute   |  음속어   |

## Sample Code
```lua
--Call
 function this.Start()
        USGFramework.Runtime.Contents.CommonAction.GetSoundOption(this.Callback_GetSoundOption)
 end
```

```lua
--CallBack
function this.Callback_GetSoundOption(Vol,Mute)
        print("Vol :" ..tostring(Vol).. "Mute :" ..tostring(Mute));
end
```

