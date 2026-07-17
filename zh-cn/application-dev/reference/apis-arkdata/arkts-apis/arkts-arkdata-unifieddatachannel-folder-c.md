# Folder

文件夹类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述文件夹。

**继承/实现关系：** Folder extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class Folder extends File--><!--Device-unifiedDataChannel-class Folder extends File-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## folderUri

```TypeScript
set folderUri(value: string)
```

表示文件夹的uri。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Folder-set folderUri(value: string)--><!--Device-Folder-set folderUri(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

