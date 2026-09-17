# RdbStore

Provides APIs for managing data in an RDB store.

Before using the following APIs, you should obtain an **RdbStore** instance by calling the [getRdbStore](arkts-arkdata-relationalstore-getrdbstore-f.md) method and then call the corresponding method through the instance.

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

## attach

```TypeScript
attach(context: Context, config: StoreConfig, attachName: string, waitTime?: number) : Promise<number>
```

Attaches a database file to the currently linked database.

**Since:** 12

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

## batchInsert

```TypeScript
batchInsert(table: string, values: Array<ValuesBucket>, callback: AsyncCallback<number>): void
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

## beginTrans

```TypeScript
beginTrans(): Promise<number>
```

Begins a transaction before executing the SQL statement.

**Since:** 12

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

## beginTransaction

```TypeScript
beginTransaction(): void
```

BeginTransaction before execute your sql.

**Since:** 9

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

## cleanDirtyData

```TypeScript
cleanDirtyData(table: string, cursor: number, callback: AsyncCallback<void>): void
```

Cleans the dirty data, which is the data deleted in the cloud.

Data with a cursor smaller than the specified cursor will be cleaned up.

**Since:** 11

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

## commit

```TypeScript
commit(): void
```

Commit the the sql you have executed.

**Since:** 9

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

## commit

```TypeScript
commit(txId : number): Promise<void>
```

Commits the SQL statement executed.

**Since:** 12

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

## delete

```TypeScript
delete(predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

Deletes data from the database based on a specified instance object of RdbPredicates.

**Since:** 9

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

## detach

```TypeScript
detach(attachName: string, waitTime?: number) : Promise<number>
```

Detaches a database from this database.

**Since:** 12

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

## execute

```TypeScript
execute(sql: string, txId: number, args?: Array<ValueType>): Promise<ValueType>
```

Executes a SQL statement that contains specified parameters and returns a value of ValueType.

**Since:** 12

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

## insert

```TypeScript
insert(table: string, values: ValuesBucket, callback: AsyncCallback<number>): void
```

Inserts a row of data into the target table.

**Since:** 9

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

## insert

```TypeScript
insert(table: string, values: ValuesBucket, conflict: ConflictResolution, callback: AsyncCallback<number>): void
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
| values | [sendableRelationalStore.ValuesBucket](arkts-arkdata-sendablerelationalstore-valuesbucket-t.md) | Yes | Indicates the row of data ValuesBucket to be inserted into the table. |
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

## rollBack

```TypeScript
rollBack(): void
```

Roll back the sql you have already executed.

**Since:** 9

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

## rollback

```TypeScript
rollback(txId : number): Promise<void>
```

Rolls back the SQL statement executed.

**Since:** 12

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

## sync

```TypeScript
sync(mode: SyncMode, predicates: RdbPredicates, callback: AsyncCallback<Array<[string, number]>>): void
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
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | Yes | {Array&lt;[string, int]&gt;}: devices sync status array, {string}: device id, {int}: device sync status. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Possible causes: 1. The hardware does not support the capability; 2. The chip does not support the capability; 3. A dependent service feature is not supported. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed.<br>**Applicable version:** 12 and later |

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

## update

```TypeScript
update(values: ValuesBucket, predicates: RdbPredicates, callback: AsyncCallback<number>): void
```

Updates data in the database based on a specified instance object of RdbPredicates.

**Since:** 9

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
