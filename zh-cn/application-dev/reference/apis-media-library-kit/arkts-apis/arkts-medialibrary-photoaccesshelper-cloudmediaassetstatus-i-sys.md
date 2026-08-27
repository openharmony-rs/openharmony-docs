# CloudMediaAssetStatus（系统接口）

云端媒体资产下载任务的详细信息，应用调用云端资产下载任务查询接口的返回类型。

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { photoAccessHelper } from '@kit.MediaLibraryKit';
```

## errorCode

```TypeScript
readonly errorCode: CloudMediaTaskPauseCause
```

云端媒体资产下载任务暂停类型。

**类型：** [CloudMediaTaskPauseCause](arkts-medialibrary-photoaccesshelper-cloudmediataskpausecause-e-sys.md)

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## taskInfo

```TypeScript
readonly taskInfo: string
```

下载资产的总个数和总大小（byte），以及未下载的总个数和总大小（byte）。

**类型：** string

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。

## taskStatus

```TypeScript
readonly taskStatus: CloudMediaAssetTaskStatus
```

云端媒体资产下载任务状态。

**类型：** [CloudMediaAssetTaskStatus](arkts-medialibrary-photoaccesshelper-cloudmediaassettaskstatus-e-sys.md)

**起始版本：** 14

**系统能力：** SystemCapability.FileManagement.PhotoAccessHelper.Core

**系统接口：** 此接口为系统接口。
