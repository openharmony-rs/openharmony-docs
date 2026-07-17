# SystemDefinedPixelMap

与系统侧定义的[PixelMap](../../apis-image-kit/arkts-apis/arkts-image-image-pixelmap-i.md)数据类型对应的图片数据类型，是[SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)的子类，仅保存PixelMap的二进制数据。

**继承/实现关系：** SystemDefinedPixelMap extends [SystemDefinedRecord](arkts-arkdata-unifieddatachannel-systemdefinedrecord-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class SystemDefinedPixelMap extends SystemDefinedRecord--><!--Device-unifiedDataChannel-class SystemDefinedPixelMap extends SystemDefinedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## rawData

```TypeScript
set rawData(value: Uint8Array)
```

PixelMap对象的二进制数据。

**类型：** Uint8Array

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemDefinedPixelMap-set rawData(value: Uint8Array)--><!--Device-SystemDefinedPixelMap-set rawData(value: Uint8Array)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

