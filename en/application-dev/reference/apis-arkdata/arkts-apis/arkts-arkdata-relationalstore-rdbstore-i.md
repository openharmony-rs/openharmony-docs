# RdbStore

```TypeScript
interface RdbStore
```

Provides APIs for managing data in an RDB store.

Before using the following APIs, you should obtain an **RdbStore** instance by calling the [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md#getrdbstore-1) method and then call the corresponding method through the instance.

In addition, use [execute](#execute) to initialize the database table structure and related data first, ensuring that the prerequisites for related API calls are met.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## attach

```TypeScript
attach(fullPath: string, attachName: string, waitTime?: number) : Promise<number>
```

Attaches a database file to the currently linked database.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fullPath | string | Yes | Indicates the path of the database file to attach. |
| attachName | string | Yes | Indicates the alias of the database. |
| waitTime | number | No | Indicates the maximum time allowed for attaching the database file, in seconds. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of attached databases. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-invalid-database-path) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800016](../errorcode-data-rdb.md#14800016-duplicate-rdb-alias) | The database alias already exists. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
// Attach a non-encrypted RDB store to a non-encrypted RDB store.
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).attach("/path/rdbstore1.db", "attachDB").then((number: number) => {
    console.info('attach succeeded');
  }).catch((err: BusinessError) => {
    console.error(`attach failed, code is ${err.code},message is ${err.message}`);
  });
}
```

<a id="attach-1"></a>

## attach

```TypeScript
attach(context: Context, config: StoreConfig, attachName: string, waitTime?: number) : Promise<number>
```

Attaches a database file to the currently linked database.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Indicates the context of an application or ability. |
| config | [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) | Yes | Indicates the [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) configuration of the database related to this RDB store. |
| attachName | string | Yes | Indicates the alias of the database. |
| waitTime | number | No | Indicates the maximum time allowed for attaching the database file, in seconds. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of attached databases. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-invalid-database-path) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800016](../errorcode-data-rdb.md#14800016-duplicate-rdb-alias) | The database alias already exists. |
| [14801001](../errorcode-data-rdb.md#14801001-stage-model-required) | The operation is supported in the stage model only. |
| [14801002](../errorcode-data-rdb.md#14801002-invalid-datagroupid-in-storeconfig) | Invalid data group ID. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

See [attach](#attach)

## backup

```TypeScript
backup(destName: string, callback: AsyncCallback<void>): void
```

Backs up a database in a specified name.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| destName | string | Yes | Indicates the name that saves the database backup. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of backup. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-invalid-database-path) | Failed to open or delete the database by an invalid database path.<br>**Applicable version:** 12 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).backup("dbBackup.db", (err) => {
    if (err) {
      console.error(`Backup failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Backup success.');
  });
}
```

<a id="backup-1"></a>

## backup

```TypeScript
backup(destName: string): Promise<void>
```

Backs up a database in a specified name.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| destName | string | Yes | Indicates the name that saves the database backup. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  let promiseBackup = (store as relationalStore.RdbStore).backup("dbBackup.db");
  promiseBackup.then(() => {
    console.info('Backup success.');
  }).catch((err: BusinessError) => {
    console.error(`Backup failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void
```

Inserts a batch of data into the target table.

The data insertion fails if the API returns an error, or if it returns -1 without throwing an error.

Write 32766 parameters per batch using the [ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md#on_conflict_replace) policy. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. This API returns immediately upon a failure during the process.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt; | Yes | Indicates the rows of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | The number of values that were inserted if the operation is successful. returns -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).batchInsert("EMPLOYEE", valueBuckets, (err, insertNum) => {
    if (err || insertNum == -1) {
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  })
}
```

<a id="batchinsert-1"></a>

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>): Promise<number>
```

Inserts a batch of data into the target table.

The data insertion fails if the API returns an error, or if it returns -1 without throwing an error.

Write 32766 parameters per batch using the [ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md#on_conflict_replace) policy. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. This API returns immediately upon a failure during the process.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt; | Yes | Indicates the rows of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The number of values that were inserted if the operation is successful. Returns -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

RDB store:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).batchInsert("EMPLOYEE", valueBuckets).then((insertNum: number) => {
    if (insertNum == -1) {
      console.error(`batchInsert is failed`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  }).catch((err: BusinessError) => {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  })
}
```

Vector store:

```TypeScript
let createSql = "CREATE TABLE IF NOT EXISTS test (id INTEGER PRIMARY KEY AUTOINCREMENT, data1 floatvector(2));";
await store!.execute(createSql, 0, undefined); // Create a relational table. The second parameter 0 means not enabling an explicit transaction, and the third parameter undefined means the SQL does not use bound parameterization.
let floatVector = Float32Array.from([1.2, 2.3]);
let valueBucketArray = new Array<relationalStore.ValuesBucket>();
for (let i = 0; i < 100; i++) { // Construct a BucketArray for writing.
  const row : relationalStore.ValuesBucket = {
    "id" : i,
    "data1" : floatVector,
  }
  valueBucketArray.push(row);
}
await store!.batchInsert("test", valueBucketArray); // Execute batched writes.
```

## batchInsertSync

```TypeScript
batchInsertSync(table: string, values: Array<ValuesBucket>): number
```

Inserts a batch of data into the target table.

The data insertion fails if the API returns an error, or if it returns -1 without throwing an error.

Write 32766 parameters per batch using the [ON_CONFLICT_REPLACE](arkts-arkdata-relationalstore-conflictresolution-e.md#on_conflict_replace) policy. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. This API returns immediately upon a failure during the process.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt; | Yes | Indicates the rows of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of values that were inserted if the operation is successful. returns -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  try {
    let insertNum: number = (store as relationalStore.RdbStore).batchInsertSync("EMPLOYEE", valueBuckets);
    if (insertNum == -1) {
      console.error(`batchInsertSync is failed`);
      return;
    }
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  } catch (err) {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithConflictResolution

```TypeScript
batchInsertWithConflictResolution(
        table: string,
        values: Array<ValuesBucket>, 
        conflict: ConflictResolution
    ): Promise<number>
```

Inserts a batch of data into the target table.

A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code 14800000 is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 * 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since:** 18

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt; | Yes | Indicates the rows of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | Yes | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The number of values that were inserted if the operation is successful. Returns -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  (store as relationalStore.RdbStore).batchInsertWithConflictResolution("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then((insertNum: number) => {
    console.info(`batchInsert is successful, insertNum = ${insertNum}`);
  }).catch((err: BusinessError) => {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## batchInsertWithConflictResolutionSync

```TypeScript
batchInsertWithConflictResolutionSync(
        table: string,
        values: Array<ValuesBucket>,
        conflict: ConflictResolution
    ): number
```

Inserts a batch of data into the target table.

A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code 14800000 is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 * 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since:** 18

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt; | Yes | Indicates the rows of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | Yes | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of values that were inserted if the operation is successful. returns -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);
let value5 = "Jack";
let value6 = 19;
let value7 = 101.5;
let value8 = new Uint8Array([6, 7, 8, 9, 10]);
let value9 = "Tom";
let value10 = 20;
let value11 = 102.5;
let value12 = new Uint8Array([11, 12, 13, 14, 15]);

const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  'NAME': value5,
  'AGE': value6,
  'SALARY': value7,
  'CODES': value8
};
const valueBucket3: relationalStore.ValuesBucket = {
  'NAME': value9,
  'AGE': value10,
  'SALARY': value11,
  'CODES': value12
};

