# PhotoAssetChangeData

媒体资产（图片/视频）的具体变更数据。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoAssetChangeData--><!--Device-photoAccessHelper-interface PhotoAssetChangeData-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## assetAfterChange

```TypeScript
assetAfterChange: PhotoAssetChangeInfo | null
```

变更后的媒体资产（图片/视频）数据。如果是删除资产，assetAfterChange为null。

**类型：** [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md) \| null

**起始版本：** 23

<!--Device-PhotoAssetChangeData-assetAfterChange: PhotoAssetChangeInfo | null--><!--Device-PhotoAssetChangeData-assetAfterChange: PhotoAssetChangeInfo | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## assetBeforeChange

```TypeScript
assetBeforeChange: PhotoAssetChangeInfo | null
```

变更前的媒体资产（图片/视频）数据。如果是新增资产，assetBeforeChange为null。

**类型：** [PhotoAssetChangeInfo](arkts-medialibrary-photoaccesshelper-photoassetchangeinfo-i.md) \| null

**起始版本：** 23

<!--Device-PhotoAssetChangeData-assetBeforeChange: PhotoAssetChangeInfo | null--><!--Device-PhotoAssetChangeData-assetBeforeChange: PhotoAssetChangeInfo | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isContentChanged

```TypeScript
isContentChanged: boolean
```

媒体资产（图片/视频）内容是否变化。true表示文件内容发生变化，false表示文件内容未发生变化。

**类型：** boolean

**起始版本：** 23

<!--Device-PhotoAssetChangeData-isContentChanged: boolean--><!--Device-PhotoAssetChangeData-isContentChanged: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isDeleted

```TypeScript
isDeleted: boolean
```

媒体资产（图片/视频）是否被删除。true表示资产被彻底删除，false表示资产未被彻底删除。

**类型：** boolean

**起始版本：** 23

<!--Device-PhotoAssetChangeData-isDeleted: boolean--><!--Device-PhotoAssetChangeData-isDeleted: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

