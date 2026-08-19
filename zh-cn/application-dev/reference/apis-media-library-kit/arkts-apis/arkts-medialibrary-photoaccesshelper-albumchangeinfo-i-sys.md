# AlbumChangeInfo

相册信息。

**起始版本：** 23

<!--Device-photoAccessHelper-interface AlbumChangeInfo--><!--Device-photoAccessHelper-interface AlbumChangeInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumOrder

```TypeScript
albumOrder?: int
```

相册的排序值。

**类型：** int

**起始版本：** 23

<!--Device-AlbumChangeInfo-albumOrder?: int--><!--Device-AlbumChangeInfo-albumOrder?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## coverInfo

```TypeScript
coverInfo?: PhotoAssetChangeInfo
```

相册封面资产的信息。

**类型：** [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md)

**起始版本：** 23

<!--Device-AlbumChangeInfo-coverInfo?: PhotoAssetChangeInfo--><!--Device-AlbumChangeInfo-coverInfo?: PhotoAssetChangeInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hidden

```TypeScript
hidden?: boolean
```

相册是否为隐藏状态。true表示相册为隐藏状态，false表示相册不为隐藏状态。

**类型：** boolean

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlbumChangeInfo-hidden?: boolean--><!--Device-AlbumChangeInfo-hidden?: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hiddenCount

```TypeScript
hiddenCount: int
```

相册中的隐藏资产数量。

**类型：** int

**起始版本：** 23

<!--Device-AlbumChangeInfo-hiddenCount: int--><!--Device-AlbumChangeInfo-hiddenCount: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hiddenCoverInfo

```TypeScript
hiddenCoverInfo?: PhotoAssetChangeInfo
```

相册隐藏封面资产的信息。

**类型：** [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md)

**起始版本：** 23

<!--Device-AlbumChangeInfo-hiddenCoverInfo?: PhotoAssetChangeInfo--><!--Device-AlbumChangeInfo-hiddenCoverInfo?: PhotoAssetChangeInfo-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## hiddenCoverUri

```TypeScript
hiddenCoverUri: string
```

相册中隐藏封面资产的uri。

**类型：** string

**起始版本：** 23

<!--Device-AlbumChangeInfo-hiddenCoverUri: string--><!--Device-AlbumChangeInfo-hiddenCoverUri: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## isCoverChanged

```TypeScript
isCoverChanged: boolean
```

相册封面文件内容是否变化。true表示封面文件内容发生变化，false表示封面文件内容未发生变化。

**类型：** boolean

**起始版本：** 23

<!--Device-AlbumChangeInfo-isCoverChanged: boolean--><!--Device-AlbumChangeInfo-isCoverChanged: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## isHiddenCoverChanged

```TypeScript
isHiddenCoverChanged: boolean
```

相册隐藏封面文件内容是否变化。true表示隐藏封面文件内容发生变化，false表示隐藏封面文件内容未发生变化。

**类型：** boolean

**起始版本：** 23

<!--Device-AlbumChangeInfo-isHiddenCoverChanged: boolean--><!--Device-AlbumChangeInfo-isHiddenCoverChanged: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## lpath

```TypeScript
lpath?: string
```

相册虚拟路径。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-AlbumChangeInfo-lpath?: string--><!--Device-AlbumChangeInfo-lpath?: string-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## orderSection

```TypeScript
orderSection?: int
```

相册的排序区域，用于确认相册在图库中的展示区域。

**类型：** int

**起始版本：** 23

<!--Device-AlbumChangeInfo-orderSection?: int--><!--Device-AlbumChangeInfo-orderSection?: int-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