let valueBuckets = new Array(valueBucket1, valueBucket2, valueBucket3);
if (store != undefined) {
  try {
    let insertNum: number = (store as relationalStore.RdbStore).batchInsertWithConflictResolutionSync("EMPLOYEE", valueBuckets, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
  } catch (err) {
    console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithReturning

```TypeScript
batchInsertWithReturning(table: string, values: Array<ValuesBucket>, config: ReturningConfig,
      conflict?: ConflictResolution): Promise<Result>
```

Inserts a batch of data into the target table and return a resultSet of changed fields.

A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code 14800001 is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 * 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt; | Yes | Indicates the rows of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | Yes | Indicate the information that needs to be returned. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | No | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. The default conflict resolution policy is [ON_CONFLICT_NONE](arkts-arkdata-relationalstore-conflictresolution-e.md#on_conflict_none). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&gt; | The [Result](arkts-arkdata-relationalstore-result-i.md) result of the inserted field includes the number of modified rows and the result set of changed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
async function batchInsertWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = await rdbStore.batchInsertWithReturning("EMPLOYEE", valueBuckets, config);
    console.info(`batchInsertWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`batchInsertWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`batchInsertWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## batchInsertWithReturningSync

```TypeScript
batchInsertWithReturningSync(table: string, values: Array<ValuesBucket>, config: ReturningConfig,
      conflict?: ConflictResolution): Result
```

Inserts a batch of data into the target table and return a resultSet of changed fields.

A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code 14800001 is returned. The product of the number of inserted data records and the size of the union of all fields in the inserted data equals the number of parameters. For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 * 10 = 32760). Ensure that your application complies with this constraint when calling this API to avoid errors caused by excessive parameters.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt; | Yes | Indicates the rows of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | Yes | Indicate the information that needs to be returned. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | No | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. The default conflict resolution policy is [ON_CONFLICT_NONE](arkts-arkdata-relationalstore-conflictresolution-e.md#on_conflict_none). |

**Return value:**

| Type | Description |
| --- | --- |
| [Result](arkts-arkdata-relationalstore-result-i.md) | The [Result](arkts-arkdata-relationalstore-result-i.md) result of the inserted field includes the number of modified rows and the result set of changed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
function batchInsertWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = rdbStore.batchInsertWithReturningSync("EMPLOYEE", valueBuckets, config);
    console.info(`batchInsertWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`batchInsertWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`batchInsertWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## beginTrans

```TypeScript
beginTrans(): Promise<number>
```

Begins a transaction before executing the SQL statement.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Returns the transaction ID. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The RdbStore verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. 4. The sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## beginTransaction

```TypeScript
beginTransaction(): void
```

BeginTransaction before execute your sql.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

if (store != undefined) {
  (store as relationalStore.RdbStore).beginTransaction();
  const valueBucket: relationalStore.ValuesBucket = {
    'NAME': value1,
    'AGE': value2,
    'SALARY': value3,
    'CODES': value4
  };
  (store as relationalStore.RdbStore).insert("test", valueBucket);
  (store as relationalStore.RdbStore).commit();
}
```

## cleanDirtyData

```TypeScript
cleanDirtyData(table: string, cursor: number, callback: AsyncCallback<void>): void
```

Cleans the dirty data, which is the data deleted in the cloud.

Data with a cursor smaller than the specified cursor will be cleaned up.

**Since:** 11

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the name of the table to check. |
| cursor | number | Yes | Indicates the position of the data to be cleaned up. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Indicates the callback invoked to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The cursor must be valid cursor. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).cleanDirtyData('test_table', 100, (err) => {
    if (err) {
      console.error(`clean dirty data failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('clean dirty data succeeded');
  });
}
```

<a id="cleandirtydata-1"></a>

## cleanDirtyData

```TypeScript
cleanDirtyData(table: string, callback: AsyncCallback<void>): void
```

Cleans all dirty data deleted in the cloud.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the name of the table to check. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of clean. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s). 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).cleanDirtyData('test_table', (err) => {
    if (err) {
      console.error(`clean dirty data failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('clean dirty data succeeded');
  });
}
```

<a id="cleandirtydata-2"></a>

## cleanDirtyData

```TypeScript
cleanDirtyData(table: string, cursor?: number): Promise<void>
```

Cleans dirty data deleted in the cloud.

If a cursor is specified, data with a cursor smaller than the specified cursor will be cleaned up. otherwise clean all.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the name of the table to check. |
| cursor | number | No | Indicates the cursor. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The cursor must be valid cursor. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).cleanDirtyData('test_table', 100).then(() => {
    console.info('clean dirty data  succeeded');
  }).catch((err: BusinessError) => {
    console.error(`clean dirty data failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## close

```TypeScript
close(): Promise<void>
```

Close the RdbStore and all resultSets.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).close().then(() => {
    console.info(`close succeeded`);
  }).catch((err: BusinessError) => {
    console.error(`close failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## cloudSync

```TypeScript
cloudSync(mode: SyncMode, progress: Callback<ProgressDetails>, callback: AsyncCallback<void>): void
```

Sync data to cloud.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | indicates the database synchronization mode. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) result. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of cloudSync. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The progress must be a callback type. 5. The callback must be a function. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, (progressDetails) => {
    console.info(`Progress: ${progressDetails}`);
  }, (err) => {
    if (err) {
      console.error(`Cloud sync failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Cloud sync succeeded');
  });
}
```

<a id="cloudsync-1"></a>

## cloudSync

```TypeScript
cloudSync(mode: SyncMode, progress: Callback<ProgressDetails>): Promise<void>
```

Sync data to cloud.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | indicates the database synchronization mode. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) result. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | : The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The progress must be a callback type. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail}`);
  }).then(() => {
    console.info('Cloud sync succeeded');
  }).catch((err: BusinessError) => {
    console.error(`cloudSync failed, code is ${err.code},message is ${err.message}`);
  });
}
```

<a id="cloudsync-2"></a>

## cloudSync

```TypeScript
cloudSync(
      mode: SyncMode,
      tables: string[],
      progress: Callback<ProgressDetails>,
      callback: AsyncCallback<void>
    ): void
```

Sync data to cloud.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | indicates the database synchronization mode. |
| tables | string[] | Yes | indicates the database synchronization mode. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) result. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of cloudSync. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes:     *     <br> 1. Mandatory parameters are left unspecified.    *     <br> 2. Incorrect parameter types.    *     <br> 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
const tables = ["table1", "table2"];

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, tables, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`Progress: ${progressDetail}`);
  }, (err) => {
    if (err) {
      console.error(`Cloud sync failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Cloud sync succeeded');
  });
};
```

<a id="cloudsync-3"></a>

## cloudSync

```TypeScript
cloudSync(mode: SyncMode, tables: string[], progress: Callback<ProgressDetails>): Promise<void>
```

Sync data to cloud.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | indicates the database synchronization mode. |
| tables | string[] | Yes | indicates the database synchronization mode. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) result. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | : The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 2 - 4 parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The tablesNames must be not empty. 5. The progress must be a callback type. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const tables = ["table1", "table2"];

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, tables, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail}`);
  }).then(() => {
    console.info('Cloud sync succeeded');
  }).catch((err: BusinessError) => {
    console.error(`cloudSync failed, code is ${err.code},message is ${err.message}`);
  });
};
```

## cloudSyncEx

```TypeScript
cloudSyncEx(config: CloudSyncConfig, progress: Callback<ProgressDetails>): Promise<void>
```

Synchronizes data to the cloud. This API uses a promise to return the result.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [CloudSyncConfig](arkts-arkdata-relationalstore-cloudsyncconfig-i.md) | Yes | indicates the cloud synchronization config. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the sync progress. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.in("id", ["id1", "id2"]);

let config: relationalStore.CloudSyncConfig = {
  mode: relationalStore.SyncMode.SYNC_MODE_TIME_FIRST,
  enablePredicate: true,
  predicate: predicates
};
if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSyncEx(config, (progressDetails: relationalStore.ProgressDetails) => {
      console.info(`progress: ${progressDetails.schedule}`);
  }).then(() => {
      console.info('cloud sync succeeded');
  }).catch((err: BusinessError) => {
      console.error(`cloud sync failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

## commit

```TypeScript
commit(): void
```

Commit the the sql you have executed.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error.<br>**Applicable version:** 12 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

