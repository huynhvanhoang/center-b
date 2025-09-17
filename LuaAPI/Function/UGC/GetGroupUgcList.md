# GetGroupUgcList
## 설명
> Ugc 리스트를 요청합니다.
## 선언
> USGFramework.Runtime.Contents.UgcAPI.GetGroupUgcList
## 주의사항
|    **함수 동작 환경**    | **동작 여부** |
|:------------------:|:---------:|
| ```Client Logic``` |  ```O```  |
| ```Server Logic``` |  ```O```  |
---
## Parameter
|                   **형식**                    | **파라미터** |           **설명**            |
|:-------------------------------------------:|:--------:|:---------------------------:|
|                  Function                   | Callback | 반환된 결과를 받는 데 사용되는 콜백 메서드입니다 |
| [ReqGetGroupUgcList](ReqGetGroupUgcList.md) | ReqData  |       요청할 UGC 리스트 속성        |
## CallBack
|                   **형식**                    | **파라미터** |   **설명**    |
|:-------------------------------------------:|:--------:|:-----------:|
| [ResGetGroupUgcList](ResGetGroupUgcList.md) | ResData  | 	결과 데이터 리스트 |

## Sample Code
```lua
--Call
function this.CallFunction()
        local ProjectType = USGFramework.Runtime.Contents.APIDataStruct.UGCProjectType.VulcanusPro
        local Key = "1"
        local Size = 5
        local _InputData = USGFramework.UgcAPI.Contents.APIDataStruct.ReqGetGroupUgcList.New(ProjectType,Key,Size)
 
 
        USGFramework.Runtime.Contents.UgcAPI.GetGroupUgcList(this.CallBackFunction,_InputData)
 end
```

```lua
--CallBack
 function this.CallBackFunction(ResUgcList)
        print("@ResultCode : "..tostring(ResUgcList.ResultCode))
        print("@Message : "..ResUgcList.Message)
        print("@TotalCount : "..ResUgcList.TotalCount)
 
 
        local UGBBase = ResUgcList.UgcList
        for i = 0,ResUgcList.UgcList.Length -1 do
            print("@ResUgc_Content : "..tostring(UGBBase[i].Content))
            print("@ResUgc_Genre : "..tostring(UGBBase[i].Genre))
            print("@ResUgc_GradeAvg : "..tostring(UGBBase[i].GradeAvg))
            print("@ResUgc_GradeCount : "..tostring(UGBBase[i].GradeCount))
            print("@ResUgc_UgcPlay : "..tostring(UGBBase[i].UgcPlay))
            print("@ResUgc_PlayCount : "..tostring(UGBBase[i].PlayCount))
            print("@Title : "..tostring(UGBBase[i].Title))
            print("@UgcId : "..tostring(UGBBase[i].UgcId))
            print("@UgcType : "..tostring(UGBBase[i].UgcType))
 
            --Tag
            local TagList = UGBBase[i].TagList
            for j = 0, TagList.Length -1 do
                print("@TagID"..TagList[i].TagId)
                print("@TagName"..TagList[i].TagName)
            end
 
             --UgcMediaInfo
            local CoverMediaList = UGBBase[i].CoverMediaList
            for k = 0, CoverMediaList.Length -1 do
                print("@CoverMedia_MediaNo"..CoverMediaList[k].MediaNo)
                print("@CoverMedia_MediaType"..CoverMediaList[k].MediaType)
                print("@CoverMedia_MediaUrl"..CoverMediaList[k].MediaUrl)
                print("@CoverMedia_PreviewUrl"..CoverMediaList[k].PreviewUrl)
                print("@CoverMedia_FeatureType"..CoverMediaList[k].FeatureType)
            end
 
            --UgcMediaInfo
            local MediaList = UGBBase[i].MediaList
            for m = 0, MediaList.Length -1 do
                print("@Media_MediaNo"..MediaList[m].MediaNo)
                print("@Media_MediaType"..MediaList[m].MediaType)
                print("@Media_MediaUrl"..MediaList[m].MediaUrl)
                print("@Media_PreviewUrl"..MediaList[m].PreviewUrl)
                print("@Media_FeatureType"..MediaList[m].FeatureType)
            end
 
            --UgcCreaterInfo
            local UgcCreaterInfo = UGBBase[i].CreaterInfo
            print("@UgcCreaterInfo_NicknameNo"..UgcCreaterInfo.NicknameNo)
            print("@UgcCreaterInfo_MemberNo"..UgcCreaterInfo.MemberNo)
            print("@UgcCreaterInfo_Nickname"..UgcCreaterInfo.Nickname)
            print("@UgcCreaterInfo_ProfileImageUrl"..UgcCreaterInfo.ProfileImageUrl)
 
            --PackageList
            local PackageList = UGBBase[i].PackageList
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
            local Meta = UGBBase[i].Meta
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
    end
```
