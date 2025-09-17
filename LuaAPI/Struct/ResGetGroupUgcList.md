# ResGetGroupUgcList

## 설명
> UGC 창작자 정보를 정의하는 구조체 입니다.
## 선언
> USGFramework.Runtime.Contents.APIDataStruct.ResGetGroupUgcList
## Parameter
|         **형식**          |  **파라미터**   |                 **설명**                  |
|:-----------------------:|:-----------:|:---------------------------------------:|
|           int           | ResultCode  | 결과코드 결과코드가 0(성공)이 아닌 경우 Message가 출력됩니다. |
|         string          |  	Message   |                 에러 메세지                  |
|           int           | 	TotalCount |                  전체 개수                  |
| [UgcBase](UgcBase.md)[] |  	UgcList   |                 Ugc 리스트                 |

