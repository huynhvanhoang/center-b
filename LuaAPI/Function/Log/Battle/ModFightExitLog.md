# ModFightExitLog

## 설명
> 현재 모드가 BattleMod일 때 모드의 상태를 알려주기 위한 로그입니다.

## 선언
>USGFramework.Runtime.Contents.BattleLog.ModFightExitLog

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 해당 함수에서는 두 가지 상태를 Parameter로 남기게 됩니다.
> 1. 플레이어가 배틀을 종료했을 때 = "normal"
> 2. 플레이어가 배틀 도중에 종료했을 때 = "midway"
---
## Parameter
| **형식** | **파라미터**  |        **설명**        |
|:------:|:---------:|:--------------------:|
| string | GameState | 현재 상태에 대해 정해진 string |

## Sample Code
```lua
   --The battle is finished.
   function this.EndBattle_Normal()
     USGFramework.Runtime.Contents.BattleLog.ModFightExitLog("normal")
   end
   
   --The player has left the battle.
   function this.EndBattle_Midway()
     USGFramework.Runtime.Contents.BattleLog.ModFightExitLog("midway")
   end
```
