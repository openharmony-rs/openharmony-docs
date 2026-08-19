# LocalFilePresentStatus（系统接口）

检测结果对象，包含应用包名及其在云盘存储空间内是否存在未上云文件的状态信息。

**起始版本：** 23

<!--Device-cloudSyncManager-interface LocalFilePresentStatus--><!--Device-cloudSyncManager-interface LocalFilePresentStatus-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { cloudSyncManager } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

应用包名。

**类型：** string

**起始版本：** 23

<!--Device-LocalFilePresentStatus-bundleName: string--><!--Device-LocalFilePresentStatus-bundleName: string-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

## isLocalFilePresent

```TypeScript
isLocalFilePresent: boolean
```

该应用在云盘存储空间内是否存在尚未同步至云端的本地文件。true 表示存在， false 表示不存在。

**类型：** boolean

**起始版本：** 23

<!--Device-LocalFilePresentStatus-isLocalFilePresent: boolean--><!--Device-LocalFilePresentStatus-isLocalFilePresent: boolean-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSyncManager

**系统接口：** 此接口为系统接口。

