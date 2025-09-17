# LeaveTeamChannel

## 설명
> 접속된 팀 보이스 채널의 연결을 끊습니다.

## 선언
> USGFramework.Runtime.Contents.VoiceAPI

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> 에디터 모드에서는 작동 하지 않습니다.

## Parameter
|  **형식**  | **파라미터** |       **설명**       |
|:--------:|:--------:|:------------------:|
| Function | Callback | 팀 보이스 채널에 접속 상태 콜백 |

## CallBack
| **형식** | **파라미터** |     **설명**     |
|:------:|:--------:|:--------------:|
|  bool  |  joined  | 팀 보이스 채널 접속 여부 |

## Sample Code
```lua
-- Called when the team leaves or the game ends
function this.OnDestroy()    
    USGFramework.Runtime.Contents.VoiceAPI.LeaveTeamChannel(this.TeamChannelCallBack)
end
```

```lua
-- CallBack
function this.TeamChannelCallBack(joined)
    print("Are you in the team voice channel ? : "  .. tostring(joined))
end
```
