# DistributedInfo（系统接口）

记录分布式信息。

**起始版本：** 24

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## flag

```TypeScript
flag?: DistributedOrigin
```

表示数据来源，不传入则保持原有数值。

**类型：** [DistributedOrigin](arkts-arkdata-relationalstore-distributedorigin-e-sys.md)

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。

## oriDevice

```TypeScript
oriDevice?: string
```

表示数据产生者的设备id，不传入则保持原有设备id。

**类型：** string

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**系统接口：** 此接口为系统接口。
