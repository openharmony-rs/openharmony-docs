# AlbumChangeData

相册的具体变更数据。

**起始版本：** 23

<!--Device-photoAccessHelper-interface AlbumChangeData--><!--Device-photoAccessHelper-interface AlbumChangeData-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## albumAfterChange

```TypeScript
albumAfterChange: AlbumChangeInfo | null
```

变更后的相册数据。如果是删除相册，albumAfterChange为null。

**类型：** [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md) \| null

**起始版本：** 23

<!--Device-AlbumChangeData-albumAfterChange: AlbumChangeInfo | null--><!--Device-AlbumChangeData-albumAfterChange: AlbumChangeInfo | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

## albumBeforeChange

```TypeScript
albumBeforeChange: AlbumChangeInfo | null
```

变更前的相册数据。如果是新增相册，albumBeforeChange为null。

**类型：** [AlbumChangeInfo](arkts-medialibrary-photoaccesshelper-albumchangeinfo-i.md) \| null

**起始版本：** 23

<!--Device-AlbumChangeData-albumBeforeChange: AlbumChangeInfo | null--><!--Device-AlbumChangeData-albumBeforeChange: AlbumChangeInfo | null-End-->

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

