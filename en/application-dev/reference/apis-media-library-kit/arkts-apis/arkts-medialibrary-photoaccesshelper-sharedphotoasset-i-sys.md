# SharedPhotoAsset (System API)

```TypeScript
interface SharedPhotoAsset
```

Describes the information about a shared media asset.

**Since:** 13

<!--Device-photoAccessHelper-interface SharedPhotoAsset--><!--Device-photoAccessHelper-interface SharedPhotoAsset-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cameraShotKey

```TypeScript
cameraShotKey: string
```

Camera shot information of the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-cameraShotKey: string--><!--Device-SharedPhotoAsset-cameraShotKey: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## data

```TypeScript
data: string
```

Path data of the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-data: string--><!--Device-SharedPhotoAsset-data: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateAdded

```TypeScript
dateAdded: number
```

Data added to the media asset.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-dateAdded: long--><!--Device-SharedPhotoAsset-dateAdded: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateAddedMs

```TypeScript
dateAddedMs: number
```

Time elapsed after the media asset was added.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-dateAddedMs: long--><!--Device-SharedPhotoAsset-dateAddedMs: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateDay

```TypeScript
dateDay: string
```

Time when the media asset was created.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-dateDay: string--><!--Device-SharedPhotoAsset-dateDay: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateModified

```TypeScript
dateModified: number
```

Data modified in the media asset.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-dateModified: long--><!--Device-SharedPhotoAsset-dateModified: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateModifiedMs

```TypeScript
dateModifiedMs: number
```

Modified time of the asset in milliseconds

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-dateModifiedMs: long--><!--Device-SharedPhotoAsset-dateModifiedMs: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateMonth

```TypeScript
dateMonth: string
```

Month when the media asset was created.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-dateMonth: string--><!--Device-SharedPhotoAsset-dateMonth: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTaken

```TypeScript
dateTaken: number
```

Timestamp when the media asset was taken and stored locally.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-dateTaken: long--><!--Device-SharedPhotoAsset-dateTaken: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTrashed

```TypeScript
dateTrashed: number
```

Whether the media asset is moved to the trash.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-dateTrashed: long--><!--Device-SharedPhotoAsset-dateTrashed: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTrashedMs

```TypeScript
dateTrashedMs: number
```

Time elapsed since the media asset was trashed.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-dateTrashedMs: long--><!--Device-SharedPhotoAsset-dateTrashedMs: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateYear

```TypeScript
dateYear: string
```

Year when the media asset was created.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-dateYear: string--><!--Device-SharedPhotoAsset-dateYear: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## displayName

```TypeScript
displayName: string
```

Display name of the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-displayName: string--><!--Device-SharedPhotoAsset-displayName: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## duration

```TypeScript
duration: number
```

Duration of the media asset if it is a video.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-duration: int--><!--Device-SharedPhotoAsset-duration: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dynamicRangeType

```TypeScript
dynamicRangeType: DynamicRangeType
```

Dynamic range type of the media asset.

**Type:** [DynamicRangeType](arkts-medialibrary-photoaccesshelper-dynamicrangetype-e.md)

**Since:** 13

<!--Device-SharedPhotoAsset-dynamicRangeType: DynamicRangeType--><!--Device-SharedPhotoAsset-dynamicRangeType: DynamicRangeType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## fileId

```TypeScript
fileId: number
```

ID of the media asset.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-fileId: int--><!--Device-SharedPhotoAsset-fileId: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## height

```TypeScript
height: number
```

Pixel height of the media asset.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-height: int--><!--Device-SharedPhotoAsset-height: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hidden

```TypeScript
hidden: boolean
```

Whether the media asset is hidden. **true** if hidden, **false** otherwise.

**Type:** boolean

**Since:** 13

<!--Device-SharedPhotoAsset-hidden: boolean--><!--Device-SharedPhotoAsset-hidden: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## isFavorite

```TypeScript
isFavorite: boolean
```

Whether the media asset is marked as a favorite. **true** if marked, **false** otherwise.

**Type:** boolean

**Since:** 13

<!--Device-SharedPhotoAsset-isFavorite: boolean--><!--Device-SharedPhotoAsset-isFavorite: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## lcdSize

