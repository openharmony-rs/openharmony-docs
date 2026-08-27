# SharedPhotoAsset（系统接口）

Defines the shared photo asset

**继承/实现关系：** SharedPhotoAsset extends lang.ISendable

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## cameraShotKey

```TypeScript
cameraShotKey: string
```

Camera shot key of photo asset

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## data

```TypeScript
data: string
```

Path data of photo asset

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateAdded

```TypeScript
dateAdded: number
```

Added date of photo asset 单位为： ms，取值应为≥0的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateAddedMs

```TypeScript
dateAddedMs: number
```

Added date of photo asset in milliseconds

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateDay

```TypeScript
dateDay: string
```

The day of the file created

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateModified

```TypeScript
dateModified: number
```

Modify date of photo asset 单位为： ms，取值应为≥0的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateModifiedMs

```TypeScript
dateModifiedMs: number
```

Modified time of the asset in milliseconds

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateMonth

```TypeScript
dateMonth: string
```

The month of the file created

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTaken

```TypeScript
dateTaken: number
```

DateTaken of photo asset 单位为： ms，取值应为≥0的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTrashed

```TypeScript
dateTrashed: number
```

Trashed date of photo asset

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTrashedMs

```TypeScript
dateTrashedMs: number
```

Trashed time of the asset in milliseconds

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateYear

```TypeScript
dateYear: string
```

The year of the file created

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## displayName

```TypeScript
displayName: string
```

Display name of photo asset

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## duration

```TypeScript
duration: number
```

Duration of video photo asset 单位为： ms，取值应为≥0的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dynamicRangeType

```TypeScript
dynamicRangeType: DynamicRangeType
```

Dynamic range type of the asset

**类型：** DynamicRangeType

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## fileId

```TypeScript
fileId: number
```

File id of photo asset

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## height

```TypeScript
height: number
```

Height of photo asset 单位为： px，取值应为≥0的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hidden

```TypeScript
hidden: boolean
```

Hidden state of photo asset

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## isFavorite

```TypeScript
isFavorite: boolean
```

Favorite state of photo asset

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## lcdSize

```TypeScript
lcdSize: string
```

Width and height information of lcd picture

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## mediaType

```TypeScript
mediaType: PhotoType
```

Media type of photo asset

**类型：** PhotoType

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## movingPhotoEffectMode

```TypeScript
movingPhotoEffectMode: MovingPhotoEffectMode
```

Effect mode of moving photo

**类型：** MovingPhotoEffectMode

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## orientation

```TypeScript
orientation: number
```

Orientation of photo asset 单位为： deg，取值应为[0,359]内的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## pending

```TypeScript
pending: boolean
```

Pending state of the asset, true means asset is pending

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position: PositionType
```

Position of photo asset

**类型：** PositionType

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size: number
```

Size of photo asset 单位为： Byte，取值应为≥0的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## subtype

```TypeScript
subtype: PhotoSubtype
```

Subtype of photo asset

**类型：** PhotoSubtype

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thmSize

```TypeScript
thmSize: string
```

Width and height information of thumbnail picture

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thumbnailModifiedMs

```TypeScript
thumbnailModifiedMs: number
```

modified time of thumbnail status

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thumbnailReady

```TypeScript
thumbnailReady: boolean
```

Ready state of thumbnail

**类型：** boolean

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thumbnailVisible

```TypeScript
thumbnailVisible: ThumbnailVisibility
```

visibility of thumbnails

**类型：** ThumbnailVisibility

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## title

```TypeScript
title: string
```

Title of photo asset

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

URI of photo asset

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## userComment

```TypeScript
userComment: string
```

User comment info of photo asset

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## width

```TypeScript
width: number
```

Width of photo asset 单位为： px，取值应为≥0的整数。

**类型：** number

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