if (store != undefined) {
  (store as relationalStore.RdbStore).beginTransaction();
  const valueBucket: relationalStore.ValuesBucket = {
    'NAME': value1,
    'AGE': value2,
    'SALARY': value3,
    'CODES': value4
  };
  (store as relationalStore.RdbStore).insert("test", valueBucket);
  (store as relationalStore.RdbStore).commit();
}
```

<a id="commit-1"></a>

## commit

```TypeScript
commit(txId : number): Promise<void>
```

Commits the SQL statement executed.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| txId | number | Yes | Indicates the transaction ID which is obtained by beginTrans. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## createTransaction

```TypeScript
createTransaction(options?: TransactionOptions): Promise<Transaction>
```

create a transaction instance and begin.

**Since:** 14

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| options | [TransactionOptions](arkts-arkdata-relationalstore-transactionoptions-i.md) | No | The option for creating transactions. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Transaction](arkts-arkdata-relationalstore-transaction-i.md)&gt; | The [Transaction](arkts-arkdata-relationalstore-transaction-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database is busy. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).createTransaction().then(async (transaction: relationalStore.Transaction) => {
    transaction.execute("DELETE FROM test WHERE age = ? OR age = ?", [21, 20]).then(() => {
      transaction.commit();
    }).catch((e: BusinessError) => {
      transaction.rollback();
      console.error(`execute sql failed, code is ${e.code},message is ${e.message}`);
    });
  }).catch((err: BusinessError) => {
    (store as relationalStore.RdbStore).close();
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## delete

```TypeScript
delete(predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

Deletes data from the database based on a specified instance object of RdbPredicates.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified delete condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | The number of affected rows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).delete(predicates, (err, rows) => {
    if (err) {
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Delete rows: ${rows}`);
  });
}
```

<a id="delete-1"></a>

## delete

```TypeScript
delete(predicates: RdbPredicates): Promise<number>
```

Deletes data from the database based on a specified instance object of RdbPredicates.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified delete condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | return the number of affected rows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).delete(predicates).then((rows: number) => {
    console.info(`Delete rows: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## deleteSync

```TypeScript
deleteSync(predicates: RdbPredicates): number
```

Deletes data from the database based on a specified instance object of RdbPredicates with sync interface.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified delete condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| number | return the number of rows deleted. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  try {
    let rows: number = (store as relationalStore.RdbStore).deleteSync(predicates);
    console.info(`Delete rows: ${rows}`);
  } catch (err) {
    console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## deleteWithReturning

```TypeScript
deleteWithReturning(predicates: RdbPredicates, config: ReturningConfig): Promise<Result>
```

Deletes data from the database based on a specified instance object of RdbPredicates and return a resultSet of changed fields.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified delete condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | Yes | Indicate the information that needs to be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&gt; | The [Result](arkts-arkdata-relationalstore-result-i.md) result of the deleted field includes the number of modified rows and the result set of changed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
async function deleteWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = await rdbStore.deleteWithReturning(predicates, config);
    console.info(`deleteWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`deleteWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`deleteWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## deleteWithReturningSync

```TypeScript
deleteWithReturningSync(predicates: RdbPredicates, config: ReturningConfig): Result
```

Deletes data from the database based on a specified instance object of RdbPredicates and return a resultSet of changed fields.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified delete condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | Yes | Indicate the information that needs to be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Result](arkts-arkdata-relationalstore-result-i.md) | The [Result](arkts-arkdata-relationalstore-result-i.md) result of the deleted field includes the number of modified rows and the result set of changed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
function deleteWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = rdbStore.deleteWithReturningSync(predicates, config);
    console.info(`deleteWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`deleteWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`deleteWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## detach

```TypeScript
detach(attachName: string, waitTime?: number) : Promise<number>
```

Detaches a database from this database.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| attachName | string | Yes | Indicates the alias of the database. |
| waitTime | number | No | Indicates the maximum time allowed for detaching the database, in seconds. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Return the current number of attached databases. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).detach("attachDB").then((number: number) => {
    console.info(`detach succeeded, number is ${number}`);
  }).catch((err: BusinessError) => {
    console.error(`detach failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## emit

```TypeScript
emit(event: string): void
```

Notifies the registered observers of a change to the data resource specified by Uri.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Indicates the subscription event. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800050](../errorcode-data-rdb.md#14800050-failed-to-obtain-the-subscription-service) | Failed to obtain the subscription service. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).emit('storeObserver');
}
```

## execute

```TypeScript
execute(sql: string, args?: Array<ValueType>): Promise<ValueType>
```

Executes a SQL statement that contains specified parameters and returns a value of ValueType.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| args | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. 4. The sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

RDB store:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

// Check the RDB store integrity.
if (store != undefined) {
  const SQL_CHECK_INTEGRITY = 'PRAGMA integrity_check';
  (store as relationalStore.RdbStore).execute(SQL_CHECK_INTEGRITY).then((data) => {
    console.info(`check result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`check failed, code is ${err.code}, message is ${err.message}`);
  });
}

// Delete all data from the table.
if (store != undefined) {
  const SQL_DELETE_TABLE = 'DELETE FROM test';
  (store as relationalStore.RdbStore).execute(SQL_DELETE_TABLE).then((data) => {
    console.info(`delete result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
  });
}

// Delete a table.
if (store != undefined) {
  const SQL_DROP_TABLE = 'DROP TABLE test';
  (store as relationalStore.RdbStore).execute(SQL_DROP_TABLE).then((data) => {
    console.info(`drop result: ${data}`);
  }).catch((err: BusinessError) => {
    console.error(`drop failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

Vector store:

```TypeScript
// FLOATVECTOR(2) is a vector property with a dimension of 2. The subsequent repr operation should be performed based on this dimension.
let createSql = "CREATE TABLE test (ID INTEGER PRIMARY KEY,REPR FLOATVECTOR(2));";
// Create a table.
await store!.execute(createSql);
// Insert data with parameter binding.
let insertSql = "insert into test VALUES(?, ?);";
const vectorValue: Float32Array = Float32Array.from([1.5, 6.6]);
await store!.execute(insertSql, [0, vectorValue]);
// Execute without using bound parameters.
await store!.execute("insert into test values(1, '[3.5, 1.8]');");
```

<a id="execute-1"></a>

## execute

```TypeScript
execute(sql: string, txId: number, args?: Array<ValueType>): Promise<ValueType>
```

Executes a SQL statement that contains specified parameters and returns a value of ValueType.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| txId | number | Yes | Indicates the transaction ID which is obtained by beginTrans or 0. |
| args | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. 4. The sql(attach,begin,commit,rollback etc.). |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## executeSql

```TypeScript
executeSql(sql: string, callback: AsyncCallback<void>): void
```

Executes a SQL statement that contains specified parameters but returns no value.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of executeSql. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. 4. The sql(attach,begin,commit,rollback etc.).<br>**Applicable version:** 12 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = 'zhangsan'";
if (store != undefined) {
  (store as relationalStore.RdbStore).executeSql(SQL_DELETE_TABLE, (err) => {
    if (err) {
      console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Delete table done.');
  });
}
```

<a id="executesql-1"></a>

## executeSql

```TypeScript
executeSql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<void>): void
```

Executes a SQL statement that contains specified parameters but returns no value.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | Yes | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of executeSql. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. 4. The sql(attach,begin,commit,rollback etc.).<br>**Applicable version:** 12 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = ?";
if (store != undefined) {
  (store as relationalStore.RdbStore).executeSql(SQL_DELETE_TABLE, ['zhangsan'], (err) => {
    if (err) {
      console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Delete table done.');
  });
}
```

<a id="executesql-2"></a>

## executeSql

```TypeScript
executeSql(sql: string, bindArgs?: Array<ValueType>): Promise<void>
```

Executes a SQL statement that contains specified parameters but returns no value.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. 4. The sql(attach,begin,commit,rollback etc.).<br>**Applicable version:** 12 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

const SQL_DELETE_TABLE = "DELETE FROM test WHERE name = 'zhangsan'";
if (store != undefined) {
  (store as relationalStore.RdbStore).executeSql(SQL_DELETE_TABLE).then(() => {
    console.info('Delete table done.');
  }).catch((err: BusinessError) => {
    console.error(`ExecuteSql failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## executeSync

```TypeScript
executeSync(sql: string, args?: Array<ValueType>): ValueType
```

Executes a SQL statement that contains specified parameters and returns a value of ValueType with sync interface.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| args | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |

**Return value:**

| Type | Description |
| --- | --- |
| [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
// Check the RDB store integrity.
if (store != undefined) {
  const SQL_CHECK_INTEGRITY = 'PRAGMA integrity_check';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_CHECK_INTEGRITY);
    console.info(`check result: ${data}`);
  } catch (err) {
    console.error(`check failed, code is ${err.code}, message is ${err.message}`);
  }
}

// Delete all data from the table.
if (store != undefined) {
  const SQL_DELETE_TABLE = 'DELETE FROM test';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_DELETE_TABLE);
    console.info(`delete result: ${data}`);
  } catch (err) {
    console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
  }
}

// Delete a table.
if (store != undefined) {
  const SQL_DROP_TABLE = 'DROP TABLE test';
  try {
    let data = (store as relationalStore.RdbStore).executeSync(SQL_DROP_TABLE);
    console.info(`drop result: ${data}`);
  } catch (err) {
    console.error(`drop failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getModifyTime

```TypeScript
getModifyTime(table: string, columnName: string, primaryKeys: PRIKeyType[]): Promise<ModifyTime>
```

Obtains the modify time of rows corresponding to the primary keys.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the name of the table to check. |
| columnName | string | Yes | Indicates the name of the column to check. |
| primaryKeys | [PRIKeyType](arkts-arkdata-relationalstore-prikeytype-t.md)[] | Yes | Indicates the primary keys of the rows to check. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md)&gt; | The promise returned by the function. ModifyTime indicates the modify time of current row. If this table does not support cloud, the [ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md) will be empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 3 - 4 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The columnName must be not empty string. 5. The PRIKey must be number or string. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let PRIKey = [1, 2, 3];
if (store != undefined) {
  (store as relationalStore.RdbStore).getModifyTime("EMPLOYEE", "NAME", PRIKey)
    .then((modifyTime: relationalStore.ModifyTime) => {
      let size = modifyTime.size;
    })
    .catch((err: BusinessError) => {
      console.error(`getModifyTime failed, code is ${err.code},message is ${err.message}`);
    });
}
```

<a id="getmodifytime-1"></a>

## getModifyTime

```TypeScript
getModifyTime(
      table: string,
      columnName: string,
      primaryKeys: PRIKeyType[],
      callback: AsyncCallback<ModifyTime>
    ): void
```

Obtains the modify time of rows corresponding to the primary keys.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the name of the table to check. |
| columnName | string | Yes | Indicates the name of the column to check. |
| primaryKeys | [PRIKeyType](arkts-arkdata-relationalstore-prikeytype-t.md)[] | Yes | Indicates the primary keys of the rows to check. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md)&gt; | Yes | The callback of getModifyTime. ModifyTime indicates the modify time of current row. If this table does not support cloud, the [ModifyTime](arkts-arkdata-relationalstore-modifytime-t.md) will be empty. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 3 - 4 parameter(s)! 2. The RdbStore must be not nullptr. 3. The tablesNames must be not empty string. 4. The columnName must be not empty string. 5. The PRIKey must be number or string. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let PRIKey = [1, 4, 2, 3];
if (store != undefined) {
  (store as relationalStore.RdbStore).getModifyTime("EMPLOYEE", "NAME", PRIKey, (err, modifyTime: relationalStore.ModifyTime) => {
    if (err) {
      console.error(`getModifyTime failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    let size = modifyTime.size;
  });
}
```

## insert

```TypeScript
insert(table: string, values: ValuesBucket, callback: AsyncCallback<number>): void
```

Inserts a row of data into the target table.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | The row ID if the operation is successful. returns -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1, (err: BusinessError, rowId: number) => {
    if (err) {
      console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Insert is successful, rowId = ${rowId}`);
  });
}
```

<a id="insert-1"></a>

## insert

```TypeScript
insert(table: string, values: ValuesBucket, conflict: ConflictResolution, callback: AsyncCallback<number>): void
```

Inserts a row of data into the target table.

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | Yes | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | The row ID if the operation is successful. returns -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE,
    (err: BusinessError, rowId: number) => {
      if (err) {
        console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
        return;
      }
      console.info(`Insert is successful, rowId = ${rowId}`);
    });
}
```

