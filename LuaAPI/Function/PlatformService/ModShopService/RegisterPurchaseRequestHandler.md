# RegisterPurchaseRequestHandler

## 설명
> 유저가 ModShop에서 구입을 요청할때 구입요청에 대한 처리를 하는 함수를 등록합니다.
> CallBack함수는 유저가 PurchaseModShop함수를 호출 했을때 호출되며 
> CallBack함수에서는 유저가 구입 요청한 내용을 처리 후 그 결과를 Return해주어야 합니다.
## 선언
> USGFramework.Runtime.Contents.ModShopAPI.RegisterPurchaseRequestHandler
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```X```  |
| ```Server Logic``` |  ```O```  |
> 유저가 구입 요청 [PurchaseModShop](PurchaseModShop.md) 함수를 호출 했을 때 Server에 해당 내용이 전달되고
> 그 내용을 창작자가 직접 처리할 수 있도록 함수를 등록합니다.  
> Server에서는 전달된 내용을 받을수 있는 함수를 등록하는 함수입니다.  
> > 함수의 호출 단계는 다음과 같습니다.
> >1. Client가 [PurchaseModShop](PurchaseModShop.md) 함수로 구매요청을 합니다.
> >2. Server는 해당 내용으로 구매요청 후 결과를 받습니다.
> >3. Server는 RegisterPurchaseRequestHandler에 등록한 함수를 통해 아이템 지급처리를 합니다.
> >4. Server는 아이템 지급 처리에 대한 결과를 Client에게 전달합니다.
> >5. Client는 아이템 지급 처리에 대한 결과를 받습니다.

![PurchaseModShop_img.PNG](media/images/PurchaseModShop_img.PNG)



## Parameter
|  **형식**  | **파라미터** |         **설명**         |
|:--------:|:--------:|:----------------------:|
| Function | Callback | 유저가 구입 요청 했을 때 처리 할 함수 |
## CallBack
|           **형식**            |   **파라미터**   |    **설명**    |
|:---------------------------:|:------------:|:------------:|
| [ResultData](ResultData.md) |    Result    |     	결과값     |
|             int             | ConnectionID | 대상 유저의 커넥션ID |
|           string            |   OrderNo    |     주문번호     |
|             int             |   payPrice   |     지불가격     |
|             int             |   CashType   |   구매한 캐쉬타입   |
## CallBack Return
|                      **형식**                       |   **파라미터**   |         **설명**          |
|:-------------------------------------------------:|:------------:|:-----------------------:|
| [PurchaseRequestResult](PurchaseRequestResult.md) | ReturnResult | 구매 요청된 아이템을 지급한 아이템의 정보 |

## Sample Code
```lua
--"Register the function in the Start function"
function this.Start()
    USGFramework.Runtime.Contents.ModShopAPI.RegisterPurchaseRequestHandler(this.CallBack_RegisterPurchaseRequestHandler)
end
```

```lua
--CallBack
 function this.CallBack_RegisterPurchaseRequestHandler(resultInfo,targetConnectionID,orderNo,payPrice,CashType)
    
        print("@targetConnectionID :".. tostring(targetConnectionID))
        print("@orderNo :".. tostring(orderNo))
        print("@payPrice :".. tostring(payPrice))
        print("@cashType :".. tostring(CashType))

        local ResultOrderNo = orderNo
        local ResultCode = 1

        local MyResult = USGFramework.Runtime.Contents.APIDataStruct.PurchaseRequestResult.New(ResultOrderNo,ResultCode)
        return  MyResult
 end
```
