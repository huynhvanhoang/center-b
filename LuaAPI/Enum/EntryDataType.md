# EntryDataType
---
## 설명
> EntryValue에서 사용하는 매개변수에서 사용되는 Enum값

## 선언
>  USGFramework.Runtime.Contents.APIDataStruct.EntryValue.EntryDataType  

## Parameter
| **형식** | **파라미터** | **설명**  |
|:------:|:--------:|:-------:|
|  Enum  |   None   |         |
|  Enum  |   Bool   |  bool형  |
|  Enum  |   Long   |  long형  |
|  Enum  |  String  | string형 |

## Sample Code

```lua
--Call
function this.CreateEntryKey()
        local BoolType = USGFramework.Runtime.Contents.APIDataStruct.EntryValue.EntryDataType.Bool
        local LongType = USGFramework.Runtime.Contents.APIDataStruct.EntryValue.EntryDataType.Long
        local StringType = USGFramework.Runtime.Contents.APIDataStruct.EntryValue.EntryDataType.String
end
```

