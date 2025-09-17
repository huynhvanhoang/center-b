# RegisterUnpaidRequestHandler

## 설명
> 이전 게임에서 유저가 ModShop 아이템을 샀지만 지급을 받지 못하고 종료 후  
> 유저가 게임에 다시 들어왔을 때 미지급 아이템이 있는지 체크할 함수를 등록 하는 함수입니다.  
> CallBack함수는 유저가 접속했을 경우 호출되며 미지급 아이템에 대한 처리를 한 후 
> 그 결과를 Return해주어야 합니다.
## 선언
> USGFramework.Runtime.Contents.ModShopAPI.RegisterUnpaidRequestHandler
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```X```  |
| ```Server Logic``` |  ```O```  |
> 해당 함수는 Server Logic에서만 동작하는 함수로 Client에서는 호출되지 않습니다.  
> CallBack 함수도 Server Logic에서만 호출됩니다.  
> CallBack 함수의 Return을 반드시 해주어야 합니다.
---


## Parameter
|  **형식**  |   **파라미터**    |          **설명**          |
|:--------:|:-------------:|:------------------------:|
| Function |   Callback    | 유저가 접속 했을때  미지급 처리를 할 함수 |
## CallBack
|                    **형식**                     |   **파라미터**    |    **설명**    |
|:---------------------------------------------:|:-------------:|:------------:|
|          [ResultData](ResultData.md)          |    Result     |     	결과값     |
|                      int                      | ConnectionID  | 대상 유저의 커넥션ID |
| [ModShopOrderNotify](ModShopOrderNotify.md)[] | orderNotifies | 미지급 아이템 리스트  |
## CallBack Return
|                    **형식**                     |   **파라미터**   |    **설명**     |
|:---------------------------------------------:|:------------:|:-------------:|
| [UnpaidRequestResult](UnpaidRequestResult.md) | ReturnResult | 재 지급된 아이템의 정보 |

## Sample Code
```lua
--"Register the function in the Start function"
function this.Start()
    USGFramework.Runtime.Contents.ModShopAPI.RegisterUnpaidRequestHandler(this.CallBack_RegisterUnpaidRequestHandler)
end
```

```lua
--CallBack
function this.CallBack_RegisterUnpaidRequestHandler(Result,targetConnectionID,orderNotifies)
        print("@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message))
            
        local OrderNoArray = {}
        local ResultCodeArray = {}
            
        if orderNotifies.Length == 0 then
            print("@No unpaid items")
        else
            print("@unpaid items Count "..tostring(orderNotifies.Length))
            
            for i=0,Event.OrderNotifies.Length -1 do
                print("@ModShopOrderNotify OrderNo :".. tostring(orderNotifies[i].OrderNo))
                print("@ModShopOrderNotify ProductId :".. tostring(orderNotifies[i].ProductId))
                print("@ModShopOrderNotify PurchaseQuantity :".. tostring(orderNotifies[i].PurchaseQuantity))
                print("@ModShopOrderNotify Price :".. tostring(orderNotifies[i].Price))
                print("@ModShopOrderNotify PayPrice :".. tostring(orderNotifies[i].PayPrice))
                print("@ModShopOrderNotify NotifyStatus :".. tostring(orderNotifies[i].NotifyStatus))
                
                OrderNoArray[i] = orderNotifies[i].OrderNo
                ResultCodeArray[i] = 1
                --ResultCodeArray[i] = 0
            end
        end
            
        --*******crucial*******
        local MyResult = USGFramework.Runtime.Contents.APIDataStruct.UnpaidRequestResult.New(OrderNoArray,ResultCodeArray)
        return  MyResult
    end
```
