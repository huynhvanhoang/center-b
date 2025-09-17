# DownloadUgc
## 설명
> 다운로드를 시작합니다.
## 선언
> USGFramework.Runtime.Contents.MatchAPI.DownloadUgc
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
## Parameter
|               **형식**                | **파라미터** | **설명** |
|:-----------------------------------:|:--------:|:------:|
| [ReqDownloadUgc](ReqDownloadUgc.md) | ReqData  | 매칭 정보  |

## Sample Code
```lua
--Call
 function this.CallFunction()
      local req = USGFramework.Runtime.Contents.APIDataStruct.ReqDownLoadUgc.New()
      req.UgcID ="123"
 
      USGFramework.Runtime.Contents.MatchAPI.DownloadUgc(req)
 end
```

[ReqDownloadUgc]:../../Struct/ReqDownloadUgc.md