<a id="insert-2"></a>

## insert

```TypeScript
insert(table: string, values: ValuesBucket): Promise<number>
```

Inserts a row of data into the target table.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The row ID if the operation is successful. return -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1).then((rowId: number) => {
    console.info(`Insert is successful, rowId = ${rowId}`);
  }).catch((err: BusinessError) => {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  });
}
```

<a id="insert-3"></a>

## insert

```TypeScript
insert(table: string, values: ValuesBucket, conflict: ConflictResolution): Promise<number>
```

Inserts a row of data into the target table.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | Yes | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The row ID if the operation is successful. return -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  (store as relationalStore.RdbStore).insert("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then((rowId: number) => {
    console.info(`Insert is successful, rowId = ${rowId}`);
  }).catch((err: BusinessError) => {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## insertSync

```TypeScript
insertSync(table: string, values: ValuesBucket, conflict?: ConflictResolution): number
```

Inserts a row of data into the target table with sync interface.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) to be inserted into the table. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | No | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The row ID if the operation is successful. return -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

if (store != undefined) {
  try {
    let rowId: number = (store as relationalStore.RdbStore).insertSync("EMPLOYEE", valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`Insert is successful, rowId = ${rowId}`);
  } catch (err) {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

<a id="insertsync-1"></a>

## insertSync

```TypeScript
insertSync(table: string, values: sendableRelationalStore.ValuesBucket, conflict?: ConflictResolution): number
```

Inserts a row of data into the target table with sync interface.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| table | string | Yes | Indicates the target table. |
| values | [sendableRelationalStore.ValuesBucket](arkts-arkdata-sendablerelationalstore-valuesbucket-t.md) | Yes | Indicates the row of data [ValuesBucket](arkts-arkdata-sendablerelationalstore-valuesbucket-t.md) to be inserted into the table. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | No | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The row ID if the operation is successful. return -1 otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
import { sendableRelationalStore } from '@kit.ArkData';

const valuesBucket: relationalStore.ValuesBucket = {
  "NAME": 'hangman',
  "AGE": 18,
  "SALARY": 100.5,
  "CODES": new Uint8Array([1, 2, 3])
};
const sendableValuesBucket = sendableRelationalStore.toSendableValuesBucket(valuesBucket);

if (store != undefined) {
  try {
    let rowId: number = (store as relationalStore.RdbStore).insertSync("EMPLOYEE", sendableValuesBucket, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`Insert is successful, rowId = ${rowId}`);
  } catch (err) {
    console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## lockRow

```TypeScript
lockRow(predicates: RdbPredicates): Promise<void>
```

Locks data from the database based on a specified instance object of RdbPredicates.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified lock condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800018](../errorcode-data-rdb.md#14800018-no-match) | No data meets the condition. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).lockRow(predicates).then(() => {
    console.info(`Lock success`);
  }).catch((err: BusinessError) => {
    console.error(`Lock failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string, callback: AsyncCallback<string>): void
```

Obtain distributed table name of specified remote device according to local table name. When query remote device database, distributed table name is needed.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | Indicates the remote device. |
| table | string | Yes | {string}: the distributed table name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).obtainDistributedTableName(deviceId, "EMPLOYEE", (err, tableName) => {
    if (err) {
      console.error(`ObtainDistributedTableName failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ObtainDistributedTableName successfully, tableName= ${tableName}`);
  });
}
```

<a id="obtaindistributedtablename-1"></a>

## obtainDistributedTableName

```TypeScript
obtainDistributedTableName(device: string, table: string): Promise<string>
```

