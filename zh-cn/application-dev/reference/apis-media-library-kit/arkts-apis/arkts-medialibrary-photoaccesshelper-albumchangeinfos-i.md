# AlbumChangeInfos

相册的变更通知信息。

**起始版本：** 23

<!--Device-photoAccessHelper-interface AlbumChangeInfos--><!--Device-photoAccessHelper-interface AlbumChangeInfos-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumChangeDatas

```TypeScript
albumChangeDatas: AlbumChangeData[] | null
```

变更的相册数组。如果需要重新查询所有相册，albumChangeDatas为null。

**类型：** [AlbumChangeData](arkts-medialibrary-photoaccesshelper-albumchangedata-i.md)[] \| null

**起始版本：** 23

<!--Device-AlbumChangeInfos-albumChangeDatas: AlbumChangeData[] | null--><!--Device-AlbumChangeInfos-albumChangeDatas: AlbumChangeData[] | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## isForRecheck

```TypeScript
isForRecheck: boolean
```

应用是否应该重新查询所有媒体资产（图片/视频）信息。true表示需要重新查询所有资产，false表示无需查询所有资产。 **注意：** 在大量资产操作或者异常通知的场景下，应用收到的isForRecheck为true，表示重新查询所有资产信息。

**类型：** boolean

**起始版本：** 23

<!--Device-AlbumChangeInfos-isForRecheck: boolean--><!--Device-AlbumChangeInfos-isForRecheck: boolean-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## type

```TypeScript
type: NotifyChangeType
```

相册变更的通知类型。

**类型：** [NotifyChangeType](arkts-medialibrary-photoaccesshelper-notifychangetype-e.md)

**起始版本：** 23

<!--Device-AlbumChangeInfos-type: NotifyChangeType--><!--Device-AlbumChangeInfos-type: NotifyChangeType-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

