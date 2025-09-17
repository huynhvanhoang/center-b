#  PlayerCurrency

## 설명
> 유저의 재화 정보를 가지고있는 구조체 입니다.
## 선언
> USGFramework.Runtime.Contents.APIDataStruct.PlayerCurrency
## 주의사항
> Parameter의 1번째 값인 CurrencyType은 다음과 같습니다. 

|  **CurrencyType**   | **TypeNumber** |
|:-------------------:|:--------------:|
|        None         |       0        |
|        Bcash        |       1        |
|     StarDiamond     |       2        |
|        Gold         |       3        |
|       Scoin_A       |       40       |
|       Scoin_B       |       41       |
|        Ncoin        |       50       |
|      DC_Credit      |       60       |
|     SkillPoint      |       70       |
| FirstRechargeTicket |       80       |
|     PenguinCoin     |       90       |

 

## Parameter
| **형식** |   **파라미터**   | **설명**  |
|:------:|:------------:|:-------:|
|  int   | CurrencyType |  재화타입   |
|  int   |  FreeAmount  | 무료 재화 수 |
|  int   |  PayAmount   | 유료 재화 수 |