Obtain distributed table name of specified remote device according to local table name. When query remote device database, distributed table name is needed.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | Indicates the remote device. |
| table | string | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | {string}: the distributed table name. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).obtainDistributedTableName(deviceId, "EMPLOYEE").then((tableName: string) => {
    console.info(`ObtainDistributedTableName successfully, tableName= ${tableName}`);
  }).catch((err: BusinessError) => {
    console.error(`ObtainDistributedTableName failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## off

```TypeScript
off(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

Remove specified observer of specified type from the database.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Indicates the event must be string 'dataChange'. |
| type | [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md) | Yes | Indicates the subscription type, which is defined in [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md). If its value is SUBSCRIBE_TYPE_REMOTE, ohos.permission.DISTRIBUTED_DATASYNC is required. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | {Array&lt;string&gt;}: the data change observer already registered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storeObserver = () => {
  console.info(`storeObserver`);
};

try {
  if (store != undefined) {
    (store as relationalStore.RdbStore).on('storeObserver', false, storeObserver);
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Register observer failed, code is ${code},message is ${message}`);
}

try {
  if (store != undefined) {
    (store as relationalStore.RdbStore).off('storeObserver', false, storeObserver);
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Unregister observer failed, code is ${code},message is ${message}`);
}
```

<a id="off-1"></a>

## off

```TypeScript
off(
      event: 'dataChange',
      type: SubscribeType,
      observer?: Callback<Array<string>> | Callback<Array<ChangeInfo>>
    ): void
```

Remove specified observer of specified type from the database.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | indicates the event must be string 'dataChange'. |
| type | [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md) | Yes | indicates the subscription type, which is defined in [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md). If its value is SUBSCRIBE_TYPE_REMOTE, ohos.permission.DISTRIBUTED_DATASYNC is required. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; &#124; [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[ChangeInfo](arkts-arkdata-relationalstore-changeinfo-i.md)&gt;&gt; | No | {Array&lt;string&gt;}: the data change observer already registered. {Array&lt;ChangeInfo&gt;}: the change info already registered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [off](#off)

<a id="off-2"></a>

## off

```TypeScript
off(event: string, interProcess: boolean, observer?: Callback<void>): void
```

Remove specified observer of specified type from the database.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Indicates the subscription event. |
| interProcess | boolean | Yes | Indicates whether it is an interprocess subscription or an in-process subscription. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | The data change observer already registered.<br>**Since:** 12 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800050](../errorcode-data-rdb.md#14800050-failed-to-obtain-the-subscription-service) | Failed to obtain the subscription service. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [off](#off)

<a id="off-3"></a>

## off

```TypeScript
off(event: 'autoSyncProgress', progress?: Callback<ProgressDetails>): void
```

Unregister the database auto synchronization callback.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'autoSyncProgress' | Yes | indicates the event must be string 'autoSyncProgress'. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | No | Callback used to return the [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Need 1 - 3 parameter(s)! 2. The RdbStore must be valid. 3. The event must be a not empty string. 4. The progress must be function. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [off](#off)

<a id="off-4"></a>

## off

```TypeScript
off(event: 'statistics', observer?: Callback<SqlExecutionInfo> ): void
```

Unsubscribes from the SQL statistics.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'statistics' | Yes | Indicates the event type, which must be 'statistics'. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | No | Indicates the callback to unregister. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

See [off](#off)

<a id="off-5"></a>

## off

```TypeScript
off(event: 'perfStat', observer?: Callback<SqlExecutionInfo>): void
```

Unsubscribes from the SQL performance statistics.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'perfStat' | Yes | Event type, which must be 'perfStat'. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | No | Callback to unregister. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

See [off](#off)

<a id="off-6"></a>

## off

```TypeScript
off(event: 'sqliteErrorOccurred', observer?: Callback<ExceptionMessage>): void
```

Unsubscribes from the SQL execution error logs.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'sqliteErrorOccurred' | Yes | Indicates the event type, which must be 'sqliteErrorOccurred'. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExceptionMessage](arkts-arkdata-relationalstore-exceptionmessage-i.md)&gt; | No | Callback to unregister. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

See [off](#off)

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>>): void
```

Subscribes to data changes of this RDB store. The registered callback will be called when data in a distributed RDB store changes. the callback will be invoked.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Indicates the event must be string 'dataChange'. |
| type | [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md) | Yes | Indicates the subscription type, which is defined in [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md). If its value is SUBSCRIBE_TYPE_REMOTE, ohos.permission.DISTRIBUTED_DATASYNC is required. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | {Array&lt;string&gt;}: the observer of data change events in the distributed database. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let storeObserver = () => {
  console.info(`storeObserver`);
};

try {
  if (store != undefined) {
    (store as relationalStore.RdbStore).on('storeObserver', false, storeObserver);
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error(`Register observer failed, code is ${code},message is ${message}`);
}
```

<a id="on-1"></a>

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, observer: Callback<Array<string>> | Callback<Array<ChangeInfo>>): void
```

Subscribes to data changes of this RDB store. The registered callback will be called when data in a distributed RDB store changes.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Indicates the event must be string 'dataChange'. |
| type | [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md) | Yes | Indicates the subscription type, which is defined in [SubscribeType](arkts-arkdata-relationalstore-subscribetype-e.md). If its value is SUBSCRIBE_TYPE_REMOTE, ohos.permission.DISTRIBUTED_DATASYNC is required. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;string&gt;&gt; &#124; [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[ChangeInfo](arkts-arkdata-relationalstore-changeinfo-i.md)&gt;&gt; | Yes | {Array&lt;string&gt;}: the observer of data change events in the distributed database. {Array&lt;ChangeInfo&gt;}: The change info of data change events in the distributed database. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [on](#on)

<a id="on-2"></a>

## on

```TypeScript
on(event: string, interProcess: boolean, observer: Callback<void>): void
```

Registers an observer for the database.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | string | Yes | Event type, which must match the event type in emit. |
| interProcess | boolean | Yes | Indicates whether it is an interprocess subscription or an in-process subscription. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | The observer of data change events in the database. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800050](../errorcode-data-rdb.md#14800050-failed-to-obtain-the-subscription-service) | Failed to obtain the subscription service. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [on](#on)

<a id="on-3"></a>

## on

```TypeScript
on(event: 'autoSyncProgress', progress: Callback<ProgressDetails>): void
```

Register an automatic synchronization callback to the database.

**Since:** 11

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'autoSyncProgress' | Yes | Indicates the event must be string 'autoSyncProgress'. |
| progress | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md)&gt; | Yes | Callback used to return the [ProgressDetails](arkts-arkdata-relationalstore-progressdetails-i.md) result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed; <br>4. The event must be a not empty string; 5. The progress must be function. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

See [on](#on)

<a id="on-4"></a>

## on

```TypeScript
on(event: 'statistics', observer: Callback<SqlExecutionInfo> ): void
```

Subscribes to the SQL statistics.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'statistics' | Yes | Indicates the event type, which must be 'statistics'. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | Yes | Indicates the callback used to return the SQL execution statistics SqlExeInfo in the database. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

See [on](#on)

<a id="on-5"></a>

## on

```TypeScript
on(event: 'perfStat', observer: Callback<SqlExecutionInfo>): void
```

Subscribes to the SQL performance statistics.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'perfStat' | Yes | Event type, which must be 'perfStat'. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md)&gt; | Yes | Callback used to return the SQL execution statistics [SqlExecutionInfo](arkts-arkdata-relationalstore-sqlexecutioninfo-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

See [on](#on)

<a id="on-6"></a>

## on

```TypeScript
on(event: 'sqliteErrorOccurred', observer: Callback<ExceptionMessage>): void
```

Subscribes to the SQL execution error logs.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'sqliteErrorOccurred' | Yes | Event type, which must be 'sqliteErrorOccurred'. |
| observer | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ExceptionMessage](arkts-arkdata-relationalstore-exceptionmessage-i.md)&gt; | Yes | Callback used to return the SQL execution errorlog [ExceptionMessage](arkts-arkdata-relationalstore-exceptionmessage-i.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

See [on](#on)

## query

```TypeScript
query(predicates: RdbPredicates, callback: AsyncCallback<ResultSet>): void
```

Queries data in the database based on specified conditions.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Yes | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query(predicates, async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  });
}
```

<a id="query-1"></a>

## query

```TypeScript
query(predicates: RdbPredicates, columns: Array<string>, callback: AsyncCallback<ResultSet>): void
```

Queries data in the database based on specified conditions.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | Yes | The columns to query. If the value is empty array, the query applies to all columns. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Yes | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"], async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  });
}
```

<a id="query-2"></a>

## query

```TypeScript
query(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

Queries data in the database based on specified conditions.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | No | The columns to query. If the value is null, the query applies to all columns. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## queryByStep

```TypeScript
queryByStep(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>
```

Query data in the database step‑by‑step based on SQL statements.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute.<br>Value range: (0, +∞) <br>A valid SQL statement must be used. Otherwise, an error code may be thrown when ResultSet is used. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. <br>Default value:The default value is an empty array. <br>The value must be the same as the number of placeholders in the SQL statement. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).queryByStep("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'").then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

<a id="querybystep-1"></a>

## queryByStep

```TypeScript
queryByStep(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

Queries data in the database step‑by‑step based on specified conditions.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | No | The columns to query. If the value is null, the query applies to all columns.<br>Default value: empty array by default. <br>If an empty array is transferred, all columns are queried. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).queryByStep(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

## queryLockedRow

```TypeScript
queryLockedRow(predicates: RdbPredicates, columns?: Array<string>): Promise<ResultSet>
```

Queries locked data in the database based on specified conditions.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | No | The columns to query. If the value is null, the query applies to all columns. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).queryLockedRow(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## querySql

```TypeScript
querySql(sql: string, callback: AsyncCallback<ResultSet>): void
```

Queries data in the database based on SQL statement.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Yes | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |

**Examples**

RDB store:

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'", async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  });
}
```

Vector store:

```TypeScript
// <-> means to calculate vector similarity, and <=> means to calculate the cosine distance.
const querySql = "select id, repr <-> '[1.5,5.6]' as distance from test ORDER BY repr <-> '[1.5,5.6]' limit 10 offset 1;";
let resultSet = await store.querySql(querySql);

// Aggregate query. GROUP BY supports multiple columns.
const querySql1 = "select id, repr from test group by id, repr having max(repr<=>'[1.5,5.6]');";
let resultSet1 = await store.querySql(querySql1);

// Subquery. A maximum of 32 nested layers are supported.
const querySql2 = "select * from test where id in (select id from test1)";
let resultSet2 = await store.querySql(querySql2);
```

<a id="querysql-1"></a>

## querySql

```TypeScript
querySql(sql: string, bindArgs: Array<ValueType>, callback: AsyncCallback<ResultSet>): void
```

Queries data in the database based on SQL statement.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | Yes | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Yes | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = ?", ['sanguo'], async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  });
}
```

<a id="querysql-2"></a>

## querySql

```TypeScript
querySql(sql: string, bindArgs?: Array<ValueType>): Promise<ResultSet>
```

Queries data in the database based on SQL statement.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |

**Examples**

RDB store:

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'").then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  });
}
```

Vector store:

```TypeScript
// Query the top 10 records with ID of 1 and the similarity to [1.5, 2.5] is less than 0.5, and sort them in ascending order by similarity.
const querySql = "select id, repr <-> ? as distance from test where id = ? and repr <-> ? < 0.5 ORDER BY repr <-> ? limit 10;";
const vectorValue: Float32Array = new Float32Array([1.5, 2.5]);
let resultSet = await store.querySql(querySql, [vectorValue, 1, vectorValue, vectorValue]);
```

## querySqlSync

```TypeScript
querySqlSync(sql: string, bindArgs?: Array<ValueType>): ResultSet
```

Queries data in the database based on SQL statement with sync interface.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | Indicates the SQL statement to execute. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Indicates the [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) values of the parameters in the SQL statement. The values are strings. |

**Return value:**

| Type | Description |
| --- | --- |
| [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |

**Examples**

```TypeScript
if (store != undefined) {
  let resultSet: relationalStore.ResultSet | undefined;
  try {
    resultSet = store.querySqlSync("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'");
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code},message is ${err.message}`);
  } finally {
    // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
    if (resultSet) {
      resultSet.close();
    }
  }
}
```

## querySqlWithoutRowCount

```TypeScript
querySqlWithoutRowCount(sql: string, bindArgs?: Array<ValueType>): Promise<LiteResultSet>
```

Queries data from the RDB store based on specified conditions without calculating the row count. This API uses a promise to return the result and delivers better performance than the [querySql](arkts-arkdata-relationalstore-transaction-i.md#querysql) API. The number of relational operators between expressions and operators in the SQL statement cannot exceed 1,000.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | SQL statement to run. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, leave this parameter blank. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md)&gt; | Promise used to return the result. If the operation is successful, a **LiteResultSet** object will be returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
async function querySqlWithoutRowCountEmployee(store : relationalStore.RdbStore) {
  if (store != undefined) {
    let resultSet: relationalStore.LiteResultSet | undefined;
    try {
      resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
      if (resultSet != undefined) {
        // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
        while (resultSet.goToNextRow()) {
          const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
          const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
          const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
          const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
          console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
        }
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      if (resultSet != undefined) {
        resultSet.close();
      }
    }
  }
}
```

## querySqlWithoutRowCountSync

```TypeScript
querySqlWithoutRowCountSync(sql: string, bindArgs?: Array<ValueType>): LiteResultSet
```

Queries data from the RDB store based on specified SQL statements without calculating the row count. The number of relational operators between expressions and operators in the SQL statement cannot exceed 1,000. If complex logic and a large number of loops are involved in the operations on the **LiteResultSet** obtained by **querySqlWithoutRowCountSync**, the freeze problem may occur. You are advised to perform this operation in the [taskpool](../../apis-arkts/arkts-apis/arkts-arkts-taskpool.md) thread.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sql | string | Yes | SQL statement to run. |
| bindArgs | Array&lt;[ValueType](arkts-arkdata-relationalstore-valuetype-t.md)&gt; | No | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, leave this parameter blank. The default value is null. |

**Return value:**

| Type | Description |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | If the operation is successful, a **LiteResultSet** object will be returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
if (store != undefined) {
  let resultSet: relationalStore.LiteResultSet | undefined;
  try {
    resultSet = store.querySqlWithoutRowCountSync('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
    if (resultSet != undefined) {
      resultSet.close();
    }
  }
}
```

## querySync

```TypeScript
querySync(predicates: RdbPredicates, columns?: Array<string>): ResultSet
```

Queries data in the database based on specified conditions with sync function.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | No | The columns to query. If the value is empty array, the query applies to all columns. |

**Return value:**

| Type | Description |
| --- | --- |
| [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |

**Examples**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  let resultSet: relationalStore.ResultSet | undefined;
  try {
    resultSet = store.querySync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
    if (resultSet) {
      resultSet.close();
    }
  }
}
```

## queryWithoutRowCount

```TypeScript
queryWithoutRowCount(predicates: RdbPredicates, columns?: Array<string>): Promise<LiteResultSet>
```

Queries data without rowCount in the database based on specified conditions.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | No | The columns to query. If the value is null, the query applies to all columns. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md)&gt; | The [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
async function queryWithoutRowCountEmployee(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    let resultSet: relationalStore.LiteResultSet | undefined;
    try {
      resultSet = await store.queryWithoutRowCount(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
      if (resultSet != undefined) {
        // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
        while (resultSet.goToNextRow()) {
          const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
          const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
          const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
          const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
          console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
        }
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      if (resultSet != undefined) {
        resultSet.close();
      }
    }
  }
}
```

## queryWithoutRowCountSync

```TypeScript
queryWithoutRowCountSync(predicates: RdbPredicates, columns?: Array<string>): LiteResultSet
```

Queries data without rowCount in the database based on specified conditions with sync function.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | No | The columns to query. If the value is null, the query applies to all columns. |

**Return value:**

| Type | Description |
| --- | --- |
| [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) | The [LiteResultSet](arkts-arkdata-relationalstore-literesultset-c.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  let resultSet: relationalStore.LiteResultSet | undefined;
  try {
    resultSet = store.queryWithoutRowCountSync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
    if (resultSet != undefined) {
      // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    }
  } catch (err) {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  } finally {
    // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
    if (resultSet != undefined) {
      resultSet.close();
    }
  }
}
```

## rekey

```TypeScript
rekey(cryptoParam?: CryptoParam): Promise<void>
```

Changes the key used to encrypt the database.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cryptoParam | [CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md) | No | Specifies the crypto parameters used to rekey. If valid cryptoParam passed, the cryptoParam is used to rekey. If cryptoParam is null or not passed, the default cryptoParam is used. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |

**Examples**

For details about the definition of this.context in the sample code, see the application [context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md) of the stage model.

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// Example 1: Use default encryption parameters.
export default class EntryAbility extends UIAbility {
  onCreate() {
    let store: relationalStore.RdbStore | undefined = undefined;
    const STORE_CONFIG1: relationalStore.StoreConfig = {
      name: 'rdbstore1.db',
      securityLevel: relationalStore.SecurityLevel.S3,
      encrypt: true
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG1).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');

      let cryptoParam1: relationalStore.CryptoParam = {
        encryptionKey: new Uint8Array()
      };

      if (store != undefined) {
        try {
          await (store as relationalStore.RdbStore).rekey(cryptoParam1);
          console.info('rekey successful');
        } catch (err) {
          let e = err as BusinessError;
          console.error(`rekey failed, code is ${err.code}, message is ${err.message}`);
        }
      }
    }).catch((err: Error) => {
      let e = err as BusinessError;
      console.error(`Get RdbStore failed, code is ${e.code}, message is ${e.message}`);
    });
  }
}
```

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// Example 2: Use custom encryption parameters.
export default class EntryAbility extends UIAbility {
  onCreate() {
    let store: relationalStore.RdbStore | undefined = undefined;
    let cryptoParam: relationalStore.CryptoParam = {
      encryptionKey: new Uint8Array([1, 2, 3, 4, 5, 6]),
      iterationCount: 1000,
      encryptionAlgo: relationalStore.EncryptionAlgo.AES_256_GCM,
      hmacAlgo: relationalStore.HmacAlgo.SHA256,
      kdfAlgo: relationalStore.KdfAlgo.KDF_SHA256,
      cryptoPageSize: 1024
    };

    const STORE_CONFIG2: relationalStore.StoreConfig = {
      name: 'rdbstore2.db',
      securityLevel: relationalStore.SecurityLevel.S3,
      encrypt: true,
      cryptoParam: cryptoParam
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG2).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');
      let cryptoParam2: relationalStore.CryptoParam = {
        encryptionKey: new Uint8Array([6, 5, 4, 3, 2, 1]),
        iterationCount: 1000,
        encryptionAlgo: relationalStore.EncryptionAlgo.AES_256_GCM,
        hmacAlgo: relationalStore.HmacAlgo.SHA256,
        kdfAlgo: relationalStore.KdfAlgo.KDF_SHA256,
        cryptoPageSize: 1024
      };

      if (store != undefined) {
        try {
          await (store as relationalStore.RdbStore).rekey(cryptoParam2);
          console.info('rekey successful');
        } catch (err) {
          let e = err as BusinessError;
          console.error(`rekey failed, code is ${err.code}, message is ${err.message}`);
        }
      }
    }).catch((err: Error) => {
      let e = err as BusinessError;
      console.error(`Get RdbStore failed, code is ${e.code}, message is ${e.message}`);
    });
  }
}
```

```TypeScript
// EntryAbility.ets
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
// Example 3: Update the key of a vector store.
export default class EntryAbility extends UIAbility {
  onCreate() {
    let store: relationalStore.RdbStore | undefined = undefined;
    let cryptoParam: relationalStore.CryptoParam = {
      encryptionKey: new Uint8Array([1, 2, 3, 4, 5, 6]),
    };
    const STORE_CONFIG1: relationalStore.StoreConfig = {
      name: 'test.db',
      securityLevel: relationalStore.SecurityLevel.S2,
      encrypt: true,
      vector: true,
      cryptoParam: cryptoParam,
    };

    relationalStore.getRdbStore(this.context, STORE_CONFIG1).then(async (rdbStore: relationalStore.RdbStore) => {
      store = rdbStore;
      console.info('Get RdbStore successfully.');

      let newCryptoParam: relationalStore.CryptoParam = {
        encryptionKey: new Uint8Array([6, 5, 4, 3, 2, 1]),
      };

      if (store != undefined) {
        try {
          await (store as relationalStore.RdbStore).rekey(newCryptoParam);
          console.info('rekey successful');
        } catch (err) {
          let e = err as BusinessError;
          console.error(`rekey failed, code is ${err.code}, message is ${err.message}`);
        }
      }
    }).catch((err: Error) => {
      let e = err as BusinessError;
      console.error(`Get RdbStore failed, code is ${e.code}, message is ${e.message}`);
    });
  }
}
```

## rekeyEx

```TypeScript
rekeyEx(cryptoParam: CryptoParam): Promise<void>
```

Change the encryption parameters of the database.

**Since:** 22

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cryptoParam | [CryptoParam](arkts-arkdata-relationalstore-cryptoparam-i.md) | Yes | Crypto parameters. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |

## remoteQuery

```TypeScript
remoteQuery(
      device: string,
      table: string,
      predicates: RdbPredicates,
      columns: Array<string>,
      callback: AsyncCallback<ResultSet>
    ): void
```

Queries remote data in the database based on specified conditions before Synchronizing Data.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | Indicates specified remote device. |
| table | string | Yes | Indicates the target table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified remote remote query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | Yes | The columns to remote query. If the value is empty array, the remote query applies to all columns. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | Yes | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.greaterThan("id", 0);
if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).remoteQuery(deviceId, "EMPLOYEE", predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"], async (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  });
}
```

<a id="remotequery-1"></a>

## remoteQuery

```TypeScript
remoteQuery(device: string, table: string, predicates: RdbPredicates, columns: Array<string>): Promise<ResultSet>
```

Queries remote data in the database based on specified conditions before Synchronizing Data.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| device | string | Yes | Indicates specified remote device. |
| table | string | Yes | Indicates the target table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified remote remote query condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| columns | Array&lt;string&gt; | Yes | The columns to remote query. If the value is empty array, the remote query applies to all columns. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)&gt; | The [ResultSet](arkts-arkdata-relationalstore-resultset-i.md) object if the operation is successful. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceId: string | undefined = undefined;

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  if (!devices || devices.length === 0) {
    console.error("No available devices found");
  } else {
    deviceId = devices[0].networkId;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.greaterThan("id", 0);
if (store != undefined && deviceId != undefined) {
  (store as relationalStore.RdbStore).remoteQuery(deviceId, "EMPLOYEE", predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then(async (resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    try {
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
        const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
        const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
        const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
    } catch (err) {
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    } finally {
      // Release the memory of resultSet. If the memory is not released, FD or memory leaks may occur.
      resultSet.close();
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to remoteQuery, code is ${err.code},message is ${err.message}`);
  });
}
```

## restore

```TypeScript
restore(srcName: string, callback: AsyncCallback<void>): void
```

Restores a database from a specified database file.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcName | string | Yes | Indicates the name that saves the database file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of restore. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).restore("dbBackup.db", (err) => {
    if (err) {
      console.error(`Restore failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Restore success.');
  });
}
```

<a id="restore-1"></a>

## restore

```TypeScript
restore(srcName: string): Promise<void>
```

Restores a database from a specified database file.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srcName | string | Yes | Indicates the name that saves the database file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  let promiseRestore = (store as relationalStore.RdbStore).restore("dbBackup.db");
  promiseRestore.then(() => {
    console.info('Restore success.');
  }).catch((err: BusinessError) => {
    console.error(`Restore failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## rollBack

```TypeScript
rollBack(): void
```

Roll back the sql you have already executed.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: The RdbStore verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error.<br>**Applicable version:** 12 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Lisa";
let value2 = 18;
let value3 = 100.5;
let value4 = new Uint8Array([1, 2, 3]);

if (store != undefined) {
  try {
    (store as relationalStore.RdbStore).beginTransaction();
    const valueBucket: relationalStore.ValuesBucket = {
      'NAME': value1,
      'AGE': value2,
      'SALARY': value3,
      'CODES': value4
    };
    (store as relationalStore.RdbStore).insert("test", valueBucket);
    (store as relationalStore.RdbStore).commit();
  } catch (err) {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error(`Transaction failed, code is ${code},message is ${message}`);
    (store as relationalStore.RdbStore).rollBack();
  }
}
```

## rollback

```TypeScript
rollback(txId : number): Promise<void>
```

Rolls back the SQL statement executed.

**Since:** 12

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| txId | number | Yes | Indicates the transaction ID which is obtained by beginTrans. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
if (store != null) {
  let txId: number;
  (store as relationalStore.RdbStore).beginTrans().then((tempTxId: number) => {
    txId = tempTxId;
    (store as relationalStore.RdbStore).execute("DELETE FROM TEST WHERE age = ? OR age = ?", txId, ["18", "20"])
      .then(() => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).commit(txId);
        }
      })
      .catch((err: BusinessError) => {
        if (txId !== undefined) {
          (store as relationalStore.RdbStore).rollback(txId);
        }
        console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
      });
  });
}
```

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>, callback: AsyncCallback<void>): void
```

Set table to be distributed table.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | Yes | Indicates the table names you want to set. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setDistributedTables. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], (err) => {
    if (err) {
      console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('SetDistributedTables successfully.');
  });
}
```

<a id="setdistributedtables-1"></a>

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>): Promise<void>
```

Set table to be distributed table.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | Yes | Indicates the table names you want to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"]).then(() => {
    console.info('SetDistributedTables successfully.');
  }).catch((err: BusinessError) => {
    console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
  });
}
```

<a id="setdistributedtables-2"></a>

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>, type: DistributedType, callback: AsyncCallback<void>): void
```

Set table to be distributed table.

**Since:** 10

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | Yes | Indicates the table names you want to set. |
| type | [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | Yes | Indicates the distributed type [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md). ohos.permission.DISTRIBUTED_DATASYNC is required only when type is DISTRIBUTED_DEVICE. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setDistributedTables. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800051](../errorcode-data-rdb.md#14800051-inconsistent-distributed-table-type) | The type of the distributed table does not match. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], relationalStore.DistributedType.DISTRIBUTED_CLOUD, (err) => {
    if (err) {
      console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('SetDistributedTables successfully.');
  });
}
```

<a id="setdistributedtables-3"></a>

## setDistributedTables

```TypeScript
setDistributedTables(
      tables: Array<string>,
      type: DistributedType,
      config: DistributedConfig,
      callback: AsyncCallback<void>
    ): void
```

Set table to be distributed table.

**Since:** 10

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | Yes | Indicates the table names you want to set. |
| type | [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | Yes | Indicates the distributed type [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md). ohos.permission.DISTRIBUTED_DATASYNC is required only when type is DISTRIBUTED_DEVICE. |
| config | [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md) | Yes | Indicates the distributed config of the tables. For details, see [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | The callback of setDistributedTables. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800051](../errorcode-data-rdb.md#14800051-inconsistent-distributed-table-type) | The type of the distributed table does not match. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], relationalStore.DistributedType.DISTRIBUTED_CLOUD, {
    autoSync: true
  }, (err) => {
    if (err) {
      console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('SetDistributedTables successfully.');
  });
}
```

<a id="setdistributedtables-4"></a>

## setDistributedTables

```TypeScript
setDistributedTables(tables: Array<string>, type?: DistributedType, config?: DistributedConfig): Promise<void>
```

Set table to be a distributed table.

**Since:** 10

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| tables | Array&lt;string&gt; | Yes | Indicates the table names you want to set. |
| type | [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md) | No | Indicates the distributed type [DistributedType](arkts-arkdata-relationalstore-distributedtype-e.md). ohos.permission.DISTRIBUTED_DATASYNC is required only when type is DISTRIBUTED_DEVICE. |
| config | [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md) | No | Indicates the distributed config of the tables. For details, see [DistributedConfig](arkts-arkdata-relationalstore-distributedconfig-i.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800051](../errorcode-data-rdb.md#14800051-inconsistent-distributed-table-type) | The type of the distributed table does not match. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).setDistributedTables(["EMPLOYEE"], relationalStore.DistributedType.DISTRIBUTED_CLOUD, {
    autoSync: true
  }).then(() => {
    console.info('SetDistributedTables successfully.');
  }).catch((err: BusinessError) => {
    console.error(`SetDistributedTables failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## setLocale

```TypeScript
setLocale(locale: string) : Promise<void>
```

Support for collations in different languages.

**Since:** 20

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| locale | string | Yes | Language related to the locale. for example, zh. The value complies with the ISO 639 standard. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
try {
  if (store != undefined) {
    await store.setLocale("zh");
    store.querySql("SELECT * FROM EMPLOYEE ORDER BY NAME COLLATE LOCALES", async (err, resultSet) => {
      if (err) {
        console.error(`Query failed, code: ${err.code}, message: ${err.message}`);
        return;
      }
      console.info(`ResultSet rowCount ${resultSet.rowCount}`);
    });
  }
} catch (err) {
  console.error(`SetLocale failed, code: ${err.code}, message: ${err.message}`);
}
```

## stopCloudSync

```TypeScript
stopCloudSync(): Promise<void>
```

Stops synchronizing data with the cloud.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | : The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. 4. The device does not support the cloud synchronization capability. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
import { relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';
if (store != undefined) {
  (store as relationalStore.RdbStore).stopCloudSync().then(() => {
    console.info('Succeeded in stopping cloud sync');
  }).catch((err: BusinessError) => {
    console.error(`Failed to stop cloud sync. Code: ${err.code}, message: ${err.message}`);
  });
}
```

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback<Array<[string, number]>>): void
```

Sync data between devices.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | Indicates the database synchronization mode. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified sync condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | Yes | {Array&lt;[string, int]&gt;}: devices sync status array, {string}: device id, {int}: device sync status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceIds: Array<string> = [];

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].networkId!;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.inDevices(deviceIds);
if (store != undefined) {
  (store as relationalStore.RdbStore).sync(relationalStore.SyncMode.SYNC_MODE_PUSH, predicates, (err, result) => {
    if (err) {
      console.error(`Sync failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info('Sync done.');
    for (let i = 0; i < result.length; i++) {
      console.info(`device= ${result[i][0]}, status= ${result[i][1]}`);
    }
  });
}
```

<a id="sync-1"></a>

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates): Promise<Array<[string, number]>>
```

Sync data between devices.

**Since:** 9

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | Indicates the database synchronization mode. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified sync condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[string, number]&gt;&gt; | {Array&lt;[string, int]&gt;}: devices sync status array, {string}: device id, {int}: device sync status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceIds: Array<string> = [];

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].networkId!;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.inDevices(deviceIds);
if (store != undefined) {
  (store as relationalStore.RdbStore).sync(relationalStore.SyncMode.SYNC_MODE_PUSH, predicates).then((result: Object[][]) => {
    console.info('Sync done.');
    for (let i = 0; i < result.length; i++) {
      console.info(`device= ${result[i][0]}, status= ${result[i][1]}`);
    }
  }).catch((err: BusinessError) => {
    console.error(`Sync failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## syncEx

```TypeScript
syncEx(mode: SyncMode, predicates: RdbPredicates): Promise<Array<SyncResult>>
```

Sync data between devices.

1. The difference between the sync interface and the syncEx interface is that they can return more error codes,
but their functionality is similar.
2. Before invoking synchronization, call setdistributedTable to set the distributed table.

**Since:** 26.0.0

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [SyncMode](arkts-arkdata-relationalstore-syncmode-e.md) | Yes | Indicates the database synchronization mode.<br>Only SYNC_MODE_PUSH and SYNC_MODE_PULL are supported. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified sync condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[SyncResult](arkts-arkdata-relationalstore-syncresult-i.md)&gt;&gt; | devices sync result array, see [SyncResult](arkts-arkdata-relationalstore-syncresult-i.md) for details. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
import { BusinessError } from '@kit.BasicServicesKit';

let dmInstance: distributedDeviceManager.DeviceManager;
let deviceIds: Array<string> = [];

try {
  dmInstance = distributedDeviceManager.createDeviceManager("com.example.appdatamgrverify");
  let devices: Array<distributedDeviceManager.DeviceBasicInfo> = dmInstance.getAvailableDeviceListSync();
  for (let i = 0; i < devices.length; i++) {
    deviceIds[i] = devices[i].networkId!;
  }
} catch (err) {
  let code = (err as BusinessError).code;
  let message = (err as BusinessError).message;
  console.error("createDeviceManager errCode:" + code + ",errMessage:" + message);
}

let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.inDevices(deviceIds);
store.syncEx(relationalStore.SyncMode.SYNC_MODE_PUSH, predicates).then((result: relationalStore.SyncResult[]) => {
  for (let i = 0; i < result.length; i++) {
    let code = result[i].code;
    let message = result[i].message;
    if (code === 0) {
      console.info(`SyncEx success`);
    } else {
      console.error(`SyncEx failed, message: ${message} code : ${code}`);
    }
  }
}).catch((err: Error) => {
    let code = (err as BusinessError).code;
    let message = (err as BusinessError).message;
    console.error("syncEx errCode:" + code + ",errMessage:" + message);
});
```

## unlockRow

```TypeScript
unlockRow(predicates: RdbPredicates): Promise<void>
```

Unlocks data from the database based on a specified instance object of RdbPredicates.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | The specified Unlock condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800018](../errorcode-data-rdb.md#14800018-no-match) | No data meets the condition. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).unlockRow(predicates).then(() => {
    console.info(`Unlock success`);
  }).catch((err: BusinessError) => {
    console.error(`Unlock failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

Updates data in the database based on a specified instance object of RdbPredicates.

**Since:** 9

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data to be updated in the database. The key-value pairs are associated with column names of the database table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Indicates the specified update condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | The number of affected rows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates, (err, rows) => {
    if (err) {
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Updated row count: ${rows}`);
  });
}
```

<a id="update-1"></a>

## update

```TypeScript
update(
      values: ValuesBucket,
      predicates: RdbPredicates,
      conflict: ConflictResolution,
      callback: AsyncCallback<number>
    ): void
```

Updates data in the database based on a specified instance object of RdbPredicates.

**Since:** 10

**Model restriction:** This API can be used in both the stage model and FA model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data to be updated in the database. The key-value pairs are associated with column names of the database table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Indicates the specified update condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | Yes | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | The number of affected rows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE, (err, rows) => {
    if (err) {
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
      return;
    }
    console.info(`Updated row count: ${rows}`);
  });
}
```

<a id="update-2"></a>

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates): Promise<number>
```

Updates data in the database based on a specified instance object of RdbPredicates.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data to be updated in the database. The key-value pairs are associated with column names of the database table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Indicates the specified update condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The number of affected rows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit.<br>**Applicable version:** 10 and later |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates).then(async (rows: number) => {
    console.info(`Updated row count: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
  });
}
```

<a id="update-3"></a>

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, conflict: ConflictResolution): Promise<number>
```

Updates data in the database based on a specified instance object of RdbPredicates.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data to be updated in the database. The key-value pairs are associated with column names of the database table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Indicates the specified update condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | Yes | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | The number of affected rows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit.<br>**Applicable version:** 12 and later |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation.<br>**Applicable version:** 12 and later |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch.<br>**Applicable version:** 12 and later |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly.<br>**Applicable version:** 12 and later |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE).then(async (rows: number) => {
    console.info(`Updated row count: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
  });
}
```

## updateSync

```TypeScript
updateSync(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): number
```

Updates data in the database based on a specified instance object of RdbPredicates with sync interface.

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data to be updated in the database. The key-value pairs are associated with column names of the database table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Indicates the specified update condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | No | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to insert data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| number | The number of affected rows. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort. |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800034](../errorcode-data-rdb.md#14800034-incorrect-use-of-sqlite-library) | SQLite: Library used incorrectly. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: relationalStore.ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4
};
const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4
};
const valueBucket3: relationalStore.ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4
};

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  try {
    let rows: number = (store as relationalStore.RdbStore).updateSync(valueBucket1, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
    console.info(`Updated row count: ${rows}`);
  } catch (err) {
    console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## updateWithReturning

```TypeScript
updateWithReturning(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig,
      conflict?: ConflictResolution): Promise<Result>
```

Updates data in the database based on a specified instance object of RdbPredicates and return a resultSet of changed fields.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data to be updated in the database. The key-value pairs are associated with column names of the database table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Indicates the specified update condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | Yes | Indicate the information that needs to be returned. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | No | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to update data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Result](arkts-arkdata-relationalstore-result-i.md)&gt; | The [Result](arkts-arkdata-relationalstore-result-i.md) result of the updated field includes the number of modified rows and the result set of changed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
async function updateWithReturningExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = await rdbStore.updateWithReturning(valueBucket1, predicates, config);
    console.info(`updateWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`updateWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`updateWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## updateWithReturningSync

```TypeScript
updateWithReturningSync(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig,
      conflict?: ConflictResolution): Result
```

Updates data in the database based on a specified instance object of RdbPredicates and return a resultSet of changed fields.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| values | [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Yes | Indicates the row of data to be updated in the database. The key-value pairs are associated with column names of the database table. |
| predicates | [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md) | Yes | Indicates the specified update condition by the instance object of [RdbPredicates](arkts-arkdata-relationalstore-rdbpredicates-c.md). |
| config | [ReturningConfig](arkts-arkdata-relationalstore-returningconfig-i.md) | Yes | Indicate the information that needs to be returned. |
| conflict | [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) | No | Indicates the [ConflictResolution](arkts-arkdata-relationalstore-conflictresolution-e.md) to update data into the table. |

**Return value:**

| Type | Description |
| --- | --- |
| [Result](arkts-arkdata-relationalstore-result-i.md) | The [Result](arkts-arkdata-relationalstore-result-i.md) result of the updated field includes the number of modified rows and the result set of changed data. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked. |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked. |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full. |
| [14800032](../errorcode-data-rdb.md#14800032-sqlite-abort-due-to-constraint-violation) | SQLite: Abort due to constraint violation. |
| [14800033](../errorcode-data-rdb.md#14800033-sqlite-data-types-mismatch) | SQLite: Data type mismatch. |
| [14800047](../errorcode-data-rdb.md#14800047-wal-file-size-exceeds-the-default-limit) | The WAL file size exceeds the default limit. |

**Examples**

```TypeScript
function updateWithReturningSyncExample(rdbStore: relationalStore.RdbStore)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    rdbStore.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = rdbStore.updateWithReturningSync(valueBucket1, predicates, config);
    console.info(`updateWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`updateWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
    results.resultSet.close();
  } catch (e) {
    console.error(`updateWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## rebuilt

```TypeScript
rebuilt: RebuildType
```

Set whether the database is rebuilt.

**Type:** [RebuildType](arkts-arkdata-relationalstore-rebuildtype-e.md)

**Since:** 12

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## version

```TypeScript
version: number
```

Set RdbStore version. The version number must be an integer greater than 0. Obtains the RdbStore version.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported.<br>**Applicable version:** 12 and later |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error.<br>**Applicable version:** 12 and later |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |
| [14800015](../errorcode-data-rdb.md#14800015-rdb-store-not-respond) | The database does not respond.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800024](../errorcode-data-rdb.md#14800024-sqlite-database-file-locked) | SQLite: The database file is locked.<br>**Applicable version:** 12 and later |
| [14800025](../errorcode-data-rdb.md#14800025-sqlite-database-table-locked) | SQLite: A table in the database is locked.<br>**Applicable version:** 12 and later |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
