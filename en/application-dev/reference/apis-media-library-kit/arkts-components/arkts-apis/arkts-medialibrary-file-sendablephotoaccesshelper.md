# @ohos.file.sendablePhotoAccessHelper(Helper functions to access image and video assets)

The module provides APIs for album management, including creating an album and accessing and modifying media data in an album, based on a [Sendable](../../../arkts-utils/arkts-sendable.md) object.

**Since:** 12

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

## Modules to Import

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-getphotoaccesshelper-f.md) | Obtains a PhotoAccessHelper instance, which can be used for accessing and modifying media files in an album. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getPhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-getphotoaccesshelper-f-sys.md) | Obtains a PhotoAccessHelper instance for the specified user, letting you access and modify media files in an album. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-sendablephotoaccesshelper-absalbum-i.md) | Defines the abstract interface of albums. |
| [Album](arkts-medialibrary-sendablephotoaccesshelper-album-i.md) | Provides APIs to manage albums. |
| [FetchResult](arkts-medialibrary-sendablephotoaccesshelper-fetchresult-i.md) | Provides APIs to manage the file retrieval result. |
| [PhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-photoaccesshelper-i.md) | Helper functions to access photos and albums. |
| [PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md) | Provides APIs for encapsulating file asset attributes. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AbsAlbum](arkts-medialibrary-sendablephotoaccesshelper-absalbum-i-sys.md) | Defines the abstract interface of albums. |
| [Album](arkts-medialibrary-sendablephotoaccesshelper-album-i-sys.md) | Provides APIs to manage albums. |
| [PhotoAccessHelper](arkts-medialibrary-sendablephotoaccesshelper-photoaccesshelper-i-sys.md) | Helper functions to access photos and albums. |
| [PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i-sys.md) | Provides APIs for encapsulating file asset attributes. |
| [SharedPhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-sharedphotoasset-i-sys.md) | Defines the shared photo asset |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [AlbumSubtype](arkts-medialibrary-sendablephotoaccesshelper-albumsubtype-e.md) | Enumerate the album subtypes. |
| [AlbumType](arkts-medialibrary-sendablephotoaccesshelper-albumtype-e.md) | Enumerates the album types. |
| [DynamicRangeType](arkts-medialibrary-sendablephotoaccesshelper-dynamicrangetype-e.md) | Enumerates the dynamic range types of media assets. |
| [PhotoSubtype](arkts-medialibrary-sendablephotoaccesshelper-photosubtype-e.md) | Enumerates the [PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md) types. |
| [PhotoType](arkts-medialibrary-sendablephotoaccesshelper-phototype-e.md) | Enumerates media file types. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AlbumSubtype](arkts-medialibrary-sendablephotoaccesshelper-albumsubtype-e-sys.md) | Enumerate the album subtypes. |
| [AlbumType](arkts-medialibrary-sendablephotoaccesshelper-albumtype-e-sys.md) | Enumerates the album types. |
| [MovingPhotoEffectMode](arkts-medialibrary-sendablephotoaccesshelper-movingphotoeffectmode-e-sys.md) | Enumeration of moving photo effect mode. |
| [PhotoSubtype](arkts-medialibrary-sendablephotoaccesshelper-photosubtype-e-sys.md) | Enumerates the [PhotoAsset](arkts-medialibrary-sendablephotoaccesshelper-photoasset-i.md) types. |
| [PositionType](arkts-medialibrary-sendablephotoaccesshelper-positiontype-e-sys.md) | Photo asset position |
| [ThumbnailVisibility](arkts-medialibrary-sendablephotoaccesshelper-thumbnailvisibility-e-sys.md) | Ability to access thumbnail |
<!--DelEnd-->
