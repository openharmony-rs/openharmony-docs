# SingleKVStore

```TypeScript
interface SingleKVStore
```

Provides APIs for data management in a single KV store, such as adding data, deleting data, and subscribing to data changes or across-device data sync completion events. Before calling any method in **SingleKVStore**, you must use getKVStore to obtain a **SingleKVStore** instance.

**Since:** 9

<!--Device-distributedKVStore-interface SingleKVStore--><!--Device-distributedKVStore-interface SingleKVStore-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## backup

```TypeScript
backup(file: string, callback: AsyncCallback<void>): void
```

Backs up a database with a specified name to the default path (**context.databaseDir**). This API uses an asynchronous callback to return the result. To back up the database to a custom path, use the [backupEx](#backupex) API.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-backup(file: string, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-backup(file: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| file | string | Yes | Name of the database to back up. The value cannot be empty and cannot contain slashes (/). There is no length limit. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.backup(backupFile, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to backup. Code: ${err.code}, message: ${err.message} `);
    } else {
      console.info(`Succeeded in backing up data`);
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

Backs up a database with a specified name to the default path (**context.databaseDir**). This API uses a promise to return the result. To back up the database to a custom path, use the [backupEx](#backupex) API.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-backup(file: string): Promise<void>--><!--Device-SingleKVStore-backup(file: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| file | string | Yes | Name of the database to back up. The value cannot be empty and cannot contain slashes (/). There is no length limit. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let backupFile = 'BK001';
try {
  kvStore.backup(backupFile).then(() => {
    console.info(`Succeeded in backing up data`);
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

Backs up a database with a specified name and path. This API uses a promise to return the result.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-backupEx(backupConfig: BackupConfig): Promise<void>--><!--Device-SingleKVStore-backupEx(backupConfig: BackupConfig): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backupConfig | [BackupConfig](arkts-arkdata-distributedkvstore-backupconfig-i.md) | Yes | Information about the database to back up, including the name and path. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100000](../errorcode-distributedKVStore.md#15100000-invalid-parameter) | Input parameters do not meet the API requirements, such as invalid value ranges, length limits, or incorrect formats. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const backupConfig: distributedKVStore.BackupConfig = {
  fileName: 'BK001',
  filePath: '/data/storage/el2/database'
};
try {
  kvStore.backupEx(backupConfig).then(() => {
    console.info(`Succeeded in backing up data`);
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

Closes the **KVStoreResultSet** object returned by [SingleKvStore.getResultSet](#getresultset-2). This API uses an asynchronous callback to return the result. After the result set is closed, the result set object cannot be used anymore, and related database resources are released.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-closeResultSet(resultSet: KVStoreResultSet, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-closeResultSet(resultSet: KVStoreResultSet, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resultSet | [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md) | Yes | **KVStoreResultSet** object to close. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Closes the **KVStoreResultSet** object returned by [SingleKvStore.getResultSet](#getresultset-2). This API uses a promise to return the result. After the result set is closed, the result set object cannot be used anymore, and related database resources are released.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-closeResultSet(resultSet: KVStoreResultSet): Promise<void>--><!--Device-SingleKVStore-closeResultSet(resultSet: KVStoreResultSet): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resultSet | [KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md) | Yes | **KVStoreResultSet** object to close. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Commits the transaction in this single KV store. This API uses an asynchronous callback to return the result. You need to call startTransaction to start a transaction before calling this API to commit the transaction. After the transaction is successfully committed, all data changes during the transaction will take effect permanently and be written into the database.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-commit(callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-commit(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Commits the transaction in this single KV store. This API uses a promise to return the result. You need to call startTransaction to start a transaction before calling this API to commit the transaction. After the transaction is successfully committed, all data changes during the transaction will take effect permanently and be written into the database.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-commit(): Promise<void>--><!--Device-SingleKVStore-commit(): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Deletes a KV pair from this KV store. This API uses an asynchronous callback to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-delete(key: string, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-delete(key: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data to delete. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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

Deletes a KV pair from this KV store. This API uses a promise to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-delete(key: string): Promise<void>--><!--Device-SingleKVStore-delete(key: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data to delete. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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

Deletes a backup file from the default path (**context.databaseDir**) based on the specified name. This API uses an asynchronous callback to return the result. After a backup file is deleted, the data in the backup file cannot be restored using the **restore** API. To delete a backup file from a custom path, use the [deleteBackupEx](#deletebackupex) API.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-deleteBackup(files: Array<string>, callback: AsyncCallback<Array<[string, int]>>): void--><!--Device-SingleKVStore-deleteBackup(files: Array<string>, callback: AsyncCallback<Array<[string, int]>>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | Yes | Name of the backup file to delete. The value cannot be empty and cannot contain slashes (/). There is no length limit. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | Yes | Callback used to return the name of the backup file deleted and the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |

**Examples**

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

Deletes a backup file from the default path (**context.databaseDir**) based on the specified name. This API uses a promise to return the result. After a backup file is deleted, the data in the backup file cannot be restored using the **restore** API. To delete a backup file from a custom path, use the [deleteBackupEx](#deletebackupex) API.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-deleteBackup(files: Array<string>): Promise<Array<[string, int]>>--><!--Device-SingleKVStore-deleteBackup(files: Array<string>): Promise<Array<[string, int]>>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| files | Array&lt;string&gt; | Yes | Name of the backup file to delete. The value cannot be empty and cannot contain slashes (/). There is no length limit. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[string, number]&gt;&gt; | Promise used to return the name of the backup file deleted and the operation result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |

**Examples**

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

Deletes a backup file based on the specified name and path. This API uses a promise to return the result.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-deleteBackupEx(backupConfig: BackupConfig): Promise<void>--><!--Device-SingleKVStore-deleteBackupEx(backupConfig: BackupConfig): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backupConfig | [BackupConfig](arkts-arkdata-distributedkvstore-backupconfig-i.md) | Yes | Information about the database to back up, including the name and path. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100000](../errorcode-distributedKVStore.md#15100000-invalid-parameter) | Input parameters do not meet the API requirements, such as invalid value ranges, length limits, or incorrect formats. |

**Examples**

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

Batch deletes KV pairs from this single KV store. This API uses an asynchronous callback to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-deleteBatch(keys: string[], callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-deleteBatch(keys: string[], callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | string[] | Yes | List of keys to delete in batches. The value cannot be empty. The length of each element in the array ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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

Batch deletes KV pairs from this single KV store. This API uses a promise to return the result. If the deletion is successful, the specified key-value pair will be permanently deleted and cannot be queried using the **get** method. If the data change notification has been subscribed to, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-deleteBatch(keys: string[]): Promise<void>--><!--Device-SingleKVStore-deleteBatch(keys: string[]): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | string[] | Yes | List of keys to delete in batches. The value cannot be empty. The length of each element in the array ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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

Sets cross-device data sync, which can be enabled or disabled. This API uses an asynchronous callback to return the result. After cross-device data sync is enabled, data in the database can be automatically synced across devices. After it is disabled, data will not be automatically synced. You need to manually call the **sync** API to trigger data sync.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-enableSync(enabled: boolean, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-enableSync(enabled: boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable data sync across devices. The value **true** means to enable data sync across devices, and the value **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Sets cross-device data sync, which can be enabled or disabled. This API uses a promise to return the result. After cross-device data sync is enabled, data in the database can be automatically synced across devices. After it is disabled, data will not be automatically synced. You need to manually call the **sync** API to trigger data sync.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-enableSync(enabled: boolean): Promise<void>--><!--Device-SingleKVStore-enableSync(enabled: boolean): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable data sync across devices. The value **true** means to enable data sync across devices, and the value **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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
get(key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void
```

Obtains the value of the specified key. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-get(key: string, callback: AsyncCallback<boolean | string | long | double | Uint8Array>): void--><!--Device-SingleKVStore-get(key: string, callback: AsyncCallback<boolean | string | long | double | Uint8Array>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data to obtain. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean &#124; string &#124; number &#124; Uint8Array&gt; | Yes | Callback used to return the obtained value. The value type depends on the data type when the value is stored. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-failed-to-find-data) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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
      kvStore.get(KEY_TEST_STRING_ELEMENT, (err: BusinessError, data: boolean | string | number | Uint8Array) => {
        if (err) {
          console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info(`Succeeded in getting data.data=${data}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';


const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
    if (kvStore != null) {
      kvStore.get(KEY_TEST_STRING_ELEMENT).then((data: boolean | string | number | Uint8Array) => {
        console.info(`Succeeded in getting data.data=${data}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

## get

```TypeScript
get(key: string): Promise<boolean | string | number | Uint8Array>
```

Obtains the value of the specified key. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-get(key: string): Promise<boolean | string | long | double | Uint8Array>--><!--Device-SingleKVStore-get(key: string): Promise<boolean | string | long | double | Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data to obtain. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean &#124; string &#124; number &#124; Uint8Array&gt; | Promise used to return the value corresponding to the specified key. The value type depends on the data type when the value is stored. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-failed-to-find-data) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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
      kvStore.get(KEY_TEST_STRING_ELEMENT, (err: BusinessError, data: boolean | string | number | Uint8Array) => {
        if (err) {
          console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info(`Succeeded in getting data.data=${data}`);
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';


const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
    if (kvStore != null) {
      kvStore.get(KEY_TEST_STRING_ELEMENT).then((data: boolean | string | number | Uint8Array) => {
        console.info(`Succeeded in getting data.data=${data}`);
      }).catch((err: BusinessError) => {
        console.error(`Failed to get. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to get. Code: ${error.code}, message: ${error.message}`);
}
```

## getEntries

```TypeScript
getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

Obtains all KV pairs that match the specified key prefix. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void--><!--Device-SingleKVStore-getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyPrefix | string | Yes | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]&gt; | Yes | Callback used to return the KV pairs that match the specified prefix. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Obtains all KV pairs that match the specified key prefix. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getEntries(keyPrefix: string): Promise<Entry[]>--><!--Device-SingleKVStore-getEntries(keyPrefix: string): Promise<Entry[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyPrefix | string | Yes | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]&gt; | Promise used to return the KV pairs that match the specified prefix. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Obtains the KV pairs that match the specified **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-SingleKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributedkvstore-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]&gt; | Yes | Callback used to return the KV pairs that match the specified **Query** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Obtains the KV pairs that match the specified **Query** object. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getEntries(query: Query): Promise<Entry[]>--><!--Device-SingleKVStore-getEntries(query: Query): Promise<Entry[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributedkvstore-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributedkvstore-entry-i.md)[]&gt; | Promise used to return the KV pairs that match the specified **Query** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Obtains a result set with the specified prefix from this single KV store. This API uses an asynchronous callback to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getResultSet(keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-SingleKVStore-getResultSet(keyPrefix: string, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyPrefix | string | Yes | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md)&gt; | Yes | Callback used to return the result set with the specified prefix. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-subscription-count-or-result-set-count-reaches-the-limit) | Over max limits.<br>**Applicable version:** 10 and later |

**Examples**

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

Obtains a result set with the specified prefix from this single KV store. This API uses a promise to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getResultSet(keyPrefix: string): Promise<KVStoreResultSet>--><!--Device-SingleKVStore-getResultSet(keyPrefix: string): Promise<KVStoreResultSet>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keyPrefix | string | Yes | Key prefix to match. The length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). It cannot contain '^'; otherwise, the predicate becomes invalid and all data in the RDB store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md)&gt; | Promise used to return the result set with the specified prefix. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-subscription-count-or-result-set-count-reaches-the-limit) | Over max limits.<br>**Applicable version:** 10 and later |

**Examples**

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

Obtains a **KVStoreResultSet** object that matches the specified **Query** object. This API uses an asynchronous callback to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getResultSet(query: Query, callback: AsyncCallback<KVStoreResultSet>): void--><!--Device-SingleKVStore-getResultSet(query: Query, callback: AsyncCallback<KVStoreResultSet>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributedkvstore-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md)&gt; | Yes | Callback used to return the **KVStoreResultSet** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-subscription-count-or-result-set-count-reaches-the-limit) | Over max limits.<br>**Applicable version:** 10 and later |

**Examples**

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

Obtains a **KVStoreResultSet** object that matches the specified **Query** object. This API uses a promise to return the result. After using the obtained result set, call [closeResultSet](#closeresultset) to close the result set and release resources.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getResultSet(query: Query): Promise<KVStoreResultSet>--><!--Device-SingleKVStore-getResultSet(query: Query): Promise<KVStoreResultSet>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributedkvstore-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KVStoreResultSet](arkts-arkdata-distributedkvstore-kvstoreresultset-i.md)&gt; | Promise used to return the **KVStoreResultSet** object obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [15100001](../errorcode-distributedKVStore.md#15100001-subscription-count-or-result-set-count-reaches-the-limit) | Over max limits.<br>**Applicable version:** 10 and later |

**Examples**

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

Obtains the number of results that match the specified **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getResultSize(query: Query, callback: AsyncCallback<int>): void--><!--Device-SingleKVStore-getResultSize(query: Query, callback: AsyncCallback<int>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributedkvstore-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the number of results obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-failed-to-find-data) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Obtains the number of results that match the specified **Query** object. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getResultSize(query: Query): Promise<int>--><!--Device-SingleKVStore-getResultSize(query: Query): Promise<int>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributedkvstore-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of results obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-failed-to-find-data) | Not found. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Obtains the security level of this KV store. This API uses an asynchronous callback to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getSecurityLevel(callback: AsyncCallback<SecurityLevel>): void--><!--Device-SingleKVStore-getSecurityLevel(callback: AsyncCallback<SecurityLevel>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[SecurityLevel](arkts-arkdata-distributedkvstore-securitylevel-e.md)&gt; | Yes | Callback used to return the security level of the KV store. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Obtains the security level of this KV store. This API uses a promise to return the result.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-getSecurityLevel(): Promise<SecurityLevel>--><!--Device-SingleKVStore-getSecurityLevel(): Promise<SecurityLevel>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[SecurityLevel](arkts-arkdata-distributedkvstore-securitylevel-e.md)&gt; | Promise used to return the security level of the KV store. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Unsubscribes from data changes. You must call on('dataChange') to subscribe to data changes before calling off to cancel subscription.

**Since:** 9

<!--Device-SingleKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void--><!--Device-SingleKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event type. The value is **dataChange**, which indicates a data change event. |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeNotification](arkts-arkdata-distributedkvstore-changenotification-i.md)&gt; | No | Callback to unregister. If this parameter is not specified, this API unregisters all callbacks for data changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Unsubscribes from the cross-device data sync completion events. You must call on('syncComplete') to subscribe to the events before calling off to cancel subscription.

**Since:** 9

<!--Device-SingleKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void--><!--Device-SingleKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'syncComplete' | Yes | Event type. The value is **syncComplete**, which indicates a sync completion event. |
| syncCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | No | Callback to unregister. If this parameter is not set, all callbacks used to listen for the data sync completion event are unregistered. Note that if multiple ArkTS instances (obtained through the getKVStore API) of the same database all register the callback used to listen for the sync completion event, and one of the instances calls **off('syncComplete')** without passing the **syncCallback** parameter (that is, all callbacks of this instance are unregistered), then the callbacks of the other instances are also unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Subscribes to data changes of the specified type. After calling on to subscribe to data changes, call off('dataChange') to cancel the subscription when it is no longer needed.

**Since:** 9

<!--Device-SingleKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void--><!--Device-SingleKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event type. The value is **dataChange**, which indicates a data change event. |
| type | [SubscribeType](arkts-arkdata-distributedkvstore-subscribetype-e.md) | Yes | Type of data change. |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeNotification](arkts-arkdata-distributedkvstore-changenotification-i.md)&gt; | Yes | Callback used to return the object to be notified when the data changes. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100001](../errorcode-distributedKVStore.md#15100001-subscription-count-or-result-set-count-reaches-the-limit) | Over max limits. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Subscribes to the cross-device data sync completion events. After calling on to subscribe to the events, call off('syncComplete') to unsubscribe from the events when they are no longer needed.

**Since:** 9

<!--Device-SingleKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void--><!--Device-SingleKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'syncComplete' | Yes | Event type. The value is **syncComplete**, which indicates the sync completion event. |
| syncCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | Yes | Callback used to return the sync completion event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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
put(key: string, value: Uint8Array | string | number | boolean, callback: AsyncCallback<void>): void
```

Adds a KV pair of the specified type to this KV store. This API uses an asynchronous callback to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-put(key: string, value: Uint8Array | string | long | double | boolean, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-put(key: string, value: Uint8Array | string | long | double | boolean, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data to add. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |
| value | Uint8Array &#124; string &#124; number &#124; boolean | Yes | Value of the data to add. The value type can be Uint 8Array, long , double, string, or boolean. The length range of the Uint8Array and string is 0- [MAX_VALUE_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
  kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(() => {
    console.info(`Succeeded in putting data`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## put

```TypeScript
put(key: string, value: Uint8Array | string | number | boolean): Promise<void>
```

Adds a KV pair of the specified type to this KV store. This API uses a promise to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-put(key: string, value: Uint8Array | string | long | double | boolean): Promise<void>--><!--Device-SingleKVStore-put(key: string, value: Uint8Array | string | long | double | boolean): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the data to add. The value cannot be empty and its length ranges from 1 to [MAX_KEY_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |
| value | Uint8Array &#124; string &#124; number &#124; boolean | Yes | Value of the data to add. The value type can be Uint 8Array, long , double, string, or boolean. The length range of the Uint8Array and string is 0- [MAX_VALUE_LENGTH](arkts-arkdata-distributedkvstore-constants-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types; <br>3.Parameter verification failed. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

See [put](#put)

## putBatch

```TypeScript
putBatch(entries: Entry[], callback: AsyncCallback<void>): void
```

Batch inserts KV pairs to this single KV store. This API uses an asynchronous callback to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-putBatch(entries: Entry[], callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-putBatch(entries: Entry[], callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| entries | [Entry](arkts-arkdata-distributedkvstore-entry-i.md)[] | Yes | KV pairs to insert, which An **entries** object supports up to 512 MB of data. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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

## putBatch

```TypeScript
putBatch(entries: Entry[]): Promise<void>
```

Batch inserts KV pairs to this single KV store. This API uses a promise to return the result. If the key already exists, the corresponding value will be updated. If you have subscribed to data change notifications, the change notification callback will be triggered.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-putBatch(entries: Entry[]): Promise<void>--><!--Device-SingleKVStore-putBatch(entries: Entry[]): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| entries | [Entry](arkts-arkdata-distributedkvstore-entry-i.md)[] | Yes | KV pairs to insert, which An **entries** object supports up to 512 MB of data. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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

Updates the encryption key of a database. This API uses a promise to return the result.

> **NOTE:** 
> 
> The **rekey** operation is valid only for databases for which encryption is enabled during creation. That is,
> the **encrypt** parameter in **Options** must be set to **true**. If this API is called for a non-encrypted
> database, an error will be returned.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-rekey(): Promise<void>--><!--Device-SingleKVStore-rekey(): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Deletes data of a device. This API uses an asynchronous callback to return the result. After the data is deleted, all data of the device will be permanently removed from the local database and cannot be queried using methods such as **get**.

> **NOTE:** 
> 
> **deviceId** is **networkId** in
> [DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md), which can be
> obtained by
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> .
> 
> For details about how to obtain **deviceId**, see [sync()](arkts-arkdata-distributedkvstore-syncmode-e.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Network ID of the device whose data is to be deleted. This parameter cannot be left empty. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Deletes data of a device. This API uses a promise to return the result. After the data is deleted, all data of the device will be permanently removed from the local database and cannot be queried using methods such as **get**.

> **NOTE:** 
> 
> **deviceId** is **networkId** in
> [DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md), which can be
> obtained by
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> .
> 
> For details about how to obtain **deviceId**, see [sync()](arkts-arkdata-distributedkvstore-syncmode-e.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-removeDeviceData(deviceId: string): Promise<void>--><!--Device-SingleKVStore-removeDeviceData(deviceId: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Network ID of the device whose data is to be deleted. This parameter cannot be left empty. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Restores a database from a specified backup file in the default database path (**context.databaseDir**). This API uses an asynchronous callback to return the result. If the restoration is successful, the data in the current database will be replaced by the data in the backup file, and the original data that is not backed up will be lost. To restore the database from a custom path, use the [restoreEx](#restoreex) API.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-restore(file: string, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-restore(file: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| file | string | Yes | Name of the database file. The value cannot be empty and cannot contain slashes (/). There is no length limit. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Restores a database from a specified backup file in the default database path (**context.databaseDir**). This API uses a promise to return the result. If the restoration is successful, the data in the current database will be replaced by the data in the backup file, and the original data that is not backed up will be lost. To restore the database from a custom path, use the [restoreEx](#restoreex) API.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-restore(file: string): Promise<void>--><!--Device-SingleKVStore-restore(file: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| file | string | Yes | Name of the database file. The value cannot be empty and cannot contain slashes (/). There is no length limit. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Parameter verification failed. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Restores a database from a backup file with the specified path and name. This API uses a promise to return the result. If the restoration is successful, the data in the current database will be replaced by that in the backup file, and the original data that is not backed up will be lost.

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-restoreEx(backupConfig: BackupConfig): Promise<void>--><!--Device-SingleKVStore-restoreEx(backupConfig: BackupConfig): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| backupConfig | [BackupConfig](arkts-arkdata-distributedkvstore-backupconfig-i.md) | Yes | Information about the database to back up, including the name and path. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100000](../errorcode-distributedKVStore.md#15100000-invalid-parameter) | Input parameters do not meet the API requirements, such as invalid value ranges, length limits, or incorrect formats. |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Rolls back the transaction in this single KV store. This API uses an asynchronous callback to return the result. You need to call startTransaction to start a transaction before calling this API to roll back the transaction. After the transaction is successfully rolled back, all data changes during the transaction will be discarded and will not be written into the database.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-rollback(callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-rollback(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Rolls back the transaction in this single KV store. This API uses a promise to return the result. You need to call startTransaction to start a transaction before calling this API to roll back the transaction. After the transaction is successfully rolled back, all data changes during the transaction will be discarded and will not be written into the database.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-rollback(): Promise<void>--><!--Device-SingleKVStore-rollback(): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |

**Examples**

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

Sets the default delay for cross-device data sync. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> After the default delay is set, calling [sync](arkts-arkdata-distributedkvstore-syncmode-e.md) will not trigger the cross-
> device data sync immediately. Instead, the data sync will be executed only after the specified delay duration.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: int, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: int, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| defaultAllowedDelayMs | number | Yes | Delay time to set, in ms. The value can be **0** or ranges from 100 to 86400000. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Sets the default delay for cross-device data sync. This API uses a promise to return the result.

> **NOTE:** 
> 
> After the default delay is set, calling [sync](arkts-arkdata-distributedkvstore-syncmode-e.md) will not trigger the cross-
> device data sync immediately. Instead, the data sync will be executed only after the specified delay duration.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: int): Promise<void>--><!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: int): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| defaultAllowedDelayMs | number | Yes | Delay time to set, in ms. The value can be **0** or ranges from 100 to 86400000. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Sets the data sync range. This API uses an asynchronous callback to return the result. You can set the sync tags for the local and remote devices to determine which devices can perform data sync. Data can be synced only when the tags of the local device overlap with those of the remote device.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localLabels | string[] | Yes | Sync labels set for the local devices, which are used to identify the range of local devices that can be synced. |
| remoteSupportLabels | string[] | Yes | Sync labels set for the remote devices that expect to sync data, which are used to identify the range of remote devices that are allowed to sync data. Data can be synced between devices only when the **remoteSupportLabels** of the local device overlap with the **localLabels** of the remote device. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Sets the data sync range. This API uses a promise to return the result. You can set the sync tags for the local and remote devices to determine which devices can perform data sync. Data can be synced only when the tags of the local device overlap with those of the remote device.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise<void>--><!--Device-SingleKVStore-setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localLabels | string[] | Yes | Sync labels set for the local devices, which are used to identify the range of local devices that can be synced. |
| remoteSupportLabels | string[] | Yes | Sync labels set for the remote devices that expect to sync data, which are used to identify the range of remote devices that are allowed to sync data. Data can be synced between devices only when the **remoteSupportLabels** of the local device overlap with the **localLabels** of the remote device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |

**Examples**

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

Starts the transaction in this single KV store. This API uses an asynchronous callback to return the result. After a transaction is started, subsequent database operations are included in this transaction until commit or rollback is called.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-startTransaction(callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-startTransaction(callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. If the operation is successful, **err** is **undefined**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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
} // Custom function used outside the scope to prevent syntax check errors.

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

Starts the transaction in this single KV store. This API uses a promise to return the result. After a transaction is started, subsequent database operations are included in this transaction until commit or rollback is called.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-startTransaction(): Promise<void>--><!--Device-SingleKVStore-startTransaction(): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [15100005](../errorcode-distributedKVStore.md#15100005-kv-store-or-result-set-closed) | Database or result set already closed. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |

**Examples**

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

Starts cross-device data sync manually. The sync result can be obtained by subscribing to the **on('syncComplete')** event. For details about the sync modes of KV stores, see [Cross-Device Synchronization of KV Stores](../../../database/data-sync-of-kv-store.md).

> **NOTE:** 
> 
> **deviceIds** is **networkId** in
> [DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md), which can be
> obtained by
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> .

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: int): void--><!--Device-SingleKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: int): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceIds | string[] | Yes | List of **networkId**s of the devices in the same networking environment to be synchronized. |
| mode | [SyncMode](arkts-arkdata-distributedkvstore-syncmode-e.md) | Yes | Sync mode. |
| delayMs | number | No | Delay time allowed, in ms. The default value is **0**. If **delayMs** is set, data sync will be executed **delayMs** after **sync()** is called. If **delayMs** is not set, the delay set in [setSyncParam](#setsyncparam) is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-failed-to-find-data) | Not found. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let devManager: distributedDeviceManager.DeviceManager;
const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';

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

Starts cross-device data sync manually. Data can be filtered by query conditions. The sync result can be obtained by subscribing to the **on('syncComplete')** event. For details about the sync modes of KV stores, see [Cross-Device Synchronization of KV Stores](../../../database/data-sync-of-kv-store.md).

> **NOTE:** 
> 
> **deviceIds** is **networkId** in
> [DeviceBasicInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicebasicinfo-i.md), which can be
> obtained by
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> .

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

<!--Device-SingleKVStore-sync(deviceIds: string[], query: Query, mode: SyncMode, delayMs?: int): void--><!--Device-SingleKVStore-sync(deviceIds: string[], query: Query, mode: SyncMode, delayMs?: int): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceIds | string[] | Yes | List of **networkId**s of the devices in the same networking environment to be synchronized. |
| query | [Query](arkts-arkdata-distributedkvstore-query-c.md) | Yes | **Query** object to match. |
| mode | [SyncMode](arkts-arkdata-distributedkvstore-syncmode-e.md) | Yes | Sync mode. |
| delayMs | number | No | Delay time allowed, in ms. The default value is **0**. If **delayMs** is set, data sync will be executed **delayMs** after **sync()** is called. If **delayMs** is not set, the delay set in [setSyncParam](#setsyncparam) is used. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified; <br>2.Incorrect parameters types. |
| [15100003](../errorcode-distributedKVStore.md#15100003-kv-store-corrupted) | Database corrupted. |
| [15100004](../errorcode-distributedKVStore.md#15100004-failed-to-find-data) | Not found. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';

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
