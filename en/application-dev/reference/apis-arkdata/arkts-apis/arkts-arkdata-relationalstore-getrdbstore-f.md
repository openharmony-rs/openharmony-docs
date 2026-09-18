# getRdbStore

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig, callback: AsyncCallback<RdbStore>): void
```

Obtains an RdbStore instance. You can set the **config** parameter as required and use **RdbStore** APIs to perform data operations. This API uses an asynchronous callback to return the result.

If no database file exists in the corresponding sandbox directory, a database file is created. For details, see [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md). If a database file exists in the corresponding directory, the existing database file is opened.

When creating a database, you should consider whether to configure the [encrypt](arkts-arkdata-relationalstore-storeconfig-i.md) parameter. Once the database is created, you are not allowed to change this parameter.

| Encryption Type When the RDB Store Is Opened | Encryption Type When the RDB Store Is Created | Result|  
| ------- | -------------------------------- | ---- |  
| Non-encryption| Encryption | The RDB store is opened in encrypted mode. |
| Encryption| Non-encryption | The RDB store is opened in non-encrypted mode. |

Currently, **getRdbStore()** does not support multi-thread concurrent operations.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| config | [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) | Yes | Configuration of the RDB store. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md)&gt; | Yes | Callback invoked to return the RDB store obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-invalid-database-path) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14801001](../errorcode-data-rdb.md#14801001-stage-model-required) | The operation is supported in the stage model only.<br>**Applicable version:** 10 and later |
| [14801002](../errorcode-data-rdb.md#14801002-invalid-datagroupid-in-storeconfig) | Invalid data group ID.<br>**Applicable version:** 10 and later |
| [14800017](../errorcode-data-rdb.md#14800017-key-configuration-changed) | StoreConfig is changed.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800020](../errorcode-data-rdb.md#14800020-key-damaged-or-lost) | The secret key is corrupted or lost.<br>**Applicable version:** 14 and later |

**Examples**

```TypeScript
FA model:
```

```TypeScript
Stage model:
```


## getRdbStore

```TypeScript
function getRdbStore(context: Context, config: StoreConfig): Promise<RdbStore>
```

Obtains an RdbStore instance. You can set the **config** parameter as required and use **RdbStore** APIs to perform data operations. This API uses a promise to return the result.

If no database file exists in the corresponding sandbox directory, a database file is created. For details, see [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md). If a database file exists in the corresponding directory, the existing database file is opened.

When creating a database, you should consider whether to configure the [encrypt](arkts-arkdata-relationalstore-storeconfig-i.md) parameter. Once the database is created, you are not allowed to change this parameter.

| Encryption Type When the RDB Store Is Opened | Encryption Type When the RDB Store Is Created | Result|  
| ------- | -------------------------------- | ---- |  
| Non-encryption| Encryption | The RDB store is opened in encrypted mode. |
| Encryption| Non-encryption | The RDB store is opened in non-encrypted mode. |

Currently, **getRdbStore()** does not support multi-thread concurrent operations.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| context | Context | Yes | Application context.<br>For details about the application context of the FA model, see Context.<br>For details about the application context of the stage model, see [Context](../../apis-ability-kit/arkts-apis/arkts-ability-context-c.md). |
| config | [StoreConfig](arkts-arkdata-relationalstore-storeconfig-i.md) | Yes | Configuration of the RDB store. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RdbStore](arkts-arkdata-relationalstore-rdbstore-i.md)&gt; | Promise used to return the **RdbStore** object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified;<br>2. Incorrect parameter types; 3. Parameter verification failed. |
| [14800000](../errorcode-data-rdb.md#14800000-internal-error) | Inner error. |
| [14800010](../errorcode-data-rdb.md#14800010-invalid-database-path) | Failed to open or delete the database by an invalid database path. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14801001](../errorcode-data-rdb.md#14801001-stage-model-required) | The operation is supported in the stage model only.<br>**Applicable version:** 10 and later |
| [14801002](../errorcode-data-rdb.md#14801002-invalid-datagroupid-in-storeconfig) | Invalid data group ID.<br>**Applicable version:** 10 and later |
| [14800017](../errorcode-data-rdb.md#14800017-key-configuration-changed) | StoreConfig is changed.<br>**Applicable version:** 12 and later |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error.<br>**Applicable version:** 12 and later |
| [14800027](../errorcode-data-rdb.md#14800027-sqlite-attempt-to-write-a-read-only-database) | SQLite: Attempt to write a readonly database.<br>**Applicable version:** 12 and later |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred.<br>**Applicable version:** 12 and later |
| [14800029](../errorcode-data-rdb.md#14800029-sqlite-database-is-full) | SQLite: The database is full.<br>**Applicable version:** 12 and later |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file.<br>**Applicable version:** 12 and later |
| [14800020](../errorcode-data-rdb.md#14800020-key-damaged-or-lost) | The secret key is corrupted or lost.<br>**Applicable version:** 14 and later |
| [14800022](../errorcode-data-rdb.md#14800022-sqlite-asynchronous-callback-request-aborted) | SQLite: Callback routine requested an abort.<br>**Applicable version:** 12 and later |
| [14800023](../errorcode-data-rdb.md#14800023-sqlite-access-denied) | SQLite: Access permission denied.<br>**Applicable version:** 12 and later |

**Examples**

See [getRdbStore](#getrdbstore)
