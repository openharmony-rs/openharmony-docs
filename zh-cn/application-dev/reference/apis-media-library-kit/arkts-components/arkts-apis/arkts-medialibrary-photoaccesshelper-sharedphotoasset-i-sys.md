# SharedPhotoAsset（系统接口）

```TypeScript
interface SharedPhotoAsset
```

共享图片资产。

**起始版本：** 13

<!--Device-photoAccessHelper-interface SharedPhotoAsset--><!--Device-photoAccessHelper-interface SharedPhotoAsset-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## cameraShotKey

```TypeScript
cameraShotKey: string
```

图片资产相机拍摄信息。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-cameraShotKey: string--><!--Device-SharedPhotoAsset-cameraShotKey: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: string
```

图片资产的路径数据。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-data: string--><!--Device-SharedPhotoAsset-data: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateAdded

```TypeScript
dateAdded: number
```

添加了图片资产数据，单位：秒。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateAdded: long--><!--Device-SharedPhotoAsset-dateAdded: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateAddedMs

```TypeScript
dateAddedMs: number
```

图片资产数据添加后经过时间，单位：毫秒。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateAddedMs: long--><!--Device-SharedPhotoAsset-dateAddedMs: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateDay

```TypeScript
dateDay: string
```

图片资产创建日时间。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateDay: string--><!--Device-SharedPhotoAsset-dateDay: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateModified

```TypeScript
dateModified: number
```

更改了图片资产数据，单位：秒。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateModified: long--><!--Device-SharedPhotoAsset-dateModified: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateModifiedMs

```TypeScript
dateModifiedMs: number
```

文件修改时的Unix时间戳。单位为毫秒。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateModifiedMs: long--><!--Device-SharedPhotoAsset-dateModifiedMs: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateMonth

```TypeScript
dateMonth: string
```

图片资产创建月份时间。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateMonth: string--><!--Device-SharedPhotoAsset-dateMonth: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTaken

```TypeScript
dateTaken: number
```

图片资产拍照后存入本地时间，单位：秒。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateTaken: long--><!--Device-SharedPhotoAsset-dateTaken: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTrashed

```TypeScript
dateTrashed: number
```

图片资产是否在回收站中。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateTrashed: long--><!--Device-SharedPhotoAsset-dateTrashed: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTrashedMs

```TypeScript
dateTrashedMs: number
```

图片资产数据进回收站后经过时间，单位：毫秒。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateTrashedMs: long--><!--Device-SharedPhotoAsset-dateTrashedMs: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateYear

```TypeScript
dateYear: string
```

图片资产创建年份时间。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-dateYear: string--><!--Device-SharedPhotoAsset-dateYear: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## displayName

```TypeScript
displayName: string
```

图片资产的显示名称。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-displayName: string--><!--Device-SharedPhotoAsset-displayName: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## duration

```TypeScript
duration: number
```

视频类型的图片资产时长，单位：毫秒。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-duration: int--><!--Device-SharedPhotoAsset-duration: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dynamicRangeType

```TypeScript
dynamicRangeType: DynamicRangeType
```

媒体文件的动态范围类型。

**类型：** [DynamicRangeType](arkts-medialibrary-photoaccesshelper-dynamicrangetype-e.md)

**起始版本：** 13

<!--Device-SharedPhotoAsset-dynamicRangeType: DynamicRangeType--><!--Device-SharedPhotoAsset-dynamicRangeType: DynamicRangeType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## fileId

```TypeScript
fileId: number
```

图片资产标识id。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-fileId: int--><!--Device-SharedPhotoAsset-fileId: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## height

```TypeScript
height: number
```

图片资产的像素高度，单位：像素。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-height: int--><!--Device-SharedPhotoAsset-height: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hidden

```TypeScript
hidden: boolean
```

图片资产是否隐藏。true表示已隐藏，false表示未隐藏。

**类型：** boolean

**起始版本：** 13

<!--Device-SharedPhotoAsset-hidden: boolean--><!--Device-SharedPhotoAsset-hidden: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## isFavorite

```TypeScript
isFavorite: boolean
```

是否收藏了此图片。true表示已收藏，false表示未收藏。

**类型：** boolean

**起始版本：** 13

<!--Device-SharedPhotoAsset-isFavorite: boolean--><!--Device-SharedPhotoAsset-isFavorite: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## lcdSize

```TypeScript
lcdSize: string
```

图片资产的lcd缩略图宽高信息。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-lcdSize: string--><!--Device-SharedPhotoAsset-lcdSize: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## mediaType

```TypeScript
mediaType: PhotoType
```

图片资产的媒体类型。

**类型：** [PhotoType](arkts-medialibrary-photoaccesshelper-phototype-e.md)

**起始版本：** 13

<!--Device-SharedPhotoAsset-mediaType: PhotoType--><!--Device-SharedPhotoAsset-mediaType: PhotoType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## movingPhotoEffectMode

```TypeScript
movingPhotoEffectMode: MovingPhotoEffectMode
```

动态照片效果模式。

**类型：** [MovingPhotoEffectMode](arkts-medialibrary-photoaccesshelper-movingphotoeffectmode-e-sys.md)

**起始版本：** 13

<!--Device-SharedPhotoAsset-movingPhotoEffectMode: MovingPhotoEffectMode--><!--Device-SharedPhotoAsset-movingPhotoEffectMode: MovingPhotoEffectMode-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## orientation

```TypeScript
orientation: number
```

图片资产的旋转角度，单位：度（°）。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-orientation: int--><!--Device-SharedPhotoAsset-orientation: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## pending

```TypeScript
pending: boolean
```

图片资产等待状态，true表示等待，false表示解除等待。

**类型：** boolean

**起始版本：** 13

<!--Device-SharedPhotoAsset-pending: boolean--><!--Device-SharedPhotoAsset-pending: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: PositionType
```

