# GetUgcDetail
## 설명
> Ugc 상세 정보 요청
## 선언
> USGFramework.Runtime.Contents.UgcAPI.GetUgcDetail
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
## Parameter
|                **형식**                 | **파라미터** |           **설명**            |
|:-------------------------------------:|:--------:|:---------------------------:|
|               Function                | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
| [ReqGetUgcDetail](ReqGetUgcDetail.md) | ReqData  |         요청할 UGC 정보          |
## CallBack
|                **형식**                 | **파라미터** |   **설명**   |
|:-------------------------------------:|:--------:|:----------:|
| [ResGetUgcDetail](ResGetUgcDetail.md) | ResData  | 	결과 UGC 정보 |

## Sample Code
```lua
--Call
 function this.CallFunction()
       local Type = USGFramework.Runtime.Contents.APIDataStruct.UGcArchitectType.Windows
 
       local UgcID = "123456"
       local UgcArchitectType = Type
       local _InputData = USGFramework.Runtime.Contents.APIDataStruct.ReqUgcDetail.New(UgcID,UgcArchitectType)
 
       USGFramework.Runtime.Contents.UgcAPI.GetUgcDetail(this.CallBackFunction,_InputData)
    end
```

```lua
--CallBack
function this.CallBackFunction(ResData)
       print("@ResultCode : "..tostring(ResData.ResultCode))
       print("@Message : "..tostring(ResData.Message))
       
       --ResData.Ugc
       print("@Ugc.IsFavorite : "..tostring(ResData.Ugc.IsFavorite))
       print("@Ugc.IsPlay: "..tostring(ResData.Ugc.IsPlay))
       print("@Ugc.ThumbnailTagName : "..tostring(ResData.Ugc.ThumbnailTagName))
       print("@Ugc.ThumbnailTagType : "..tostring(ResData.Ugc.ThumbnailTagType))
 
       --UgcBase
       print("@ResUgc_Content : "..tostring(ResData.Content))
       print("@ResUgc_Genre : "..tostring(ResData.Genre))
       print("@ResUgc_GradeAvg : "..tostring(ResData.GradeAvg))
       print("@ResUgc_GradeCount : "..tostring(ResData.GradeCount))
       print("@ResUgc_UgcPlay : "..tostring(ResData.UgcPlay))
       print("@ResUgc_PlayCount : "..tostring(ResData.PlayCount))
       print("@Title : "..tostring(ResData.Title))
       print("@UgcId : "..tostring(ResData.UgcId))
       print("@UgcType : "..tostring(ResData.UgcType))
 
        --Tag
        local TagList = ResData.TagList
        for j = 0, TagList.Length -1 do
            print("@TagID"..TagList[i].TagId)
            print("@TagName"..TagList[i].TagName)
        end
 
        --UgcMediaInfo
        local CoverMediaList = ResData.CoverMediaList
        for k = 0, CoverMediaList.Length -1 do
            print("@CoverMedia_MediaNo"..CoverMediaList[k].MediaNo)
            print("@CoverMedia_MediaType"..CoverMediaList[k].MediaType)
            print("@CoverMedia_MediaUrl"..CoverMediaList[k].MediaUrl)
            print("@CoverMedia_PreviewUrl"..CoverMediaList[k].PreviewUrl)
            print("@CoverMedia_FeatureType"..CoverMediaList[k].FeatureType)
        end
 
        --UgcMediaInfo
        local MediaList = ResData.MediaList
        for m = 0, MediaList.Length -1 do
            print("@Media_MediaNo"..MediaList[m].MediaNo)
            print("@Media_MediaType"..MediaList[m].MediaType)
            print("@Media_MediaUrl"..MediaList[m].MediaUrl)
            print("@Media_PreviewUrl"..MediaList[m].PreviewUrl)
            print("@Media_FeatureType"..MediaList[m].FeatureType)
        end
 
        --UgcCreaterInfo
        local UgcCreaterInfo = ResData.CreaterInfo
        print("@UgcCreaterInfo_NicknameNo"..UgcCreaterInfo.NicknameNo)
        print("@UgcCreaterInfo_MemberNo"..UgcCreaterInfo.MemberNo)
        print("@UgcCreaterInfo_Nickname"..UgcCreaterInfo.Nickname)
        print("@UgcCreaterInfo_ProfileImageUrl"..UgcCreaterInfo.ProfileImageUrl)
 
 
        --PackageList
        local PackageList = ResData.PackageList
        for n = 0 , PackageList.Length-1 do
            print("@Package_Architect :"..tostring(PackageList[n].PackageArchitect))
            print("@Package_Checksum :"..tostring(PackageList[n].PackageChecksum))
            print("@Package_FileName :"..tostring(PackageList[n].PackageFileName))
            print("@Package_Id :"..tostring(PackageList[n].PackageId))
            print("@Package_InstallPath :"..tostring(PackageList[n].PackageInstallPath))
            print("@Package_Size :"..tostring(PackageList[n].PackageSize))
            print("@Package_Default :"..tostring(PackageList[n].PackageDefault))
        end
 
        --Mata
        local Meta = ResData.Meta
        print("@Meta_PatchNote :"..tostring(Meta.PatchNote))
        print("@Meta_PublishedDt :"..tostring(Meta.PublishedDt))
        print("@Meta_Version :"..tostring(Meta.Version))
        print("@Meta_VersionId :"..tostring(Meta.VersionId))
        print("@Meta_Extra :"..tostring(Meta.Extra))
        print("@Meta_PackageVersion :"..tostring(Meta.PackageVersion))
        print("@Meta_RepresentRankId :"..tostring(Meta.RepresentRankId))
        print("@Meta_MinPlayerCount :"..tostring(Meta.MinPlayerCount))
        print("@Meta_MaxPlayerCount :"..tostring(Meta.MaxPlayerCount))
        print("@Meta_ProjectType :"..tostring(Meta.ProjectType))
    end
```
