# GetModShopProduct

## 설명
> ModShop 상품의 자세한 정보을 요청합니다.
## 선언
> USGFramework.Runtime.Contents.ModShopAPI.GetModShopProduct
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```X```  |
> 해당 함수는 Client Logic에서만 동작하는 함수로 Server에서는 호출되지 않습니다.
---


## Parameter
|  **형식**  |     **파라미터**     |           **설명**            |
|:--------:|:----------------:|:---------------------------:|
| Function |     Callback     | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
|  string  |    ProductId     |           상품 아이디            |
## CallBack
|               **형식**                | **파라미터** | **설명** |
|:-----------------------------------:|:--------:|:------:|
|     [ResultData](ResultData.md)     |  Result  |  	결과값  |
| [ModShopProduct](ModShopProduct.md) | Product  | 상품 정보  |

## Sample Code
```lua
--Call
function this.Call_GetModShopProduct()
        local ModShopProductID = "ProductID"
        USGFramework.Runtime.Contents.ModShopAPI.GetModShopProduct(this.CallBack_GetModShopProduct,ModShopProductID)
end
```

```lua
function this.CallBack_GetModShopProduct(Result,products)
 
        print("@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message))
        print("@Products ID :".. tostring(products.ProductId))
        print("@Products Name :".. tostring(products.ProductName))
        print("@Products Icon :".. tostring(products.ProductIcon))
        for i = 0, products.PriceList.Count -1 do
            print("@Products Price :".. tostring(products.PriceList[i]))
            print("@Products Type :".. tostring(products.CashTypeList[i]))
        end
    end
```
