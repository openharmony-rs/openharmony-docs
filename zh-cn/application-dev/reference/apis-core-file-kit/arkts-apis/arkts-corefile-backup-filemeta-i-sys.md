# FileMeta（系统接口）

文件的元数据，包含应用名称及文件URI，在与备份服务进行IPC时使用。

**起始版本：** 10

<!--Device-backup-interface FileMeta--><!--Device-backup-interface FileMeta-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { backup } from '@kit.CoreFileKit';
```

## bundleName

```TypeScript
bundleName: string
```

应用名称。

**类型：** string

**起始版本：** 10

<!--Device-FileMeta-bundleName: string--><!--Device-FileMeta-bundleName: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## uri

```TypeScript
uri: string
```

应用沙箱内待传输文件的名称。

**类型：** string

**起始版本：** 10

<!--Device-FileMeta-uri: string--><!--Device-FileMeta-uri: string-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

## uris

```TypeScript
uris?: Array<string>
```

应用沙箱内待传输文件的名称数组。

**类型：** Array&lt;string&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-FileMeta-uris?: Array<string>--><!--Device-FileMeta-uris?: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.StorageService.Backup

**系统接口：** 此接口为系统接口。

