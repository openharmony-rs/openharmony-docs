# SingleKVStore

SingleKVStore数据库实例，提供增加数据、删除数据和订阅数据变更、订阅数据端端同步完成的方法。

在调用SingleKVStore的方法前，需要先通过
[getKVStore](arkts-arkdata-kvmanager-i.md#getkvstore-1)
构建一个SingleKVStore实例。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## backup

```TypeScript
backup(file: string, callback: AsyncCallback<void>): void
```

以指定名称备份数据库到默认路径（context.databaseDir），使用callback异步回调。如需备份到自定义路径，请使用
[backupEx](arkts-arkdata-singlekvstore-i.md#backupex-1)接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string | 是 | 备份数据库的指定名称，不能为空，无长度限制，不能包含特殊字符'/'。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当以指定名称备份数据库成功，err为undefined，否则为错误对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.backup(backupFile, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to backup. Code: ${err.code}, message: ${err.message} `);
    } else {
      console.info(`Succeeded in backupping data`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## backup

```TypeScript
backup(file: string): Promise<void>
```

以指定名称备份数据库到默认路径（context.databaseDir），使用Promise异步回调。如需备份到自定义路径，请使用
[backupEx](arkts-arkdata-singlekvstore-i.md#backupex-1)接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string | 是 | 备份数据库的指定名称，不能为空，无长度限制，不能包含特殊字符'/'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.backup(backupFile).then(() => {
    console.info(`Succeeded in backupping data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to backup. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## backupEx

```TypeScript
backupEx(backupConfig: BackupConfig): Promise<void>
```

以指定名称和路径备份数据库，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backupConfig | BackupConfig | 是 | 备份数据库的信息（名称和路径）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const backupConfig: distributedKVStore.BackupConfig = {
  fileName: 'BK001',
  filePath: '/data/storage/el2/database'
};
try {
  kvStore.backupEx(backupConfig).then(() => {
    console.info(`Succeeded in backupping data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to backup. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## closeResultSet

```TypeScript
closeResultSet(resultSet: KVStoreResultSet, callback: AsyncCallback<void>): void
```

关闭由[SingleKVStore.getResultSet](arkts-arkdata-singlekvstore-i.md#getresultset-2)返回的
KVStoreResultSet对象，使用callback异步回调。关闭结果集后，该结果集对象将不可再用，相关数据库资源被释放。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | KVStoreResultSet | 是 | 表示要关闭的KVStoreResultSet对象。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。关闭KVStoreResultSet对象成功，err为undefined，否则为错误对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let resultSet: distributedKVStore.KVStoreResultSet;
try {
  kvStore.getResultSet('batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
    if (err) {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing result set');
      })
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}


```

## closeResultSet

```TypeScript
closeResultSet(resultSet: KVStoreResultSet): Promise<void>
```

关闭由[SingleKVStore.getResultSet](arkts-arkdata-singlekvstore-i.md#getresultset-2)返回的
KVStoreResultSet对象，使用Promise异步回调。关闭结果集后，该结果集对象将不可再用，相关数据库资源被释放。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | KVStoreResultSet | 是 | 表示要关闭的KVStoreResultSet对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let resultSet: distributedKVStore.KVStoreResultSet;
try {
  kvStore.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet).then(() => {
        console.info('Succeeded in closing result set');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });

} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## commit

```TypeScript
commit(callback: AsyncCallback<void>): void
```

提交SingleKVStore数据库中的事务，使用callback异步回调。需先调用
[startTransaction](arkts-arkdata-singlekvstore-i.md#starttransaction-1)启动事务后再调
用本接口提交事务。提交成功后，事务期间的所有数据变更将永久生效并写入数据库。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。提交SingleKVStore数据库中的事务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.commit((err: BusinessError) => {
    if (err) {
      console.error(`Failed to commit. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in committing');
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## commit

```TypeScript
commit(): Promise<void>
```

提交SingleKVStore数据库中的事务，使用Promise异步回调。需先调用
[startTransaction](arkts-arkdata-singlekvstore-i.md#starttransaction-1)启动事务后再调
用本接口提交事务。提交成功后，事务期间的所有数据变更将永久生效并写入数据库。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.commit().then(async () => {
    console.info('Succeeded in committing');
  }).catch((err: BusinessError) => {
    console.error(`Failed to commit. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## delete

```TypeScript
delete(key: string, callback: AsyncCallback<void>): void
```

从数据库中删除指定键值的数据，使用callback异步回调。删除成功后，指定键值对将被永久删除，无法再通过get等方法查询；若已订阅数据变更通知，将触发变更通知回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要删除数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。删除指定的数据成功，err为undefined，否则为错误对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting');
    if (kvStore != null) {
      kvStore.delete(KEY_TEST_STRING_ELEMENT, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in deleting');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## delete

```TypeScript
delete(key: string): Promise<void>
```

从数据库中删除指定键值的数据，使用Promise异步回调。删除成功后，指定键值对将被永久删除，无法再通过get等方法查询；若已订阅数据变更通知，将触发变更通知回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要删除数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
    if (kvStore != null) {
      kvStore.delete(KEY_TEST_STRING_ELEMENT).then(() => {
        console.info('Succeeded in deleting');
      }).catch((err: BusinessError) => {
        console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteBackup

```TypeScript
deleteBackup(files: Array<string>, callback: AsyncCallback<Array<[string, number]>>): void
```

根据指定名称从默认路径（context.databaseDir）删除备份文件，使用callback异步回调。删除备份文件后，将无法再通过
[restore](arkts-arkdata-singlekvstore-i.md#restore-2)接口恢复该备份文件中的数据。如需从自定义路径删除备份，请使用
[deleteBackupEx](arkts-arkdata-singlekvstore-i.md#deletebackupex-1)接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | 是 | 删除备份文件所指定的名称，不能为空，无长度限制，不能包含特殊字符'/'。 |
| callback | AsyncCallback&lt;Array&lt;[string, number]&gt;&gt; | 是 | 回调函数，返回删除备份的文件名及其处理结果。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let files = ['BK001', 'BK002'];
try {
  kvStore.deleteBackup(files, (err: BusinessError, data: [string, number][]) => {
    if (err) {
      console.error(`Failed to delete Backup. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeed in deleting Backup.data=${data}`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteBackup

```TypeScript
deleteBackup(files: Array<string>): Promise<Array<[string, number]>>
```

根据指定名称从默认路径（context.databaseDir）删除备份文件，使用Promise异步回调。删除备份文件后，将无法再通过
[restore](arkts-arkdata-singlekvstore-i.md#restore-1)接口恢复该备份文件中的
数据。如需从自定义路径删除备份，请使用[deleteBackupEx](arkts-arkdata-singlekvstore-i.md#deletebackupex-1)接口。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | 是 | 删除备份文件所指定的名称，不能为空，无长度限制，不能包含特殊字符'/'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[string, number]&gt;&gt; | Promise对象，返回删除备份的文件名及其处理结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Parameter verification failed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let files = ['BK001', 'BK002'];
try {
  kvStore.deleteBackup(files).then((data: [string, number][]) => {
    console.info(`Succeed in deleting Backup.data=${data}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete Backup. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteBackupEx

```TypeScript
deleteBackupEx(backupConfig: BackupConfig): Promise<void>
```

根据指定名称和路径删除备份文件，使用Promise异步回调。

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backupConfig | BackupConfig | 是 | 备份数据库的信息（名称和路径）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100000](../errorcode-distributedKVStore.md#15100000-无效的参数) | Input parameters do not meet the API requirements, such as invalid valueranges, length limits, or incorrect formats. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const backupConfig: distributedKVStore.BackupConfig = {
  fileName: 'BK001',
  filePath: '/data/storage/el2/database'
};
try {
  kvStore.deleteBackupEx(backupConfig).then(() => {
    console.info(`Succeed in deleting Backup.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to delete Backup. Code: ${err.code}, message: ${err.message}`);
  })
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteBatch

```TypeScript
deleteBatch(keys: string[], callback: AsyncCallback<void>): void
```

批量删除SingleKVStore数据库中的键值对，使用callback异步回调。删除成功后，指定键值对将被永久删除，无法再通过get等方法查询；若已订阅数据变更通知，将触发变更通知回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | string[] | 是 | 表示要批量删除的键名列表，不能为空，数组中每个元素的长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。批量删除指定的数据成功，err为undefined，否则为错误对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  let keys: string[] = [];
  for (let i = 0; i < 5; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
    keys.push(key + i);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.deleteBatch(keys, async (err: BusinessError) => {
        if (err) {
          console.error(`Failed to delete Batch. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in deleting Batch');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## deleteBatch

```TypeScript
deleteBatch(keys: string[]): Promise<void>
```

批量删除SingleKVStore数据库中的键值对，使用Promise异步回调。删除成功后，指定键值对将被永久删除，无法再通过get等方法查询；若已订阅数据变更通知，将触发变更通知回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | string[] | 是 | 表示要批量删除的键名列表，不能为空，数组中每个元素的长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  let keys: string[] = [];
  for (let i = 0; i < 5; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
    keys.push(key + i);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.deleteBatch(keys).then(() => {
        console.info('Succeeded in deleting Batch');
      }).catch((err: BusinessError) => {
        console.error(`Failed to delete Batch. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## enableSync

```TypeScript
enableSync(enabled: boolean, callback: AsyncCallback<void>): void
```

设定是否开启端端同步，使用callback异步回调。开启端端同步后，数据库中的数据可在多设备间自动同步；关闭后则不会自动同步，需要手动调用
[sync](arkts-arkdata-singlekvstore-i.md#sync-1)接口触发同步。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设定是否开启端端同步，true表示开启端端同步，false表示不启用端端同步。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。设定成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.enableSync(true, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to enable sync. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in enabling sync');
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## enableSync

```TypeScript
enableSync(enabled: boolean): Promise<void>
```

设定是否开启端端同步，使用Promise异步回调。开启端端同步后，数据库中的数据可在多设备间自动同步；关闭后则不会自动同步，需要手动调用
[sync](arkts-arkdata-singlekvstore-i.md#sync-1)接口触发同步。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设定是否开启端端同步，true表示开启端端同步，false表示不启用端端同步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.enableSync(true).then(() => {
    console.info('Succeeded in enabling sync');
  }).catch((err: BusinessError) => {
    console.error(`Failed to enable sync. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## get

```TypeScript
get(key: string, callback: AsyncCallback<boolean | string | number | number | Uint8Array>): void
```

获取指定键的值，使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要查询数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |
| callback | AsyncCallback&lt;boolean \| string \| number \| number \| Uint8Array&gt; | 是 | 回调函数。返回获取查询的值，值的类型取决于存储时的数据类型。[ |

## get

```TypeScript
get(key: string): Promise<boolean | string | number | number | Uint8Array>
```

获取指定键的值，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要查询数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean \| string \| number \| number \| Uint8Array&gt; | Promise对象。返回指定键对应的值，值的类型取决于存储时的数据类型。[ |

## getEntries

```TypeScript
getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

获取匹配指定键前缀的所有键值对，使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| callback | AsyncCallback&lt;Entry[]&gt; | 是 | 回调函数。返回匹配指定前缀的键值对列表。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getEntries

```TypeScript
getEntries(keyPrefix: string): Promise<Entry[]>
```

获取匹配指定键前缀的所有键值对，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回匹配指定前缀的键值对列表。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';


try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
        console.info(`PutBatch ${entries}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getEntries

```TypeScript
getEntries(query: Query, callback: AsyncCallback<Entry[]>): void
```

获取与指定Query对象匹配的键值对列表，使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | Query | 是 | 表示要查询的对象。 |
| callback | AsyncCallback&lt;Entry[]&gt; | 是 | 回调函数。返回与指定Query对象匹配的键值对列表。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query, (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}

```

## getEntries

```TypeScript
getEntries(query: Query): Promise<Entry[]>
```

获取与指定Query对象匹配的键值对列表，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | Query | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回与指定Query对象匹配的键值对列表。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let arr = new Uint8Array([21, 31]);
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_bool_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.BYTE_ARRAY,
        value: arr
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getEntries(query).then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
  });
  console.info('Succeeded in getting Entries');
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get Entries. Code: ${error.code}, message: ${error.message}`);
}

```

## getResultSet

```TypeScript
getResultSet(keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void
```

从SingleKVStore数据库中获取具有指定前缀的结果集，使用callback异步回调。获取结果集后，在使用完毕时需调用
[closeResultSet](arkts-arkdata-singlekvstore-i.md#closeresultset-1)
关闭结果集释放资源。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |
| callback | AsyncCallback&lt;KVStoreResultSet&gt; | 是 | 回调函数。返回具有指定前缀的结果集。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    if (kvStore != null) {
      kvStore.getResultSet('batch_test_string_key', async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set');
        resultSet = result;
        if (kvStore != null) {
          kvStore.closeResultSet(resultSet, (err :BusinessError) => {
            if (err) {
              console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
              return;
            }
            console.info('Succeeded in closing result set');
          });
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getResultSet

```TypeScript
getResultSet(keyPrefix: string): Promise<KVStoreResultSet>
```

从SingleKVStore数据库中获取具有指定前缀的结果集，使用Promise异步回调。获取结果集后，在使用完毕时需调用
[closeResultSet](arkts-arkdata-singlekvstore-i.md#closeresultset-1)
关闭结果集释放资源。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀，长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。不能包含'^'，包含'^'将导致谓词失效，查询结果会返回数据库中的所有数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KVStoreResultSet&gt; | Promise对象。返回具有指定前缀的结果集。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore!.putBatch(entries).then(() => {
    console.info('Succeeded in putting batch');
    kvStore!.getResultSet('batch_test_string_key').then((result: distributedKVStore.KVStoreResultSet) => {
      console.info('Succeeded in getting result set');
      resultSet = result;
      if (kvStore != null) {
        kvStore.closeResultSet(resultSet).then(() => {
          console.info('Succeeded in closing result set');
        }).catch((err: BusinessError) => {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
        });
      }
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getResultSet

```TypeScript
getResultSet(query: Query, callback: AsyncCallback<KVStoreResultSet>): void
```

获取与指定Query对象匹配的KVStoreResultSet对象，使用callback异步回调。获取结果集后，在使用完毕时需调用
[closeResultSet](arkts-arkdata-singlekvstore-i.md#closeresultset-1)
关闭结果集释放资源。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | Query | 是 | 表示查询对象。 |
| callback | AsyncCallback&lt;KVStoreResultSet&gt; | 是 | 回调函数，获取与指定Query对象匹配的KVStoreResultSet对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSet(query, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
        if (err) {
          console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getResultSet

```TypeScript
getResultSet(query: Query): Promise<KVStoreResultSet>
```

获取与指定Query对象匹配的KVStoreResultSet对象，使用Promise异步回调。获取结果集后，在使用完毕时需调用
[closeResultSet](arkts-arkdata-singlekvstore-i.md#closeresultset-1)
关闭结果集释放资源。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | Query | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KVStoreResultSet&gt; | Promise对象。获取与指定Query对象匹配的KVStoreResultSet对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
    kvStore!.putBatch(entries).then(() => {
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    kvStore!.getResultSet(query).then((result: distributedKVStore.KVStoreResultSet) => {
      console.info(`Succeeded in getting result set size=${result.getCount()}`);
    }).catch((err: BusinessError) => {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getResultSize

```TypeScript
getResultSize(query: Query, callback: AsyncCallback<number>): void
```

获取与指定Query对象匹配的结果数，使用callback异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | Query | 是 | 表示查询对象。 |
| callback | AsyncCallback&lt;number&gt; | 是 | 回调函数。返回与指定Query对象匹配的结果数。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
    const query = new distributedKVStore.Query();
    query.prefixKey('batch_test');
    if (kvStore != null) {
      kvStore.getResultSize(query, (err: BusinessError, resultSize: number) => {
        if (err) {
          console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting result set size');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getResultSize

```TypeScript
getResultSize(query: Query): Promise<number>
```

获取与指定Query对象匹配的结果数，使用Promise异步回调。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | Query | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。获取与指定Query对象匹配的结果数。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting batch');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
  });
  const query = new distributedKVStore.Query();
  query.prefixKey('batch_test');
  kvStore.getResultSize(query).then((resultSize: number) => {
    console.info('Succeeded in getting result set size');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get result size. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getSecurityLevel

```TypeScript
getSecurityLevel(callback: AsyncCallback<SecurityLevel>): void
```

获取数据库的安全级别，使用callback异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;SecurityLevel&gt; | 是 | 回调函数。返回数据库的安全级别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.getSecurityLevel((err: BusinessError, data: distributedKVStore.SecurityLevel) => {
    if (err) {
      console.error(`Failed to get SecurityLevel. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting securityLevel');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## getSecurityLevel

```TypeScript
getSecurityLevel(): Promise<SecurityLevel>
```

获取数据库的安全级别，使用Promise异步回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SecurityLevel&gt; | Promise对象。返回数据库的安全级别。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.getSecurityLevel().then((data: distributedKVStore.SecurityLevel) => {
    console.info('Succeeded in getting securityLevel');
  }).catch((err: BusinessError) => {
    console.error(`Failed to get SecurityLevel. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## off

```TypeScript
off(event: 'dataChange', listener?: Callback<ChangeNotification>): void
```

取消订阅数据变更通知。必须先调用
[on('dataChange')](arkts-arkdata-singlekvstore-i.md#on-1)
订阅后，才能调用off取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取消订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| listener | Callback&lt;ChangeNotification&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有已订阅的函数。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class KvstoreModel {
  call(data: distributedKVStore.ChangeNotification) {
    console.info(`dataChange : ${data}`);
  }

  subscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.on('dataChange', distributedKVStore.SubscribeType.SUBSCRIBE_TYPE_REMOTE, this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to subscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  }

  unsubscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.off('dataChange', this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to unsubscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  }
}

```

## off

```TypeScript
off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void
```

取消订阅端端同步完成事件回调通知。必须先调用
[on('syncComplete')](arkts-arkdata-singlekvstore-i.md#on-2)
订阅后，才能调用off取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 取消订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | Callback&lt;Array&lt;[string, number]&gt;&gt; | 否 | 取消订阅的同步完成回调函数。如果该参数不填，则取消所有已订阅的同步完成回调函数。需要注意的是：如果同一个数据库存在多个ArkTS实例（通过[getKVStore](arkts-arkdata-kvmanager-i.md#getkvstore-1)接口获取），且这些实例分别注册了同步完成事件回调，那么当任意一个实例调用off('syncComplete')且不传入syncCallback参数（即取消该实例的所有回调）时，其他实例已订阅的同步完成回调函数也会被一并取消。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

class KvstoreModel {
  call(data: [string, number][]) {
    console.info(`syncComplete : ${data}`);
  }

  subscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.on('syncComplete', this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to subscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  }

  unsubscribeDataChange() {
    try {
      if (kvStore != null) {
        kvStore.off('syncComplete', this.call);
      }
    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to unsubscribeDataChange. Code: ${error.code}, message: ${error.message}`);
    }
  } 
}

```

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void
```

订阅指定类型的数据变更通知。调用on订阅后，在不需要监听时必须调用
[off('dataChange')](arkts-arkdata-singlekvstore-i.md#off-1)
取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| type | SubscribeType | 是 | 表示订阅的类型。 |
| listener | Callback&lt;ChangeNotification&gt; | 是 | 回调函数。成功返回数据变更时通知的对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100001](../errorcode-distributedKVStore.md#15100001-超过最大订阅数量或结果集数量) | Over max limits. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.on('dataChange', distributedKVStore.SubscribeType.SUBSCRIBE_TYPE_LOCAL, (data: distributedKVStore.ChangeNotification) => {
    console.info(`dataChange callback call data: ${data}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## on

```TypeScript
on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void
```

订阅端端同步完成事件回调通知。调用on订阅后，在不需要监听时必须调用
[off('syncComplete')](arkts-arkdata-singlekvstore-i.md#off-2)
取消订阅。

**起始版本：** 9

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | Callback&lt;Array&lt;[string, number]&gt;&gt; | 是 | 回调函数。用于向调用方发送同步结果的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';


const KEY_TEST_FLOAT_ELEMENT = 'key_test_float';
const VALUE_TEST_FLOAT_ELEMENT = 321.12;
try {
  kvStore.on('syncComplete', (data: [string, number][]) => {
    console.info(`syncComplete ${data}`);
  });
  kvStore.put(KEY_TEST_FLOAT_ELEMENT, VALUE_TEST_FLOAT_ELEMENT).then(() => {
    console.info('succeeded in putting');
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to subscribe syncComplete. Code: ${error.code}, message: ${error.message}`);
}

```

## put

```TypeScript
put(key: string, value: Uint8Array | string | number | number | boolean, callback: AsyncCallback<void>): void
```

添加指定类型键值对到数据库，使用callback异步回调。若Key已存在则更新对应Value；若已订阅数据变更通知，将触发变更通知回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要添加数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |
| value | Uint8Array \| string \| number \| number \| boolean | 是 | 要添加数据的value，支持Uint8Array、string、number、boolean，Uint8Array、string的长度范围为0-[MAX_VALUE_LENGTH](arkts-arkdata-constants-i.md)。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。数据添加成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |

## put

```TypeScript
put(key: string, value: Uint8Array | string | number | number | boolean): Promise<void>
```

添加指定类型键值对到数据库，使用Promise异步回调。若Key已存在则更新对应Value；若已订阅数据变更通知，将触发变更通知回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要添加数据的Key，不能为空且长度范围为1-[MAX_KEY_LENGTH](arkts-arkdata-constants-i.md)。 |
| value | Uint8Array \| string \| number \| number \| boolean | 是 | 要添加数据的value，支持Uint8Array、string、number、boolean，Uint8Array、string的长度范围为0-[MAX_VALUE_LENGTH](arkts-arkdata-constants-i.md)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types;<br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |

## putBatch

```TypeScript
putBatch(entries: Entry[], callback: AsyncCallback<void>): void
```

批量插入键值对到SingleKVStore数据库中，使用callback异步回调。若Key已存在则更新对应Value；若已订阅数据变更通知，将触发变更通知回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entries | Entry[] | 是 | 表示要批量插入的键值对。一个entries对象中允许的最大数据量为512MB。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。数据批量插入成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key', (err: BusinessError, entries: distributedKVStore.Entry[]) => {
        if (err) {
          console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in getting Entries');
        console.info(`entries.length: ${entries.length}`);
        console.info(`entries[0]: ${entries[0]}`);
      });
    } else {
      console.error('KvStore is null'); // 后续示例代码与此处保持一致
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## putBatch

```TypeScript
putBatch(entries: Entry[]): Promise<void>
```

批量插入键值对到SingleKVStore数据库中，使用Promise异步回调。若Key已存在则更新对应Value；若已订阅数据变更通知，将触发变更通知回调。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entries | Entry[] | 是 | 表示要批量插入的键值对。一个entries对象中允许的最大数据量为512MB。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < 10; i++) {
    let key = 'batch_test_string_key';
    let entry: distributedKVStore.Entry = {
      key: key + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  console.info(`entries: ${entries}`);
  kvStore.putBatch(entries).then(async () => {
    console.info('Succeeded in putting Batch');
    if (kvStore != null) {
      kvStore.getEntries('batch_test_string_key').then((entries: distributedKVStore.Entry[]) => {
        console.info('Succeeded in getting Entries');
        console.info(`PutBatch ${entries}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get Entries. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put Batch. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## rekey

```TypeScript
rekey(): Promise<void>
```

更新数据库的加密密钥，使用Promise异步回调。

> **说明：**
>
> rekey仅对创建时已启用加密的数据库有效，即Options中encrypt需设置为true，非加密数据库调用此接口将返回错误。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [15100006](../errorcode-distributedKVStore.md#15100006-更新数据库加密密钥失败) | Failed to update the key. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.rekey().then(() => {
    console.info('Success');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to rekey. Code: ${error.code}, message: ${error.message}`);
}

```

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void
```

删除指定设备的数据，使用callback异步回调。删除成功后，指定设备的所有数据将从本地数据库中永久移除，无法再通过get等方法查询该设备的数据。

> **说明：**
>
> 其中deviceId为[DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicebasicinfo-i.md)中的
> networkId，通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-i.md#getavailabledevicelistsync-1)
> 方法得到。
>
> deviceId具体获取方式请参考
> [sync接口示例](arkts-arkdata-singlekvstore-i.md#sync-1)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要删除其数据的设备，不能为空。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。删除指定设备的数据成功，err为undefined，否则为错误对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put device data. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting data');
    const deviceId = 'no_exist_device_id';
    if (kvStore) {
      kvStore.removeDeviceData(deviceId, async (err: BusinessError) => {
        if (err) {
          console.error(`Failed to remove device data. Code: ${err.code}, message: ${err.message}`);
        } else {
          console.info('Succeeded in removing device data');
          if (kvStore) {
            kvStore.get(KEY_TEST_STRING_ELEMENT, async (err: BusinessError, data: boolean | string | number | Uint8Array) => {
                if (err) {
                  console.error(`Failed to get data. Code: ${err.code}, message: ${err.message}`);
                  return;
                }
                console.info(`Succeeded in getting data.data=${data}`);
              });
          }
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string): Promise<void>
```

删除指定设备的数据，使用Promise异步回调。删除成功后，指定设备的所有数据将从本地数据库中永久移除，无法再通过get等方法查询该设备的数据。

> **说明：**
>
> 其中deviceId为[DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicebasicinfo-i.md)中的
> networkId，通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-i.md#getavailabledevicelistsync-1)
> 方法得到。
>
> deviceId具体获取方式请参考
> [sync接口示例](arkts-arkdata-singlekvstore-i.md#sync-1)。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 设备的networkId，标识要删除其数据的设备，不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-001';
try {
  kvStore!.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info('Succeeded in putting data');
    const deviceId = 'no_exist_device_id';
    kvStore!.removeDeviceData(deviceId).then(() => {
      console.info('succeeded in removing device data');
      kvStore!.get(KEY_TEST_STRING_ELEMENT).then((data: boolean | string | number | Uint8Array) => {
        console.info(`Succeeded in getting data. Data=${data}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get data. Code: ${err.code}, message: ${err.message}`);
      });
    }).catch((err: BusinessError) => {
      console.error(`Failed to remove device data. Code: ${err.code}, message: ${err.message}`);
    });
  }).catch((err: BusinessError) => {
    console.error(`Failed to put data. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## restore

```TypeScript
restore(file: string, callback: AsyncCallback<void>): void
```

从数据库默认路径（context.databaseDir）下指定名称的备份文件恢复数据库，使用callback异步回调。恢复成功后，当前数据库中的数据将被替换为备份文件中的数据，原有的未备份数据将丢失。如需从自定义路径恢复，请
使用[restoreEx](arkts-arkdata-singlekvstore-i.md#restoreex-1)接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string | 是 | 指定的数据库文件名称，不能为空，无长度限制，不能包含特殊字符'/'。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。当从指定的数据库文件恢复数据库成功，err为undefined，否则为错误对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.restore(backupFile, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to restore. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info(`Succeeded in restoring data`);
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## restore

```TypeScript
restore(file: string): Promise<void>
```

从数据库默认路径（context.databaseDir）下指定名称的备份文件恢复数据库，使用Promise异步回调。恢复成功后，当前数据库中的数据将被替换为备份文件中的数据，原有的未备份数据将丢失。如需从自定义路径恢复，请使
用[restoreEx](arkts-arkdata-singlekvstore-i.md#restoreex-1)接口。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string | 是 | 指定的数据库文件名称，不能为空，无长度限制，不能包含特殊字符'/'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.restore(backupFile).then(() => {
    console.info(`Succeeded in restoring data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## restoreEx

```TypeScript
restoreEx(backupConfig: BackupConfig): Promise<void>
```

从指定路径和名称的备份文件恢复数据库，使用Promise异步回调。恢复成功后，当前数据库中的数据将被替换为备份文件中的数据，原有的未备份数据将丢失。

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| backupConfig | BackupConfig | 是 | 备份数据库的信息（名称和路径）。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。[ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const backupConfig: distributedKVStore.BackupConfig = {
  fileName: 'BK001',
  filePath: '/data/storage/el2/database'
};
try {
  kvStore.restoreEx(backupConfig).then(() => {
    console.info(`Succeeded in restoring data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## rollback

```TypeScript
rollback(callback: AsyncCallback<void>): void
```

在SingleKVStore数据库中回滚事务，使用callback异步回调。需先调用
[startTransaction](arkts-arkdata-singlekvstore-i.md#starttransaction-1)启动事务后再调
用本接口回滚事务。回滚成功后，事务期间的所有数据变更将被丢弃，不会写入数据库。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。SingleKVStore数据库中回滚事务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.rollback((err: BusinessError) => {
    if (err) {
      console.error(`Failed to rollback. Code: ${err.code}, message: ${err.message}`);
    } else {
      console.info('Succeeded in rolling back');
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## rollback

```TypeScript
rollback(): Promise<void>
```

在SingleKVStore数据库中回滚事务，使用Promise异步回调。需先调用
[startTransaction](arkts-arkdata-singlekvstore-i.md#starttransaction-1)启动事务后再调
用本接口回滚事务。回滚成功后，事务期间的所有数据变更将被丢弃，不会写入数据库。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.rollback().then(async () => {
    console.info('Succeeded in rolling back');
  }).catch((err: BusinessError) => {
    console.error(`Failed to rollback. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## setSyncParam

```TypeScript
setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback<void>): void
```

设置数据库端端同步允许的默认延时，使用callback异步回调。

> **说明：**
>
> 设置默认延时后，调用
> [sync](arkts-arkdata-singlekvstore-i.md#sync-1)接口不会立即触发
> 端端同步，而是等待指定的延时时间后再执行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultAllowedDelayMs | number | 是 | 表示一个延时时间，单位为毫秒（ms），取值范围为0或[100, 86400000]。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。设置成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const defaultAllowedDelayMs = 500;
  kvStore.setSyncParam(defaultAllowedDelayMs, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set syncParam. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting syncParam');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## setSyncParam

```TypeScript
setSyncParam(defaultAllowedDelayMs: number): Promise<void>
```

设置数据库端端同步允许的默认延时，使用Promise异步回调。

> **说明：**
>
> 设置默认延时后，调用
> [sync](arkts-arkdata-singlekvstore-i.md#sync-1)接口不会立即触发
> 端端同步，而是等待指定的延时时间后再执行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultAllowedDelayMs | number | 是 | 表示一个延时时间，单位为毫秒（ms），取值范围为0或[100, 86400000]。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const defaultAllowedDelayMs = 500;
  kvStore.setSyncParam(defaultAllowedDelayMs).then(() => {
    console.info('Succeeded in setting syncParam');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set syncParam. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## setSyncRange

```TypeScript
setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback<void>): void
```

设置同步范围标签，使用callback异步回调。通过设置本地设备和远程设备的同步标签，决定哪些设备间可以进行数据同步。只有当本地设备的标签与远程设备的标签存在交集时，两端才允许同步数据。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localLabels | string[] | 是 | 表示本地设备的同步标签，用于标识本设备可参与同步的范围。 |
| remoteSupportLabels | string[] | 是 | 表示期望同步数据的对端设备的同步标签，用于标识允许同步的对端设备范围。当本端的remoteSupportLabels与对端的localLabels存在交集时，设备间才允许数据同步。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。设置成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localLabels = ['A', 'B'];
  const remoteSupportLabels = ['C', 'D'];
  kvStore.setSyncRange(localLabels, remoteSupportLabels, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to set syncRange. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in setting syncRange');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## setSyncRange

```TypeScript
setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise<void>
```

设置同步范围标签，使用Promise异步回调。通过设置本地设备和远程设备的同步标签，决定哪些设备间可以进行数据同步。只有当本地设备的标签与远程设备的标签存在交集时，两端才允许同步数据。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localLabels | string[] | 是 | 表示本地设备的同步标签，用于标识本设备可参与同步的范围。 |
| remoteSupportLabels | string[] | 是 | 表示期望同步数据的对端设备的同步标签，用于标识允许同步的对端设备范围。当本端的remoteSupportLabels与对端的localLabels存在交集时，设备间才允许数据同步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  const localLabels = ['A', 'B'];
  const remoteSupportLabels = ['C', 'D'];
  kvStore.setSyncRange(localLabels, remoteSupportLabels).then(() => {
    console.info('Succeeded in setting syncRange');
  }).catch((err: BusinessError) => {
    console.error(`Failed to set syncRange. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}

```

## startTransaction

```TypeScript
startTransaction(callback: AsyncCallback<void>): void
```

启动SingleKVStore数据库中的事务，使用callback异步回调。启动事务后，后续的数据库操作将纳入此事务范围，直到调用
[commit](arkts-arkdata-singlekvstore-i.md#commit-1)提交或
[rollback](arkts-arkdata-singlekvstore-i.md#rollback-1)回滚才会结束事务。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。启动SingleKVStore数据库中的事务成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

function putBatchString(len: number, prefix: string) {
  let entries: distributedKVStore.Entry[] = [];
  for (let i = 0; i < len; i++) {
    let entry: distributedKVStore.Entry = {
      key: prefix + i,
      value: {
        type: distributedKVStore.ValueType.STRING,
        value: 'batch_test_string_value'
      }
    }
    entries.push(entry);
  }
  return entries;
} // 自定义函数，放置在作用域最外侧，防止语法检查报错

try {
  let count = 0;
  kvStore.on('dataChange', 0, (data: distributedKVStore.ChangeNotification) => {
    console.info(`startTransaction 0 ${data}`);
    count++;
  });
  kvStore.startTransaction(async (err: BusinessError) => {
    if (err) {
      console.error(`Failed to start Transaction. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in starting Transaction');
    let entries = putBatchString(10, 'batch_test_string_key');
    console.info(`entries: ${entries}`);
    if (kvStore != null) {
      kvStore.putBatch(entries, async (err: BusinessError) => {
        if (err) {
          console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in putting Batch');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to start Transaction. Code: ${error.code}, message: ${error.message}`);
}

```

## startTransaction

```TypeScript
startTransaction(): Promise<void>
```

启动SingleKVStore数据库中的事务，使用Promise异步回调。启动事务后，后续的数据库操作将纳入此事务范围，直到调用
[commit](arkts-arkdata-singlekvstore-i.md#commit-1)提交或
[rollback](arkts-arkdata-singlekvstore-i.md#rollback-1)回滚才会结束事务。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-数据库或查询结果集已关闭) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal文件大小超过默认上限) | The WAL file size exceeds the default limit.<br>**适用版本：** 10+ |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  kvStore.on('dataChange', distributedKVStore.SubscribeType.SUBSCRIBE_TYPE_ALL, (data: distributedKVStore.ChangeNotification) => {
    console.info(`startTransaction 0 ${data}`);
  });
  kvStore.startTransaction().then(async () => {
    console.info('Succeeded in starting Transaction');
  }).catch((err: BusinessError) => {
    console.error(`Failed to start Transaction. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to start Transaction. Code: ${error.code}, message: ${error.message}`);
}

```

## sync

```TypeScript
sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void
```

在手动同步方式下，触发数据库端端同步。同步结果可通过订阅
[on('syncComplete')](arkts-arkdata-singlekvstore-i.md#on-2)
事件获取。关于键值型数据库的端端同步方式说明，请见[键值型数据库跨设备数据同步](../../../../database/data-sync-of-kv-store.md)。

> **说明：**
>
> 其中deviceIds为[DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicebasicinfo-i.md)中的
> networkId, 通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-i.md#getavailabledevicelistsync-1)
> 方法得到。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceIds | string[] | 是 | 同一组网环境下，需要同步的设备的networkId列表。 |
| mode | SyncMode | 是 | 同步模式。 |
| delayMs | number | 否 | 可选参数，允许延时时间，单位：ms（毫秒），默认为0。设置delayMs后，调用sync接口时延时时间为delayMs。未设置时以[setSyncParam](arkts-arkdata-singlekvstore-i.md#setsyncparam-1)设置的时长为准。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let devManager: distributedDeviceManager.DeviceManager;
const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';
// create deviceManager
export default class EntryAbility extends UIAbility {
  onCreate() {
    let context = this.context;
    try {
      devManager = distributedDeviceManager.createDeviceManager(context.applicationInfo.name);
      let deviceIds: string[] = [];
      if (devManager != null) {
        let devices = devManager.getAvailableDeviceListSync();
        for (let i = 0; i < devices.length; i++) {
          deviceIds[i] = devices[i].networkId as string;
        }
      }
      try {
        if (kvStore != null) {
          kvStore.on('syncComplete', (data: [string, number][]) => {
            console.info('Sync dataChange');
          });
          if (kvStore != null) {
            kvStore.put(KEY_TEST_SYNC_ELEMENT + 'testSync101', VALUE_TEST_SYNC_ELEMENT, (err: BusinessError) => {
              if (err) {
                console.error(`Failed to sync. Code: ${err.code}, message: ${err.message}`);
                return;
              }
              console.info('Succeeded in putting data');
              const mode = distributedKVStore.SyncMode.PULL_ONLY;
              if (kvStore != null) {
                kvStore.sync(deviceIds, mode, 1000);
              }
            });
          }
        }
      } catch (err) {
        let error = err as BusinessError;
        console.error(`Failed to sync. Code: ${error.code}, message: ${error.message}`);
      }

    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to create device manager. Code: ${error.code}, message: ${error.message}`);
    }
  }
}

```

## sync

```TypeScript
sync(deviceIds: string[], query: Query, mode: SyncMode, delayMs?: number): void
```

在手动同步方式下，触发数据库端端同步，支持按查询条件过滤同步数据。同步结果可通过订阅
[on('syncComplete')](arkts-arkdata-singlekvstore-i.md#on-2)
事件获取。关于键值型数据库的端端同步方式说明，请见[键值型数据库跨设备数据同步](../../../../database/data-sync-of-kv-store.md)。

> **说明：**
>
> 其中deviceIds为[DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicebasicinfo-i.md)中的
> networkId, 通过调用
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-i.md#getavailabledevicelistsync-1)
> 方法得到。

**起始版本：** 9

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceIds | string[] | 是 | 同一组网环境下，需要同步的设备的networkId列表。 |
| query | Query | 是 | 表示数据库的查询谓词条件。 |
| mode | SyncMode | 是 | 同步模式。 |
| delayMs | number | 否 | 可选参数，允许延时时间，单位：ms（毫秒），默认为0。设置delayMs后，调用sync接口时延时时间为delayMs。未设置时以[setSyncParam](arkts-arkdata-singlekvstore-i.md#setsyncparam-1)设置的时长为准。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-数据库损坏) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-未找到相关数据) | Not found. |

**示例：**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';
// create deviceManager
export default class EntryAbility extends UIAbility {
  onCreate() {
    let context = this.context;
    try {
      let devManager = distributedDeviceManager.createDeviceManager(context.applicationInfo.name);
      let deviceIds: string[] = [];
      if (devManager != null) {
        let devices = devManager.getAvailableDeviceListSync();
        for (let i = 0; i < devices.length; i++) {
          deviceIds[i] = devices[i].networkId as string;
        }
      }
      try {
        if (kvStore != null) {
          kvStore.on('syncComplete', (data: [string, number][]) => {
            console.info('Sync dataChange');
          });
          if (kvStore != null) {
            kvStore.put(KEY_TEST_SYNC_ELEMENT + 'testSync101', VALUE_TEST_SYNC_ELEMENT, (err: BusinessError) => {
              if (err) {
                console.error(`Failed to sync. Code: ${err.code}, message: ${err.message}`);
                return;
              }
              console.info('Succeeded in putting data');
              const mode = distributedKVStore.SyncMode.PULL_ONLY;
              const query = new distributedKVStore.Query();
              query.prefixKey('batch_test');
              query.deviceId(devManager.getLocalDeviceNetworkId());
              if (kvStore != null) {
                kvStore.sync(deviceIds, query, mode, 1000);
              }
            });
          }
        }
      } catch (err) {
        let error = err as BusinessError;
        console.error(`Failed to sync. Code: ${error.code}, message: ${error.message}`);
      }

    } catch (err) {
      let error = err as BusinessError;
      console.error(`Failed to create device manager. Code: ${error.code}, message: ${error.message}`);
    }
  }
}

```

