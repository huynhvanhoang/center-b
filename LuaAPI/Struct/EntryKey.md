# EntryKey

---

## 설명
> DataStore or Franchisee에서 주로 사용되는 구조체입니다. 
> 매개변수로 Key을 전달하기 위해 사용됩니다. 

## 선언
## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.EntryKey

## Parameter
|         **형식**         |     **파라미터**      |       **설명**       |
|:----------------------:|:-----------------:|:------------------:|
|         string         |   DataStoreCode   | 데이터스토어 or 프렌차이즈 코드 |
|         string         |        Key        |      데이터 Key       |

## SampleCode
```lua
function this.TestFunction()
     local EntryCode = "Test"
     local EntryKey =  "TestKey"
     local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New(EntryCode,EntryKey)
end
```