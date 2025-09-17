# GetAllSoundOption
## 설명
> 홈랜드 환경 설정 중 사운드와 관련된 모든 옵션을 가져옵니다.
## 선언
> USGFramework.Runtime.Contents.CommonAction.GetAllSoundOption
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
|          **형식**           | **파라미터** | **설명**  |
|:-------------------------:|:--------:|:-------:|
| [SoundInfo](SoundInfo.md) |   Main   | 메인 사운드  |
| [SoundInfo](SoundInfo.md) |   BGM    | BGM 사운드 |
| [SoundInfo](SoundInfo.md) |  Effect  | 효과 사운드  |

## Sample Code
```lua
--Call
 function this.Start()
       USGFramework.Runtime.Contents.CommonAction.GetAllSoundOption(this.CallBack_GetAllSoundOption)
 end
```

```lua
--CallBack
 function this.CallBack_GetAllSoundOption(Main,BGM,Effect)
        print("@MainVolume :".. tostring(Main.Volume))
        print("@MainVolume :".. tostring(Main.Mute))

        print("@BGMVolume :".. tostring(BGM.Volume))
        print("@BGMMute :".. tostring(BGM.Mute))

        print("@EffectVolume :".. tostring(Effect.Volume))
        print("@EffectMute :".. tostring(Effect.Mute))
    end
```

