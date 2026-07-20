# SystemDefinedRecord

SystemDefinedRecord是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是OpenHarmony系统特有数据类型的基类，用于描述仅在OpenHarmony系统范围内流通的特有数据类型，推荐开发者优先使用SystemDefinedRecord的子类描述数据，如[SystemDefinedForm](arkts-arkdata-unifieddatachannel-systemdefinedform-c.md)、[SystemDefinedAppItem](arkts-arkdata-unifieddatachannel-systemdefinedappitem-c.md)、[SystemDefinedPixelMap](arkts-arkdata-unifieddatachannel-systemdefinedpixelmap-c.md)等具体子类。

**继承/实现关系：** SystemDefinedRecord extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class SystemDefinedRecord extends UnifiedRecord--><!--Device-unifiedDataChannel-class SystemDefinedRecord extends UnifiedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## details

```TypeScript
details?: Record<string, number | number | number | string | Uint8Array>
```

是一个字典类型对象，key是string类型，value可以写入number（数值类型）、string（字符串类型）、Uint8Array（二进制字节数组）类型数据。非必填字段，默认值为空字典对象。

**类型：** Record&lt;string, number \| number \| number \| string \| Uint8Array&gt;

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-SystemDefinedRecord-details?: Record<string, int | long | double | string | Uint8Array>--><!--Device-SystemDefinedRecord-details?: Record<string, int | long | double | string | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

