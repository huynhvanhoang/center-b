# UgcBase

## 설명
> 현재 매칭중인 UGC의 정보를 받아올때 사용되는 구조체 입니다.

## 선언
> USGFramework.Runtime.Contents.APIDataStruct.UgcBase
## Parameter
|                **형식**                 |    **파라미터**    |   **설명**   |
|:-------------------------------------:|:--------------:|:----------:|
|                string                 |    Content     |   UGC 설명   |
|                string                 |     Genre      |     장르     |
|                 float                 |    GradeAvg    |   평균 별점    |
|                  int                  |   GradeCount   | 별점을 매긴 횟수  |
|     [UgcPlayType](UgcPlayType.md)     |    UgcPlay     | UGC 플레이 구분 |
|                  int                  |   PlayCount    | 모드 플레이 횟수  |
|     [UgcTagInfo](UgcTagInfo.md)[]     |    TagList     |   태그 리스트   |
|                string                 |     Title      |   UGC 제목   |
|                string                 |     UgcId      |   UGC ID   |
|   [UgcMediaInfo](UgcMediaInfo.md)[]   | CoverMediaList |  썸네일 리스트   |
|   [UgcMediaInfo](UgcMediaInfo.md)[]   |   MediaList    |  미디어 리스트   |
|         [UgcType](UgcType.md)         |    UgcType     |   UGC 종류   |
|  [UgcCreaterInfo](UgcCreaterInfo.md)  |  CreaterInfo   |   창작자 정보   |
| [UgcCreaterInfo](UgcCreaterInfo.md)[] |  PackageList   |   패키지 정보   |
|         [UgcMeta](UgcMeta.md)         |      Meta      |  커스텀 Meta  |

