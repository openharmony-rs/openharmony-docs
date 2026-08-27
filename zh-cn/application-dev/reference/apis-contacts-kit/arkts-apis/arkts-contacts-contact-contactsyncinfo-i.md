# ContactSyncInfo

调用应用程序相关的联系人同步的信息。

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Applications.ContactsData

## 导入模块

```TypeScript
import { contact } from '@kit.ContactsKit';
```

## completedBatches

```TypeScript
completedBatches: Array<number>
```

表示已成功同步的联系人的批处理标识符数组。值的范围是从1到totalBatches。

**类型：** Array&lt;number&gt;

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## lastSyncTime

```TypeScript
lastSyncTime: number
```

表示联系人同步的最新时间戳（毫秒）。

**类型：** number

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.Applications.ContactsData

## mode

```TypeScript
mode: ContactSyncMode
```

联系人同步模式。

**类型：** [ContactSyncMode](arkts-contacts-contact-contactsyncmode-e.md)

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**原子化服务API：** 从API版本26.0.0开始，该接口支持在原子化服务API中使用。

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

**系统能力：** SystemCapability.Applications.ContactsData
