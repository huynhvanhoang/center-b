# GetDataStoreEntriesGlobal

## 설명
> Global함수는 모두가 접근 가능하며 공용으로 사용 가능한 함수입니다.
> DataStore에 저장된 EntryKeyList를 가져옵니다.
## 선언
> USGFramework.Runtime.Contents.DataStoreAPI.GetDataStoreEntriesGlobal
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
> 가져올 DataStore가 없을 경우 CallBack결과 값에 오류로 나타냅니다.
---


## Parameter
|  **형식**   |    **파라미터**    |                  **설명**                  |
|:---------:|:--------------:|:----------------------------------------:|
| Function  |    Callback    |       반환된 결과를 받는 데 사용되는 콜백 메서드입니다        |
|    int    |    PageNum     |         현재 페이지, 1 이상, 기본값은 1입니다          |
|    int    |    PageSize    | 페이지당 데이터 양은 1 이상, 기본값은 20, 최대값은 200입니다.  |
|  string   | DatastoreCode  |                  데이터 코드                  |
|  string   |     Prefix     |        범위를 지정하는 데 사용할 수 있는 접두사 검색        |
## CallBack
|           **형식**            |      **파라미터**      |    **설명**    |
|:---------------------------:|:------------------:|:------------:|
| [ResultData](ResultData.md) |       Result       |     결과 값     |
|             int             |      PageNum       | 대상 유저의 커넥션ID |
|             int             |      PageSize      |    현재 페이지    |
|             int             |       Total        |     총 개수     |
|             int             |     TotalPages     |    총 페이지     |
|  [EntryKey](EntryKey.md)[]  | DataStoreEntryKeys | 데이터 엔트리키 리스트 |


## Sample Code
```lua
--Call
function this.GetDataStoreEntriesGlobal()
      local PageNum = 1
      local PageSize = 20
      local DataStoreCode ="Test"
      local Prefix = ""
      USGFramework.Runtime.Contents.DataStoreAPI.GetDataStoreEntriesGlobal(this.CallBack_GetDataStoresGlobal,PageNum,PageSize,DataStoreCode,Prefix)
 end
```

```lua
--CallBack
function this.CallBack_GetDataStoresGlobal(result,pageNo,pageSize,total,totalPage,dataStoreKey)
        print("@Result Code :".. tostring(result.Code) ..", Message : "..tostring(result.Message))
        print("@PageNO :".. tostring(pageNo))
        print("@PageSize :".. tostring(pageSize))
        print("@Total :".. tostring(total))
        print("@TotalPage :".. tostring(totalPage))
  
        for i = 0, dataStoreKey.Length - 1 do
            print("@DataStore Code :".. dataStoreKey[i].EntryKey)
            print("@DataStore CreatedAt :".. dataStoreKey[i].CreatedAt)
        end
    end
```
