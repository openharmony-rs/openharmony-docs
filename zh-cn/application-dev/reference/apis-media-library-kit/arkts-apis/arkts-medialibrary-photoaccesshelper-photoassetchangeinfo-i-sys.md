# PhotoAssetChangeInfo

媒体资产（图片/视频）信息。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoAssetChangeInfo--><!--Device-photoAccessHelper-interface PhotoAssetChangeInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumChangeInfos

```TypeScript
albumChangeInfos?: AlbumChangeInfo[] | null
```

智慧相册的相册变更信息。

**类型：** [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md)[] \| null

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAssetChangeInfo-albumChangeInfos?: AlbumChangeInfo[] | null--><!--Device-PhotoAssetChangeInfo-albumChangeInfos?: AlbumChangeInfo[] | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## assetSourceType

```TypeScript
assetSourceType?: AssetSourceType
```

资产来源类型 默认值： 0。

**类型：** [AssetSourceType](arkts-medialibrary-photoaccesshelper-assetsourcetype-e-sys.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAssetChangeInfo-assetSourceType?: AssetSourceType--><!--Device-PhotoAssetChangeInfo-assetSourceType?: AssetSourceType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateAddedMs

```TypeScript
dateAddedMs: long
```

文件创建时的Unix时间戳（单位：毫秒）。

**类型：** long

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-dateAddedMs: long--><!--Device-PhotoAssetChangeInfo-dateAddedMs: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateDay

```TypeScript
dateDay: string
```

创建媒体文件的日期。

**类型：** string

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-dateDay: string--><!--Device-PhotoAssetChangeInfo-dateDay: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateModifiedMs

```TypeScript
dateModifiedMs?: long
```

文件修改时的Unix时间戳。 <br> 单位为毫秒。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAssetChangeInfo-dateModifiedMs?: long--><!--Device-PhotoAssetChangeInfo-dateModifiedMs?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTakenMs

```TypeScript
dateTakenMs: long
```

文件拍摄时的Unix时间戳（单位：毫秒）。

**类型：** long

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-dateTakenMs: long--><!--Device-PhotoAssetChangeInfo-dateTakenMs: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## dateTrashedMs

```TypeScript
dateTrashedMs: long
```

文件删除时的Unix时间戳（单位：毫秒）。

**类型：** long

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-dateTrashedMs: long--><!--Device-PhotoAssetChangeInfo-dateTrashedMs: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## displayName

```TypeScript
displayName?: string
```

媒体资产（图片/视频）的显示名称。

**类型：** string

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-displayName?: string--><!--Device-PhotoAssetChangeInfo-displayName?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## fileId

```TypeScript
fileId: int
```

媒体资产（图片/视频）的id。

**类型：** int

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-fileId: int--><!--Device-PhotoAssetChangeInfo-fileId: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hiddenTime

```TypeScript
hiddenTime?: long
```

媒体资产（图片/视频）的隐藏时间。 <br> 单位为毫秒。

**类型：** long

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-PhotoAssetChangeInfo-hiddenTime?: long--><!--Device-PhotoAssetChangeInfo-hiddenTime?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## isFavorite

```TypeScript
isFavorite: boolean
```

表示媒体资产（图片/视频）的收藏状态。true表示资产已收藏，false表示资产未收藏。

**类型：** boolean

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-isFavorite: boolean--><!--Device-PhotoAssetChangeInfo-isFavorite: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## isHidden

```TypeScript
isHidden: boolean
```

表示媒体资产（图片/视频）的隐藏状态。true表示资产已隐藏，false表示资产未隐藏。

**类型：** boolean

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-isHidden: boolean--><!--Device-PhotoAssetChangeInfo-isHidden: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## position

```TypeScript
position?: PositionType
```

媒体资产（图片/视频）的所在位置。

**类型：** PositionType

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-position?: PositionType--><!--Device-PhotoAssetChangeInfo-position?: PositionType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## size

```TypeScript
size?: long
```

媒体资产（图片/视频）的文件大小（单位：字节）。动态照片的size包括图片和视频的总大小。

**类型：** long

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-size?: long--><!--Device-PhotoAssetChangeInfo-size?: long-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## strongAssociation

```TypeScript
strongAssociation: StrongAssociationType
```

图片的强关联类型。

**类型：** [StrongAssociationType](arkts-medialibrary-photoaccesshelper-strongassociationtype-e-sys.md)

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-strongAssociation: StrongAssociationType--><!--Device-PhotoAssetChangeInfo-strongAssociation: StrongAssociationType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## thumbnailVisible

```TypeScript
thumbnailVisible: ThumbnailVisibility
```

缩略图的可访问性。

**类型：** ThumbnailVisibility

**起始版本：** 23

<!--Device-PhotoAssetChangeInfo-thumbnailVisible: ThumbnailVisibility--><!--Device-PhotoAssetChangeInfo-thumbnailVisible: ThumbnailVisibility-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

