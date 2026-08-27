# ChangeNotification

数据变更时通知的对象，包括插入的数据、更新的数据、删除的数据和设备ID。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## deleteEntries

```TypeScript
deleteEntries: Entry[]
```

数据删除记录。

**类型：** Entry[]

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId: string
```

设备ID，此处为设备UUID。

**类型：** string

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**示例**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.deviceId('deviceId');
      console.info(`query is ${query.getSqlLike()}`);
    }
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## insertEntries

```TypeScript
insertEntries: Entry[]
```

数据添加记录。

**类型：** Entry[]

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## updateEntries

```TypeScript
updateEntries: Entry[]
```

数据更新记录。

**类型：** Entry[]

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core
