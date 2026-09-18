# SharedPhotoAsset (System API)

Defines the shared photo asset

**Inheritance/Implementation:** SharedPhotoAsset extends lang.ISendable

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { sendablePhotoAccessHelper } from '@kit.MediaLibraryKit';
```

## cameraShotKey

```TypeScript
cameraShotKey: string
```

Camera shot key of photo asset

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## data

```TypeScript
data: string
```

Path data of photo asset

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateAdded

```TypeScript
dateAdded: number
```

Added date of photo asset Unit: ms, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateAddedMs

```TypeScript
dateAddedMs: number
```

Added date of photo asset in milliseconds

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateDay

```TypeScript
dateDay: string
```

The day of the file created

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateModified

```TypeScript
dateModified: number
```

Modify date of photo asset Unit: ms, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateModifiedMs

```TypeScript
dateModifiedMs: number
```

Modified time of the asset in milliseconds

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateMonth

```TypeScript
dateMonth: string
```

The month of the file created

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTaken

```TypeScript
dateTaken: number
```

DateTaken of photo asset Unit: ms, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTrashed

```TypeScript
dateTrashed: number
```

Trashed date of photo asset

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateTrashedMs

```TypeScript
dateTrashedMs: number
```

Trashed time of the asset in milliseconds

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dateYear

```TypeScript
dateYear: string
```

The year of the file created

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## displayName

```TypeScript
displayName: string
```

Display name of photo asset

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## duration

```TypeScript
duration: number
```

Duration of video photo asset Unit: ms, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## dynamicRangeType

```TypeScript
dynamicRangeType: DynamicRangeType
```

Dynamic range type of the asset

**Type:** [DynamicRangeType](arkts-medialibrary-sendablephotoaccesshelper-dynamicrangetype-e.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## fileId

```TypeScript
fileId: number
```

File id of photo asset

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## height

```TypeScript
height: number
```

Height of photo asset Unit: px, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## hidden

```TypeScript
hidden: boolean
```

Hidden state of photo asset

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## isFavorite

```TypeScript
isFavorite: boolean
```

Favorite state of photo asset

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## lcdSize

```TypeScript
lcdSize: string
```

Width and height information of lcd picture

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## mediaType

```TypeScript
mediaType: PhotoType
```

Media type of photo asset

**Type:** [PhotoType](arkts-medialibrary-sendablephotoaccesshelper-phototype-e.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## movingPhotoEffectMode

```TypeScript
movingPhotoEffectMode: MovingPhotoEffectMode
```

Effect mode of moving photo

**Type:** [MovingPhotoEffectMode](arkts-medialibrary-sendablephotoaccesshelper-movingphotoeffectmode-e-sys.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## orientation

```TypeScript
orientation: number
```

Orientation of photo asset Unit: deg, The value must be an integer within [0,359].

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## pending

```TypeScript
pending: boolean
```

Pending state of the asset, true means asset is pending

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## position

```TypeScript
position: PositionType
```

Position of photo asset

**Type:** [PositionType](arkts-medialibrary-photoaccesshelper-positiontype-e.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## size

```TypeScript
size: number
```

Size of photo asset Unit: Byte, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## subtype

```TypeScript
subtype: PhotoSubtype
```

Subtype of photo asset

**Type:** [PhotoSubtype](arkts-medialibrary-sendablephotoaccesshelper-photosubtype-e.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thmSize

```TypeScript
thmSize: string
```

Width and height information of thumbnail picture

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thumbnailModifiedMs

```TypeScript
thumbnailModifiedMs: number
```

modified time of thumbnail status

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thumbnailReady

```TypeScript
thumbnailReady: boolean
```

Ready state of thumbnail

**Type:** boolean

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## thumbnailVisible

```TypeScript
thumbnailVisible: ThumbnailVisibility
```

visibility of thumbnails

**Type:** [ThumbnailVisibility](arkts-medialibrary-sendablephotoaccesshelper-thumbnailvisibility-e-sys.md)

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## title

```TypeScript
title: string
```

Title of photo asset

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## uri

```TypeScript
uri: string
```

URI of photo asset

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## userComment

```TypeScript
userComment: string
```

User comment info of photo asset

**Type:** string

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.

## width

```TypeScript
width: number
```

Width of photo asset Unit: px, The value must be an integer greater than or equal to 0.

**Type:** number

**Since:** 14

**System capability:** SystemCapability.FileManagement.PhotoAccessHelper.Core

**System API:** This is a system API.
