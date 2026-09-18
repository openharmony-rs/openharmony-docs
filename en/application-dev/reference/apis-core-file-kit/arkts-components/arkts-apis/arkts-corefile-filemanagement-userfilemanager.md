# @ohos.filemanagement.userFileManager

The **userFileManager** module provides user data management capabilities, including accessing and modifying user media data.

**Since:** 9

**Deprecated since:** 26.0.0

**Substitutes:** [photoAccessHelper](../../apis-media-library-kit/arkts-apis/arkts-medialibrary-file-photoaccesshelper.md)

**System capability:** SystemCapability.FileManagement.UserFileManager.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { userFileManager } from '@kit.CoreFileKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getUserFileMgr](arkts-corefile-userfilemanager-getuserfilemgr-f-sys.md) | Obtains a **UserFileManager** instance. This instance can be used to access and modify user media data (such as audio and video assets, images, and documents). |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AbsAlbum](arkts-corefile-userfilemanager-absalbum-i-sys.md) | Defines the AbsAlbum. |
| [Album](arkts-corefile-userfilemanager-album-i-sys.md) | Provides APIs to manage albums. |
| [AlbumFetchOptions](arkts-corefile-userfilemanager-albumfetchoptions-i-sys.md) | Defines the options for fetching file attributes. |
| [ChangeData](arkts-corefile-userfilemanager-changedata-i-sys.md) | Defines the return value of the listener callback. |
| [FetchOptions](arkts-corefile-userfilemanager-fetchoptions-i-sys.md) | Defines the options for fetching file attributes. |
| [FetchResult](arkts-corefile-userfilemanager-fetchresult-i-sys.md) | Provides APIs to manage the file retrieval result. |
| [FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md) | Provides APIs for encapsulating file asset attributes. |
| [PeerInfo](arkts-corefile-userfilemanager-peerinfo-i-sys.md) | Defines information about a registered device. |
| [PhotoCreateOptions](arkts-corefile-userfilemanager-photocreateoptions-i-sys.md) | Defines the options for creating an image or video asset. |
| [PrivateAlbum](arkts-corefile-userfilemanager-privatealbum-i-sys.md) | Provides APIs for managing the system albums. |
| [UserFileManager](arkts-corefile-userfilemanager-userfilemanager-i-sys.md) | Defines the UserFileManager class and provides functions to access the data in user file storage. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AlbumKey](arkts-corefile-userfilemanager-albumkey-e-sys.md) | Defines the key album information. |
| [AlbumSubType](arkts-corefile-userfilemanager-albumsubtype-e-sys.md) | Enumerates the album subtypes. |
| [AlbumType](arkts-corefile-userfilemanager-albumtype-e-sys.md) | Enumerates the album types. |
| [AudioKey](arkts-corefile-userfilemanager-audiokey-e-sys.md) | Defines the key information about an audio file. |
| [DefaultChangeUri](arkts-corefile-userfilemanager-defaultchangeuri-e-sys.md) | Enumerates the **DefaultChangeUri** subtypes. |
| [FileType](arkts-corefile-userfilemanager-filetype-e-sys.md) | Enumerates media file types. |
| [ImageVideoKey](arkts-corefile-userfilemanager-imagevideokey-e-sys.md) | Defines the key information about an image or video file. |
| [NotifyType](arkts-corefile-userfilemanager-notifytype-e-sys.md) | Enumerates the notification event types. |
| [PhotoSubType](arkts-corefile-userfilemanager-photosubtype-e-sys.md) | Enumerates the [FileAsset](arkts-corefile-userfilemanager-fileasset-i-sys.md) types. |
| [PositionType](arkts-corefile-userfilemanager-positiontype-e-sys.md) | Enumerates the file location. |
| [PrivateAlbumType](arkts-corefile-userfilemanager-privatealbumtype-e-sys.md) | Enumerates the system album types. |
<!--DelEnd-->

<!--Del-->
### Types(System API)

| Name | Description |
| --- | --- |
| [ChangeEvent](arkts-corefile-userfilemanager-changeevent-t-sys.md) | Enumerates the type of changes to observe. |
| [MemberType](arkts-corefile-userfilemanager-membertype-t-sys.md) | Represents the type of a file asset member. |
<!--DelEnd-->
