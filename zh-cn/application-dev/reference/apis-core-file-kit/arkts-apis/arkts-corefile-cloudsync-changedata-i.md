# ChangeData

定义变更数据。

**起始版本：** 12

<!--Device-cloudSync-interface ChangeData--><!--Device-cloudSync-interface ChangeData-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## 导入模块

```TypeScript
import { cloudSync } from '@kit.CoreFileKit';
```

## isDirectory

```TypeScript
isDirectory: Array<boolean>
```

指示更改的URI是否为目录。true：是目录。false：非目录。

**类型：** Array&lt;boolean&gt;

**起始版本：** 12

<!--Device-ChangeData-isDirectory: Array<boolean>--><!--Device-ChangeData-isDirectory: Array<boolean>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## type

```TypeScript
type: NotifyType
```

更改的通知类型。

**类型：** NotifyType

**起始版本：** 12

<!--Device-ChangeData-type: NotifyType--><!--Device-ChangeData-type: NotifyType-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

## uris

```TypeScript
uris: Array<string>
```

需要更改的URI列表。

**类型：** Array&lt;string&gt;

**起始版本：** 12

<!--Device-ChangeData-uris: Array<string>--><!--Device-ChangeData-uris: Array<string>-End-->

**系统能力：** SystemCapability.FileManagement.DistributedFileService.CloudSync.Core

