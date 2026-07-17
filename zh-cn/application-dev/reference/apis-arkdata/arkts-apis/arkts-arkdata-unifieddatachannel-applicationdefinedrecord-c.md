# ApplicationDefinedRecord

ApplicationDefinedRecord是[UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)的子类，也是应用自定义数据类型的基类，用于描述仅在应用生态内部流通的自定义数据类型，应用可基于此类进行自定义数据类型的扩展。

**继承/实现关系：** ApplicationDefinedRecord extends [UnifiedRecord](arkts-arkdata-unifieddatachannel-unifiedrecord-c.md)

**起始版本：** 10

<!--Device-unifiedDataChannel-class ApplicationDefinedRecord extends UnifiedRecord--><!--Device-unifiedDataChannel-class ApplicationDefinedRecord extends UnifiedRecord-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## 导入模块

```TypeScript
import { unifiedDataChannel } from '@kit.ArkData';
```

## applicationDefinedType

```TypeScript
set applicationDefinedType(value: string)
```

应用自定义类型标识符，必须以'ApplicationDefined'开头。

**类型：** string

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationDefinedRecord-set applicationDefinedType(value: string)--><!--Device-ApplicationDefinedRecord-set applicationDefinedType(value: string)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

## rawData

```TypeScript
set rawData(value: Uint8Array)
```

应用自定义数据类型的二进制数据。

**类型：** Uint8Array

**起始版本：** 10

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-ApplicationDefinedRecord-set rawData(value: Uint8Array)--><!--Device-ApplicationDefinedRecord-set rawData(value: Uint8Array)-End-->

**系统能力：** SystemCapability.DistributedDataManager.UDMF.Core

