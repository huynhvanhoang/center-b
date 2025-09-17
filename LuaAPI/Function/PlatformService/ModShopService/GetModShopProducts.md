# GetModShopProducts

## 설명
> ModShop 상품 제품 목록을 요청합니다.
## 선언
> USGFramework.Runtime.Contents.ModShopAPI.GetModShopProducts
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
## CallBack
|                **형식**                 | **파라미터** | **설명** |
|:-------------------------------------:|:--------:|:------:|
|      [ResultData](ResultData.md)      |  Result  |  	결과값  |
| [ModShopProduct](ModShopProduct.md)[] | Products | 상품 리스트 |

## Sample Code
```lua
--Call
 function this.Call_GetModShopProducts()
     USGFramework.Runtime.Contents.ModShopAPI.GetModShopProducts(this.CallBack_GetModShopProducts)
 end
```

```lua
function this.CallBack_GetModShopProducts(Result,products)
        print("@Result Code :".. tostring(Result.Code) ..", Message : "..tostring(Result.Message))
  
        for i=0,products.Length -1 do
            print("@Products ID :".. tostring(products[i].ProductId))
            print("@Products Name :".. tostring(products[i].ProductName))
            print("@Products Icon :".. tostring(products[i].ProductIcon))
 
 
            for j=0,products[i].PriceList.Count -1 do
                print("@Products Price :".. tostring(products[i].PriceList[j]))
                print("@Products CashType :".. tostring(products[i].CashTypeList[j]))
            end
        end
    end
```
