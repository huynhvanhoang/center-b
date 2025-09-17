# UgcMeta

## 설명
> UGC Meta정보를 정의하는 구조체입니다.
## 선언
> USGFramework.Runtime.Contents.APIDataStruct.UgcMeta
## Parameter
|               **형식**                |    **파라미터**     |                      **설명**                      |
|:-----------------------------------:|:---------------:|:------------------------------------------------:|
|               string                |    PatchNote    |                  출판 시 작성한 패치 노트                  |
|                long                 |   PublishedDt   |           UGC 출시 일시. 예) 1541030400000            |
|                float                |     Version     |         UGC 현재 버전. Package Version 과 다름          |
|                 int                 |    VersionId    | UGC의 모든 버전을 관리하는 시스템 값. Version 관련 API를 호출할 때 사용 |
|               string                |      Extra      |                  운영툴에서 정의하는 식별자                  |
|               string                | PackageVersion  |                    패키지 파일 버전                     |
|               string                | RepresentRankId |             대표 랭크 ID. 없다면 랭크 없는 UGC              |
|                 int                 | MinPlayerCount  |           UGC 최소 시작 인원 수. default : 1            |
|                 int                 | MaxPlayerCount  |   UGC 최대 인원 수. 최대인원은 TeamList.TeamMaxUser 의 합    |
| [UGCProjectType](UGCProjectType.md) |   ProjectType   |                     	프로젝트 타입                     |

