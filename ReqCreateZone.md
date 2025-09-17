# ReqCreateZone

## 설명
> 새로운 존을 생성하기 위해 사용되는 구조체
## 선언
> USGFramework.Runtime.Contents.APIDataStruct.ReqCreateZone

## Parameter
| **형식** |  **파라미터**  |                                        **설명**                                         |
|:------:|:----------:|:-------------------------------------------------------------------------------------:|
| string |   UgcID    |                                         UGCID                                         |
|  bool  | IsPrivate  |                                        비공개방 여부                                        |
|  bool  | ResultCode | 매칭 시도할 때 매칭 가능한 존에 있는 확인하는지 여부 ,샌드박스영역에서는 테이블로 매칭 가능 존 정의 ,불카누스는 펭귄광장에서 false 로 보내야 함 |
