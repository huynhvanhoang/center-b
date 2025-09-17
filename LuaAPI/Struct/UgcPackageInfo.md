# UgcPackageInfo

## 설명
> UGC 창작자 정보를 정의하는 구조체 입니다.

## 선언
> USGFramework.Runtime.Contents.APIDataStruct.UgcPackageInfo
## Parameter
|                 **형식**                  |      **파라미터**       |                         **설명**                         |
|:---------------------------------------:|:-------------------:|:------------------------------------------------------:|
| [UgcArchitectType](UgcArchitectType.md) |  PackageArchitect   | 파일이 속한 장치. AOS, IOS, Server, Project, Package, Windows |
|                 string                  |  	PackageChecksum   |                     UGC 패키지 유효성 검증                     |
|                 string                  |  	PackageFileName   |                     UGC 패키지 파일 이름                      |
|                 string                  |     	PackageId      |                     UGC 패키지 파일 아이디                     |
|                 string                  | 	PackageInstallPath |                     UGC 패키지 파일 경로                      |
|                  long                   |    	PackageSize     |                     UGC 패키지 파일 사이즈                     |
|                  long                   |   	PackageDefault   |       기본 다운로드 파일인지 여부 device를 지정하지 않으면 기본 파일을 다운       |

