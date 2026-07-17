# Video

视频类型数据，是[File](arkts-arkdata-unifieddatachannel-file-c.md)的子类，用于描述视频文件。

**继承/实现关系：** Video extends [File](arkts-arkdata-unifieddatachannel-file-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class Video extends File--><!--Device-unifiedDataChannel-class Video extends File-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## videoUri

```TypeScript
set videoUri(value: string)
```

本地视频数据uri或网络视频uri，本地视频数据uri可通过[getUriFromPath](@ohos.file.fileuri:fileUri.getUriFromPath)函数获取。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-Video-set videoUri(value: string)--><!--Device-Video-set videoUri(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

