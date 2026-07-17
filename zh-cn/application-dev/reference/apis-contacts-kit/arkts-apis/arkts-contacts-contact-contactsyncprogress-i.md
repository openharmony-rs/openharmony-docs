# ContactSyncProgress

联系人同步进度的信息。

包含同步ID、当前批次和总批次。

**起始版本：** 26.0.0

<!--Device-contact-interface ContactSyncProgress--><!--Device-contact-interface ContactSyncProgress-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## currentBatch

```TypeScript
currentBatch: number
```

表示要同步的当前联系人批次的标识符。

值的范围是从1到totalBatches。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncProgress-currentBatch: int--><!--Device-ContactSyncProgress-currentBatch: int-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## syncId

```TypeScript
syncId: number
```

表示用于同步所有联系人的同步标识符。

该值应从0开始。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncProgress-syncId: int--><!--Device-ContactSyncProgress-syncId: int-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## totalBatches

```TypeScript
totalBatches: number
```

表示要同步的联系人批次总数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncProgress-totalBatches: int--><!--Device-ContactSyncProgress-totalBatches: int-End-->

**系统能力：** SystemCapability.Applications.ContactsData