图片资产存在位置。

**类型：** [PositionType](arkts-medialibrary-photoaccesshelper-positiontype-e.md)

**起始版本：** 13

<!--Device-SharedPhotoAsset-position: PositionType--><!--Device-SharedPhotoAsset-position: PositionType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

图片资产文件大小，单位：字节。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-size: long--><!--Device-SharedPhotoAsset-size: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## subtype

```TypeScript
subtype: PhotoSubtype
```

图片资产子类型。

**类型：** [PhotoSubtype](arkts-medialibrary-photoaccesshelper-photosubtype-e.md)

**起始版本：** 13

<!--Device-SharedPhotoAsset-subtype: PhotoSubtype--><!--Device-SharedPhotoAsset-subtype: PhotoSubtype-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thmSize

```TypeScript
thmSize: string
```

图片资产的thumb缩略图宽高信息。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-thmSize: string--><!--Device-SharedPhotoAsset-thmSize: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thumbnailModifiedMs

```TypeScript
thumbnailModifiedMs?: number
```

图片资产的缩略图状态改变后经过时间，单位：毫秒。

**类型：** number

**起始版本：** 14

<!--Device-SharedPhotoAsset-thumbnailModifiedMs?: long--><!--Device-SharedPhotoAsset-thumbnailModifiedMs?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thumbnailReady

```TypeScript
thumbnailReady: boolean
```

图片资产的缩略图是否准备好。true表示已准备好，false表示未准备好。

**类型：** boolean

**起始版本：** 13

<!--Device-SharedPhotoAsset-thumbnailReady: boolean--><!--Device-SharedPhotoAsset-thumbnailReady: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thumbnailVisible

```TypeScript
thumbnailVisible: ThumbnailVisibility
```

缩略图可见标识。

**类型：** [ThumbnailVisibility](arkts-medialibrary-photoaccesshelper-thumbnailvisibility-e-sys.md)

**起始版本：** 14

<!--Device-SharedPhotoAsset-thumbnailVisible: ThumbnailVisibility--><!--Device-SharedPhotoAsset-thumbnailVisible: ThumbnailVisibility-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## title

```TypeScript
title: string
```

图片资产的标题。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-title: string--><!--Device-SharedPhotoAsset-title: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

图片资产uri。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-uri: string--><!--Device-SharedPhotoAsset-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## userComment

```TypeScript
userComment: string
```

图片资产的用户评论信息。

**类型：** string

**起始版本：** 13

<!--Device-SharedPhotoAsset-userComment: string--><!--Device-SharedPhotoAsset-userComment: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## width

```TypeScript
width: number
```

图片资产的像素宽度，单位：像素。

**类型：** number

**起始版本：** 13

<!--Device-SharedPhotoAsset-width: int--><!--Device-SharedPhotoAsset-width: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
