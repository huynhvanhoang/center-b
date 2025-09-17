# PurchaseModShop

## 설명
> ModShop 상품 구매요청을 합니다.
## 선언
> USGFramework.Runtime.Contents.ModShopAPI.PurchaseModShop
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> 해당 함수를 사용하기위해서는 해당함수를 필수적으로 선언해야합니다. [RegisterPurchaseRequestHandler](RegisterPurchaseRequestHandler.md)
> > 함수의 호출 단계는 다음과 같습니다.
> > 1. Client가 PurchaseModShop 함수로 구매요청을 합니다.
> > 2. Server는 해당 내용으로 구매요청 후 결과를 받습니다.
> > 3. Server는 [RegisterPurchaseRequestHandler](RegisterPurchaseRequestHandler.md)에 등록한 함수를 통해 아이템 지급처리를 합니다.
> > 4. Server는 아이템 지급 처리에 대한 결과를 Client에게 전달합니다.
> > 5. Client는 아이템 지급 처리에 대한 결과를 받습니다. 

![PurchaseModShop_img.PNG](media/images/PurchaseModShop_img.PNG)


## Parameter
|  **형식**  |     **파라미터**     |           **설명**            |
|:--------:|:----------------:|:---------------------------:|
| Function |     Callback     | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
|  string  |    ProductId     |           상품 아이디            |
|   int    | PurchaseQuantity |            구매 수량            |
|   int    |     CashType     |            캐쉬 타입            |
## CallBack
|           **형식**            | **파라미터** |    **설명**    |
|:---------------------------:|:--------:|:------------:|
| [ResultData](ResultData.md) |  Result  |     	결과값     |
|           string            | orderNo  | 대상 유저의 커넥션ID |
|             int             | payPrice |     지불가격     |

## Sample Code
```lua
--Call
function this.Call_PurchaseModShop()
      local ModShopProductID = "ProductID"
      local PurchaseQuantity = 1
      local CashType = 2
      USGFramework.Runtime.Contents.ModShopAPI.PurchaseModShop(this.CallBack_PurchaseModShop,ModShopProductID,PurchaseQuantity,CashType)
end
```

```lua
--CallBack
 function this.CallBack_PurchaseModShop(Result,OrderNo,payPrice)
        Str = Str.."@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message).."\n"
        Str = Str.."@OrderNo :".. tostring(OrderNo).."\n"
        Str = Str.."@PayPrice :"..tostring(PayPrice).."\n"

        print("@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message))
        print("@OrderNo :".. tostring(OrderNo))
        print("@PayPrice :"..tostring(PayPrice))
        Log.text = Str   
    end
```
