# JoinTeamChannel

## 설명
> 유저가 팀 채팅 채널에 접속합니다.
> 팀 채널에 접속시 만들어지지 않은 채널이라면 접속전 생성이 이루어지고 채널에 접속됩니다.
> 팀 채널명이 같더라도 존이 다르면 다른 채널로 관리됩니다.

## 선언
> USGFramework.Runtime.Contents.ChatAPI

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> 존이 생성된 게임에서 호출되어야 합니다.
> 에디터 모드에서는 작동 하지 않습니다.
> 채팅에 접속만 가능하며, 홈랜드 채팅 UI가 연동되어 있지 않으면 채팅 기능을 사용할 수 없습니다.

## Parameter
|   **형식**    |   **파라미터**   |      **설명**       |
|:-----------:|:------------:|:-----------------:|
|   string    |   teamGuid   | 팀을 구분할 수 있는 고유 이름 |
|  Function   |   Callback   | 팀 채팅 채널에 접속 상태 콜백 |
> 팀을 구분하는 값은 제한이 없으나 너무 긴 값은 체널에 실패할 수 있습니다.
> 다른 유저들도 같이 사용할 수 있게 관리되는 팀 이름이나 유니트 키값으로 팀 채널 생성되어야 합니다. 팀을 구분하는 값은 제한이 없으나 다른 유저들도 같이 사용할 수 있게 관리되는 팀 이름이나 유니트 키값으로 팀 채널 생성되어야 합니다.

## CallBack
| **형식** | **파라미터** |    **설명**     |
|:------:|:--------:|:-------------:|
|  bool  |  joined  | 팀 채팅 채널 접속 여부 |

## Sample Code
```lua
-- Called when a team is created and joined to a team
function this.Start()
    USGFramework.Runtime.Contents.ChatAPI.JoinTeamChannel("TeamA", this.TeamChannelCallBack)
end
```

```lua
-- CallBack
function this.TeamChannelCallBack(joined)
    print("Are you in the team chat channel ? : "  .. tostring(joined))
end
```
