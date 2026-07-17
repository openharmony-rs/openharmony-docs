# KVManager

分布式键值数据库管理实例，用于获取分布式键值数据库的相关信息。在调用KVManager的方法前，需要先通过[createKVManager](arkts-arkdata-distributedkvstore-createkvmanager-f.md#createkvmanager-1)构建一个KVManager实例。

**起始版本：** 9

<!--Device-distributedKVStore-interface KVManager--><!--Device-distributedKVStore-interface KVManager-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## 导入模块

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## closeKVStore

```TypeScript
closeKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void
```

通过storeId的值关闭指定的分布式键值数据库，使用callback异步回调。此方法与getKVStore()方法配对使用，使用完毕的数据库应通过此方法关闭。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-closeKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void--><!--Device-KVManager-closeKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的BundleName，不可为空且长度范围为1-256字节。 |
| storeId | string | 是 | 要关闭的数据库唯一标识符，长度范围为1-[MAX_STORE_ID_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)，且只能包含字母数字或下划线_。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当要关闭的数据库成功关闭，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;
const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3
}
try {
  kvManager.getKVStore('storeId', options, async (err: BusinessError, store: distributedKVStore.SingleKVStore | null) => {
    if (err) {
      console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId为createKVManager中的appId
      kvManager.closeKVStore(appId, 'storeId', (err: BusinessError)=> {
        if (err) {
          console.error(`Failed to close KVStore. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing KVStore');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## closeKVStore

```TypeScript
closeKVStore(appId: string, storeId: string, kvConfig?: Options): Promise<void>
```

通过storeId的值关闭指定的分布式键值数据库，如果使用kvConfig参数，关闭的是指定路径下的分布式键值数据库，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvConfig?: Options): Promise<void>--><!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvConfig?: Options): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的BundleName，不可为空且长度范围为1-256字节。 |
| storeId | string | 是 | 要关闭的数据库唯一标识符，长度范围为1-[MAX_STORE_ID_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)，且只能包含字母数字或下划线_。 |
| kvConfig | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 否 | 要关闭的数据库的配置信息，默认为空。<br>**起始版本：** 24 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;

const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3,
  // 从API version 24开始，可使用rootDir指定数据库存储路径
  rootDir: "/data/storage/el2/database/entry"
}
try {
  kvManager.getKVStore<distributedKVStore.SingleKVStore>('storeId', options).then(async (store: distributedKVStore.SingleKVStore | null) => {
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId为createKVManager中的appId, 如果options中没有配置rootDir，closeKVStore不需要options参数
      kvManager.closeKVStore(appId, 'storeId', options).then(() => {
        console.info('Succeeded in closing KVStore');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close KVStore. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to close KVStore. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteKVStore

```TypeScript
deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void
```

通过storeId的值删除指定的分布式键值数据库，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void--><!--Device-KVManager-deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的BundleName，不可为空且长度范围为1-256字节。 |
| storeId | string | 是 | 要删除的数据库唯一标识符，长度范围为1-[MAX_STORE_ID_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)，且只能包含字母数字或下划线_。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。当要删除的数据库成功删除，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;

const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3
}
try {
  kvManager.getKVStore('storeId', options, async (err: BusinessError, store: distributedKVStore.SingleKVStore | null) => {
    if (err) {
      console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId为createKVManager中的appId
      kvManager.deleteKVStore(appId, 'storeId', (err: BusinessError) => {
        if (err) {
          console.error(`Failed to delete KVStore. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info(`Succeeded in deleting KVStore`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to delete KVStore. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteKVStore

```TypeScript
deleteKVStore(appId: string, storeId: string, kvConfig?: Options): Promise<void>
```

通过storeId的值删除指定的分布式键值数据库，如果使用kvConfig参数，删除的是指定路径下的分布式键值数据库，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-deleteKVStore(appId: string, storeId: string, kvConfig?: Options): Promise<void>--><!--Device-KVManager-deleteKVStore(appId: string, storeId: string, kvConfig?: Options): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的BundleName，不可为空且长度范围为1-256字节。 |
| storeId | string | 是 | 要删除的数据库唯一标识符，长度范围为1-[MAX_STORE_ID_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)，且只能包含字母数字或下划线_。 |
| kvConfig | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 否 | 要删除的数据库的配置信息，默认为空。<br>**起始版本：** 24 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;

const options: distributedKVStore.Options = {
  createIfMissing: true,
  encrypt: false,
  backup: false,
  autoSync: false,
  kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
  schema: undefined,
  securityLevel: distributedKVStore.SecurityLevel.S3,
  // 从API version 24开始，可使用rootDir指定数据库存储路径
  rootDir: "/data/storage/el2/database/entry"
}
try {
  kvManager.getKVStore<distributedKVStore.SingleKVStore>('storeId', options).then(async (store: distributedKVStore.SingleKVStore | null) => {
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    kvStore = null;
    store = null;
    if (kvManager != undefined) {
      // appId为createKVManager中的appId, 如果options中没有配置rootDir，deleteKVStore不需要options参数
      kvManager.deleteKVStore(appId, 'storeId', options).then(() => {
        console.info('Succeeded in deleting KVStore');
      }).catch((err: BusinessError) => {
        console.error(`Failed to delete KVStore. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to delete KVStore. Code: ${error.code}, message: ${error.message}`);
}

```

## getAllKVStoreId

```TypeScript
getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void
```

获取所有通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore-1)方法创建的且没有调用[deleteKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#deletekvstore-1)方法删除的分布式键值数据库的storeId，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void--><!--Device-KVManager-getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的BundleName，不可为空且长度范围为1-256字节。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<string[]> | 是 | 回调函数。返回所有创建的分布式键值数据库的storeId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // appId为createKVManager中的appId
  kvManager.getAllKVStoreId(appId, (err: BusinessError, data: string[]) => {
    if (err) {
      console.error(`Failed to get AllKVStoreId. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting AllKVStoreId');
    console.info(`GetAllKVStoreId size = ${data.length}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get AllKVStoreId. Code: ${error.code}, message: ${error.message}`);
}

```

## getAllKVStoreId

```TypeScript
getAllKVStoreId(appId: string): Promise<string[]>
```

获取所有通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore-1)方法创建的且没有调用[deleteKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#deletekvstore-1)方法删除的分布式键值数据库的storeId，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-getAllKVStoreId(appId: string): Promise<string[]>--><!--Device-KVManager-getAllKVStoreId(appId: string): Promise<string[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 应用的BundleName，不可为空且长度范围为1-256字节。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<string[]> | Promise对象。返回所有创建的分布式键值数据库的storeId。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  // appId为createKVManager中的appId
  console.info('GetAllKVStoreId');
  kvManager.getAllKVStoreId(appId).then((data: string[]) => {
    console.info('Succeeded in getting AllKVStoreId');
    console.info(`GetAllKVStoreId size = ${data.length}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get AllKVStoreId. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get AllKVStoreId. Code: ${error.code}, message: ${error.message}`);
}

```

## getKVStore

```TypeScript
getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>): void
```

通过指定options和storeId，创建并获取分布式键值数据库，使用callback异步回调。获取数据库后，在使用完毕时需调用[closeKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#closekvstore-1)关闭数据库释放资源。

> **注意：**  
>  
> 在获取已有的分布式键值数据库时，如果数据库文件无法打开（例如文件头损坏），将触发自动重建逻辑，并返回新创建的分布式键值数据库实例。建议对重要且无法重新生成的数据使用备份恢复功能，以防止数据丢失。有关备份恢复的使用方法，请参  
> 阅[数据库备份与恢复](../../../../database/data-backup-and-restore.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>): void--><!--Device-KVManager-getKVStore<T>(storeId: string, options: Options, callback: AsyncCallback<T>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| storeId | string | 是 | 数据库唯一标识符，长度范围为1-[MAX_STORE_ID_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)，且只能包含字母数字或下划线_。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 创建分布式键值实例的配置信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<T> | 是 | 回调函数。返回创建的分布式键值数据库实例（根据kvStoreType的不同，可以创建SingleKVStore实例和DeviceKVStore实例）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100002](../errorcode-distributedKVStore.md#15100002-打开已有数据库时参数配置发生变化) | Open existed database with changed options. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;
try {
  const options: distributedKVStore.Options = {
    createIfMissing: true,
    encrypt: false,
    backup: false,
    autoSync: false,
    kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
    securityLevel: distributedKVStore.SecurityLevel.S3
  };
  kvManager.getKVStore('storeId', options, (err: BusinessError, store: distributedKVStore.SingleKVStore) => {
    if (err) {
      console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting KVStore');
    kvStore = store;
    if (kvStore !== null) {
       // 进行后续相关数据操作，包括数据的增、删、改、查、订阅数据变化等操作
       // ...
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getKVStore

```TypeScript
getKVStore<T>(storeId: string, options: Options): Promise<T>
```

指定options和storeId，创建并获取分布式键值数据库，使用Promise回调。获取数据库后，在使用完毕时需调用[closeKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#closekvstore-1)关闭数据库释放资源。

> **注意：**  
>  
> 获取已有的分布式键值数据库时，如果数据库文件无法打开（如文件头损坏），将触发自动重建逻辑，并返回新创建的分布式键值数据库实例。建议对重要且无法重新生成的数据使用备份恢复功能，防止数据丢失。备份恢复的使用方法详见  
> [数据库备份与恢复](../../../../database/data-backup-and-restore.md)。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-KVManager-getKVStore<T>(storeId: string, options: Options): Promise<T>--><!--Device-KVManager-getKVStore<T>(storeId: string, options: Options): Promise<T>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| storeId | string | 是 | 数据库唯一标识符，长度范围为1-[MAX_STORE_ID_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md)，且只能包含字母数字或下划线_。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 创建分布式键值实例的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<T> | Promise对象。返回创建的分布式键值数据库实例（根据kvStoreType的不同，可以创建SingleKVStore实例和DeviceKVStore实例）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100002](../errorcode-distributedKVStore.md#15100002-打开已有数据库时参数配置发生变化) | Open existed database with changed options. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let kvStore: distributedKVStore.SingleKVStore | null = null;
try {
  const options: distributedKVStore.Options = {
    createIfMissing: true,
    encrypt: false,
    backup: false,
    autoSync: false,
    kvStoreType: distributedKVStore.KVStoreType.SINGLE_VERSION,
    securityLevel: distributedKVStore.SecurityLevel.S3,
    // 从API version 24开始，可使用rootDir指定数据库存储路径
    rootDir: "/data/storage/el2/database/entry"
  };
  kvManager.getKVStore<distributedKVStore.SingleKVStore>('storeId', options).then((store: distributedKVStore.SingleKVStore) => {
    console.info('Succeeded in getting KVStore');
    kvStore = store;
  }).catch((err: BusinessError) => {
    console.error(`Failed to get KVStore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## off

```TypeScript
off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void
```

取消订阅服务状态变更通知。必须先调用[on('distributedDataServiceDie')](arkts-arkdata-distributedkvstore-kvmanager-i.md#on-1)订阅后，才能调用off取消订阅。参数中的deathCallback必须是已经订阅过的deathCallback，否则会取消订阅失败。

**起始版本：** 9

<!--Device-KVManager-off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void--><!--Device-KVManager-off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'distributedDataServiceDie' | 是 | 取消订阅的事件名，固定为'distributedDataServiceDie'，即服务状态变更事件。 |
| deathCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<void> | 否 | 回调函数。如果该参数不填，那么会将之前订阅过的所有的deathCallback取消订阅。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info('KVManagerOff');
  const deathCallback = () => {
    console.info('death callback call');
  }
  kvManager.off('distributedDataServiceDie', deathCallback);
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## on

```TypeScript
on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void
```

订阅服务终止事件。如果服务终止，需要重新调用[on('dataChange')](arkts-arkdata-distributedkvstore-singlekvstore-i.md#on-1)和[on('syncComplete')](arkts-arkdata-distributedkvstore-singlekvstore-i.md#on-2)注册数据变更通知和端端同步完成事件回调通知，并且端端同步操作会返回失败。调用on订阅后，在不需要监听时必须调用[off('distributedDataServiceDie')](arkts-arkdata-distributedkvstore-kvmanager-i.md#off-1)取消订阅。

**起始版本：** 9

<!--Device-KVManager-on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void--><!--Device-KVManager-on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'distributedDataServiceDie' | 是 | 订阅的事件名，固定为'distributedDataServiceDie'，即服务终止事件。 |
| deathCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<void> | 是 | 回调函数。订阅成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  console.info('KVManagerOn');
  const deathCallback = () => {
    console.info('death callback call');
  }
  kvManager.on('distributedDataServiceDie', deathCallback);
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

