# GetQueryCurrencies
## 설명
> 현재 나의 재화 정보를 얻어옵니다.

## 선언
> USGFramework.Runtime.Contents.CommonAction.GetQueryCurrencies

## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |

## Parameter
|        **형식**         |   **파라미터**    |             **설명**             |
|:---------------------:|:-------------:|:------------------------------:|
|       Function        |   Callback    |  반환된 결과를 받는 데 사용되는 콜백 메서드입니다   |

## CallBack
|                 **형식**                 |    **파라미터**    | **설명** |
|:--------------------------------------:|:--------------:|:------:|
| [PlayerCurrency](PlayerCurrency.md)[ ] | PlayerCurrency | 재화 옵션  |

## Sample Code
```lua
--Call
 function this.GetQueryCurrencies()
        USGFramework.Runtime.Contents.CommonAction.GetQueryCurrencies(this.CallBack_GetQueryCurrencies)
 end
```

```lua
--CallBack
function this.CallBack_GetQueryCurrencies(Currencies)
        local CurrenciesData = Currencies
        for i = 0, CurrenciesData.Length -1 do
            print("@CurrencyType :"..CurrenciesData[i].CurrencyType)
            print("@FreeAmount :"..CurrenciesData[i].FreeAmount)
            print("@PayAmount :"..CurrenciesData[i].PayAmount)
        end
 end
```