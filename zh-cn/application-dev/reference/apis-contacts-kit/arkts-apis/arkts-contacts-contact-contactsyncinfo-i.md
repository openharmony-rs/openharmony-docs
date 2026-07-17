# ContactSyncInfo

调用应用程序相关的联系人同步的信息。

**起始版本：** 26.0.0

<!--Device-contact-interface ContactSyncInfo--><!--Device-contact-interface ContactSyncInfo-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## completedBatches

```TypeScript
completedBatches: Array<number>
```

表示已成功同步的联系人的批处理标识符数组。

值的范围是从1到totalBatches。

**类型：** Array<number>

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncInfo-completedBatches: Array<int>--><!--Device-ContactSyncInfo-completedBatches: Array<int>-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## lastSyncTime

```TypeScript
lastSyncTime: number
```

指示联系人同步的最新时间戳（毫秒）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncInfo-lastSyncTime: int--><!--Device-ContactSyncInfo-lastSyncTime: int-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## mode

```TypeScript
mode: ContactSyncMode
```

联系人同步模式。

**类型：** ContactSyncMode

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncInfo-mode: ContactSyncMode--><!--Device-ContactSyncInfo-mode: ContactSyncMode-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## syncId

```TypeScript
syncId: number
```

表示用于同步所有联系人的同步标识符。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncInfo-syncId: int--><!--Device-ContactSyncInfo-syncId: int-End-->

**系统能力：** SystemCapability.Applications.ContactsData

## totalBatches

```TypeScript
totalBatches: number
```

指示要同步的联系人批次总数。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

<!--Device-ContactSyncInfo-totalBatches: int--><!--Device-ContactSyncInfo-totalBatches: int-End-->

**系统能力：** SystemCapability.Applications.ContactsData

