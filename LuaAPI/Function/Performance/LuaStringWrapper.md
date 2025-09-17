# LuaStringWrapper

## 설명

const string 형태를 사용가능하게 하는 object 타입 변수 생성
기본 const string 형태를 사용할 때 내부적으로 GC가 발생하게 되는데 이것을 해결 하기 위한 함수입니다.

## 선언

Utilities.LuaStringWrapper("String")

## 주의 사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |

## Parameter
| **형식** |      **파라미터**       |   **설명**   |
|:------:|:---:|:---:|
| string | value | const string value | 

## Return
|**형식**|**파라미터**|**설명**|
|:---:|:---:|:---:|
|object | object | wrapping string object |

---
## Sample Code
```lua
function this.Start
    LuaInput.ConstString_MouseX = Utilities.LuaStringWrapper("Mouse X")
    LuaInput.ConstString_MouseY = Utilities.LuaStringWrapper("Mouse Y")
    LuaInput.ConstString_Horizontal = Utilities.LuaStringWrapper("Horizontal")
    LuaInput.ConstString_Vertical = Utilities.LuaStringWrapper("Vertical")
 end
```