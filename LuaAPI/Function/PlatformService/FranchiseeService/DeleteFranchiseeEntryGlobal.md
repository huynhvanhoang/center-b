# DeleteFranchiseeEntryGlobal

## 설명
> Global함수는 모두가 접근 가능하며 공용으로 사용 가능한 함수입니다.
> Franchisee에 저장된 값이 있을 경우 값 을 삭제 합니다.
## 선언
> USGFramework.Runtime.Contents.FranchiseeAPI.DeleteFranchiseeEntryGlobal
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 Franchisee 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|         **형식**          | **파라미터** |           **설명**            |
|:-----------------------:|:--------:|:---------------------------:|
|        Function         | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
| [EntryKey](EntryKey.md) | EntryKey |          세팅할 엔트리 키          |
## CallBack
|          **형식**           | **파라미터** | **설명** |
|:-------------------------:|:--------:|:------:|
| [ResultData](EntryKey.md) |  Result  |  결과 값  |


## Sample Code
```lua
--Call
function this.Call_DeleteFranchiseeEntryGlobal()
    local Key = USGFramework.Runtime.Contents.APIDataStruct.EntryKey.New("Test","TestKey")
    USGFramework.Runtime.Contents.FranchiseeAPI.DeleteFranchiseeEntryGlobal(this.CallBack_DeleteFranchiseeEntryGlobal,Key)
end
```

```lua
--CallBack
function this.CallBack_DeleteFranchiseeEntryGlobal(result)
   print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
end
```
