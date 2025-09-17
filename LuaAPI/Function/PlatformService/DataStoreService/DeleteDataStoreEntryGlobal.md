# DeleteDataStoreEntryGlobal

## 설명
> Global함수는 모두가 접근 가능하며 공용으로 사용 가능한 함수입니다.
> DataStore에 저장된 EntryKey로 해당 값을 삭제 합니다.

## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.DeleteDataStoreEntryGlobal
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 1. 가져올 DataStore가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
> 2. 해당 EntryKey값으로 데이터가 저장되어 있어야 정상적인 동작을 합니다.

---


## Parameter
|         **형식**          | **파라미터** |           **설명**            |
|:-----------------------:|:--------:|:---------------------------:|
|        Function         | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
| [EntryKey](EntryKey.md) | EntryKey |       삭제할 값의 EntryKey       |
## CallBack
|           **형식**            | **파라미터** | **설명** |
|:---------------------------:|:--------:|:------:|
| [ResultData](ResultData.md) |  Result  |  결과 값  |


## Sample Code
```
--Call
function this.Call_DeleteDataStoreEntry()
       local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New("Test","TestKey")
       USGFramework.Runtime.Contents.DataStoreAPI.DeleteDataStoreEntryGlobal(this.CallBack_DeleteDataStoreEntryGlobal,Key)
end
```

```
--CallBack
function this.CallBack_DeleteDataStoreEntryGlobal(result)
    print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
end
```