```TypeScript
lcdSize: string
```

Width and height of the LCD thumbnail of the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-lcdSize: string--><!--Device-SharedPhotoAsset-lcdSize: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## mediaType

```TypeScript
mediaType: PhotoType
```

Media type of the media asset.

**Type:** [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md)

**Since:** 13

<!--Device-SharedPhotoAsset-mediaType: PhotoType--><!--Device-SharedPhotoAsset-mediaType: PhotoType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## movingPhotoEffectMode

```TypeScript
movingPhotoEffectMode: MovingPhotoEffectMode
```

Effect of the moving photo.

**Type:** [MovingPhotoEffectMode](arkts-medialibrary-photoaccesshelper-movingphotoeffectmode-e-sys.md)

**Since:** 13

<!--Device-SharedPhotoAsset-movingPhotoEffectMode: MovingPhotoEffectMode--><!--Device-SharedPhotoAsset-movingPhotoEffectMode: MovingPhotoEffectMode-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## orientation

```TypeScript
orientation: number
```

Rotation angle of the media asset.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-orientation: int--><!--Device-SharedPhotoAsset-orientation: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## pending

```TypeScript
pending: boolean
```

Whether the media asset is in a pending state. **true** if pending, **false** otherwise.

**Type:** boolean

**Since:** 13

<!--Device-SharedPhotoAsset-pending: boolean--><!--Device-SharedPhotoAsset-pending: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## position

```TypeScript
position: PositionType
```

Location of the media asset.

**Type:** [PositionType](arkts-medialibrary-photoaccesshelper-positiontype-e.md)

**Since:** 13

<!--Device-SharedPhotoAsset-position: PositionType--><!--Device-SharedPhotoAsset-position: PositionType-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## size

```TypeScript
size: number
```

File size of the media asset.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-size: long--><!--Device-SharedPhotoAsset-size: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## subtype

```TypeScript
subtype: PhotoSubtype
```

Subtype of the media asset.

**Type:** [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)

**Since:** 13

<!--Device-SharedPhotoAsset-subtype: PhotoSubtype--><!--Device-SharedPhotoAsset-subtype: PhotoSubtype-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thmSize

```TypeScript
thmSize: string
```

Width and height of the thumb thumbnail of the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-thmSize: string--><!--Device-SharedPhotoAsset-thmSize: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thumbnailModifiedMs

```TypeScript
thumbnailModifiedMs?: number
```

Time elapsed since the thumbnail status of the media asset changed.

**Type:** number

**Since:** 14

<!--Device-SharedPhotoAsset-thumbnailModifiedMs?: long--><!--Device-SharedPhotoAsset-thumbnailModifiedMs?: long-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thumbnailReady

```TypeScript
thumbnailReady: boolean
```

Whether the thumbnail of the media asset is ready. **true** if ready, **false** otherwise.

**Type:** boolean

**Since:** 13

<!--Device-SharedPhotoAsset-thumbnailReady: boolean--><!--Device-SharedPhotoAsset-thumbnailReady: boolean-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thumbnailVisible

```TypeScript
thumbnailVisible: ThumbnailVisibility
```

Whether the thumbnail of the media asset is visible.

**Type:** [ThumbnailVisibility](arkts-medialibrary-photoaccesshelper-thumbnailvisibility-e-sys.md)

**Since:** 14

<!--Device-SharedPhotoAsset-thumbnailVisible: ThumbnailVisibility--><!--Device-SharedPhotoAsset-thumbnailVisible: ThumbnailVisibility-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## title

```TypeScript
title: string
```

Title of the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-title: string--><!--Device-SharedPhotoAsset-title: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## uri

```TypeScript
uri: string
```

URI of the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-uri: string--><!--Device-SharedPhotoAsset-uri: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## userComment

```TypeScript
userComment: string
```

User comments on the media asset.

**Type:** string

**Since:** 13

<!--Device-SharedPhotoAsset-userComment: string--><!--Device-SharedPhotoAsset-userComment: string-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## width

```TypeScript
width: number
```

Pixel width of the media asset.

**Type:** number

**Since:** 13

<!--Device-SharedPhotoAsset-width: int--><!--Device-SharedPhotoAsset-width: int-End-->

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
