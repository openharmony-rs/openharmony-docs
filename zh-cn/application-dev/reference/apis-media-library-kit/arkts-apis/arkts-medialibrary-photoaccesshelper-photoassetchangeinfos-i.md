# PhotoAssetChangeInfos

媒体资产（图片/视频）的变更通知信息。

**起始版本：** 23

<!--Device-photoAccessHelper-interface PhotoAssetChangeInfos--><!--Device-photoAccessHelper-interface PhotoAssetChangeInfos-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## assetChangeDatas

```TypeScript
assetChangeDatas: PhotoAssetChangeData[] | null
```

变更的媒体资产（图片/视频）数组。如果需要重新查询所有媒体资产，assetChangeDatas为null。

**类型：** [PhotoAssetChangeData](arkts-medialibrary-photoaccesshelper-photoassetchangedata-i.md)[] \| null

**起始版本：** 23

<!--Device-PhotoAssetChangeInfos-assetChangeDatas: PhotoAssetChangeData[] | null--><!--Device-PhotoAssetChangeInfos-assetChangeDatas: PhotoAssetChangeData[] | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isForRecheck

```TypeScript
isForRecheck: boolean
```

应用是否应该重新查询所有媒体资产（图片/视频）信息。true表示需要重新查询所有资产，false表示无需查询所有资产。 **注意：** 在大量资产操作或者异常通知的场景下，应用收到的isForRecheck为true，表示重新查询所有资产信息。

**类型：** boolean

**起始版本：** 23

<!--Device-PhotoAssetChangeInfos-isForRecheck: boolean--><!--Device-PhotoAssetChangeInfos-isForRecheck: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## type

```TypeScript
type: NotifyChangeType
```

媒体资产（图片/视频）变更的通知类型。

**类型：** [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e.md)

**起始版本：** 23

<!--Device-PhotoAssetChangeInfos-type: NotifyChangeType--><!--Device-PhotoAssetChangeInfos-type: NotifyChangeType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

