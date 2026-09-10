# Interface (Transaction)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=99f27ed5372b3353f2b572028e1a2823f9d04616 translatedAt=2026-09-04T02:44:41.909Z pushedAt=2026-09-09T09:11:03.651Z -->

Provides APIs for managing databases in transaction mode. A transaction object is created by using [createTransaction](arkts-apis-data-relationalStore-RdbStore.md#createtransaction14). Operations on different transaction objects are isolated. For details about the transaction types, see [TransactionType](arkts-apis-data-relationalStore-e.md#transactiontype14).

Currently, an RDB store supports only one write transaction at a time. If the current [RdbStore](arkts-apis-data-relationalStore-RdbStore.md) has a write transaction that is not released, creating an **IMMEDIATE** or **EXCLUSIVE** transaction object will return error 14800024. If a **DEFERRED** transaction object is created, error 14800024 may be returned when it is used to invoke a write operation for the first time. After a write transaction is created using **IMMEDIATE** or **EXCLUSIVE**, or a **DEFERRED** transaction is upgraded to a write transaction, write operations in the [RdbStore](arkts-apis-data-relationalStore-RdbStore.md) will also return error 14800024.

When the number of concurrent transactions is large and the write transaction duration is long, the frequency of returning error 14800024 may increase. You can reduce the occurrence of error 14800024 by shortening the transaction duration or by handling the error 14800024 through retries.

Before using the following APIs, you should obtain a **Transaction** instance by calling the [createTransaction](./arkts-apis-data-relationalStore-RdbStore.md#createtransaction14) method and then call the corresponding method through the instance.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The initial APIs of this module are supported since API version 14.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Example**:

For details about the definition of **this.context** in the sample code, see the application [context](../apis-ability-kit/js-apis-inner-application-context.md) of the stage model.

```ts
import { UIAbility } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { window } from '@kit.ArkUI';

let store: relationalStore.RdbStore | undefined = undefined;

export default class EntryAbility extends UIAbility {
  async onWindowStageCreate(windowStage: window.WindowStage) {
    const STORE_CONFIG: relationalStore.StoreConfig = {
      name: 'RdbTest.db',
      securityLevel: relationalStore.SecurityLevel.S3
    };

    try {
      const rdbStore = await relationalStore.getRdbStore(this.context, STORE_CONFIG);
      store = rdbStore;
      console.info('Get RdbStore successfully.');
    } catch (error) {
      const err = error as BusinessError;
      console.error(`Get RdbStore failed, code is ${err.code},message is ${err.message}`);
    }

    if (store != undefined) {
      await store.executeSql('CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB, IDENTITY UNLIMITED INT, ASSETDATA ASSET, ASSETSDATA ASSETS, FLOATARRAY floatvector(128))');
      store.createTransaction().then(async (transaction: relationalStore.Transaction) => {
        console.info(`createTransaction success`);
        // Perform subsequent operations after the transaction instance is successfully obtained.
      }).catch((err: BusinessError) => {
        console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
      });
    }
  }
}
```

## Module to Import

```ts
import { relationalStore } from '@kit.ArkData';
```

## commit<sup>14+</sup>

commit(): Promise&lt;void&gt;

Commits the executed SQL statements. This API uses a promise to return the result. If the SQL statements are executed using an asynchronous API, ensure that the asynchronous API has finished execution before calling **commit**; otherwise, the SQL operations may be lost. After **commit** is called, the **Transaction** object and the created **ResultSet** objects will be closed.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |

**Example**:

```ts
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      await transaction.execute('CREATE TABLE IF NOT EXISTS test (id INTEGER PRIMARY KEY AUTOINCREMENT, name TEXT NOT NULL, age INTEGER, salary REAL)');
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## rollback<sup>14+</sup>

rollback(): Promise&lt;void&gt;

Rolls back this executed SQL statement. This API uses a promise to return the result. After **rollback()** is called, the transaction object and the created **ResultSet** object will be closed.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |

**Example**:

```ts
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      await transaction.execute('DELETE FROM TEST WHERE age = ? OR age = ?', ['18', '20']);
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`execute sql failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## insert<sup>14+</sup>

insert(table: string, values: ValuesBucket, conflict?: ConflictResolution): Promise&lt;number&gt;

Inserts a row of data into the target table. This API uses a promise to return the result.

Due to the limit of the shared memory, the size of a single data record must be strictly less than 2 MB.

If a single data record exceeds this limit, after a **ResultSet** is obtained through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling the get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, you are advised to use the blob type.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name  | Type                                       | Mandatory| Description                      |
| -------- | ------------------------------------------- | ---- | -------------------------- |
| table    | string                                      | Yes   | Target table name. It cannot be an empty string, and it must not contain spaces, commas, or asterisks, and cannot start or end with a dot. Otherwise, error code 401 is thrown.           |
| values   | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)               | Yes  | Row of data to insert.|
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| No  | Resolution used to resolve the conflict. <br>Default value: **relationalStore.ConflictResolution.ON_CONFLICT_NONE**.        |

**Return value**

| Type                 | Description                                             |
| --------------------- | ------------------------------------------------- |
| Promise&lt;number&gt; | Promise object that returns the row ID of the inserted data. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
const valueBucket1: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const rowId = await transaction.insert('EMPLOYEE', valueBucket1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      await transaction.commit();
      console.info(`Insert is successful, rowId = ${rowId}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Insert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## insertSync<sup>14+</sup>

insertSync(table: string, values: ValuesBucket | sendableRelationalStore.ValuesBucket, conflict?: ConflictResolution): number

Inserts a row of data into the target table.

Due to the limit of the shared memory, the size of a single data record must be strictly less than 2 MB.

If a single data record exceeds this limit, after a **ResultSet** is obtained through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling the get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. If you need to store content larger than 8 MB, use the blob type.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name  | Type                                       | Mandatory| Description                                                        |
| -------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| table    | string                                      | Yes   | Name of the target table. It cannot be an empty string.                                             |
| values   | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket) \| [sendableRelationalStore.ValuesBucket](./js-apis-data-sendableRelationalStore.md#valuesbucket)   | Yes  | Row of data to insert.                                  |
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| No  | Resolution used to resolve the conflict. <br>Default value: **relationalStore.ConflictResolution.ON_CONFLICT_NONE**.|

**Return value**

| Type  | Description                                |
| ------ | ------------------------------------ |
| number | Row ID of the inserted data. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000     | Inner error.                                                 |
| 14800011     | The current operation failed because the database is corrupted.                                          |
| 14800014     | The target instance is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**:

```ts
let value5 = 'Lisa';
let value6 = 18;
let value7 = 100.5;
let value8 = new Uint8Array([1, 2, 3, 4, 5]);

const valueBucket2: relationalStore.ValuesBucket = {
  NAME: value5,
  AGE: value6,
  SALARY: value7,
  CODES: value8
};
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rowId: number = transaction.insertSync(
        'EMPLOYEE',
        valueBucket2,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`Insert is successful, rowId = ${rowId}`);
    } catch (e) {
      await transaction.rollback();
      console.error(`Insert is failed, code is ${e.code},message is ${e.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsert<sup>14+</sup>

batchInsert(table: string, values: Array&lt;ValuesBucket&gt;): Promise&lt;number&gt;

Inserts data into a table in batches. This API uses a promise to return the result.

Because the size limit of shared memory is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, when you later obtain a **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. If you need to store content larger than 8 MB, use the blob type.

Data is written in batches of 32766 parameters at a time using the [ConflictResolution.ON_CONFLICT_REPLACE](arkts-apis-data-relationalStore-e.md#conflictresolution10) policy. The number of parameters is calculated as the number of inserted data records multiplied by the size of the union of all fields of the inserted data. If a failure occurs midway, the API returns immediately.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | Yes   | Name of the target table. It cannot be an empty string.             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | Yes  | An array of data to insert.|

**Return value**

| Type                 | Description                                                       |
| --------------------- | ----------------------------------------------------------- |
| Promise&lt;number&gt; | Promise object used to return the number of data records inserted in batch. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
const valueBucket3: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucket4: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucket5: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets = new Array(valueBucket3, valueBucket4, valueBucket5);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = await transaction.batchInsert('EMPLOYEE', valueBuckets);
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertSync<sup>14+</sup>

batchInsertSync(table: string, values: Array&lt;ValuesBucket&gt;): number

Inserts data into a table in batches. This API returns the result synchronously.

Because the size limit of shared memory is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, when you later obtain a **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. If you need to store content larger than 8 MB, use the blob type.

Writes data in batches of 32766 parameters using the [ConflictResolution.ON_CONFLICT_REPLACE](arkts-apis-data-relationalStore-e.md#conflictresolution10) policy. The number of parameters is calculated as the number of data records to insert multiplied by the size of the union of all fields in the inserted data. If a failure occurs midway, the operation returns immediately.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | Yes   | Name of the target table. It cannot be an empty string.             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | Yes  | An array of data to insert.|

**Return value**

| Type  | Description                                          |
| ------ | ---------------------------------------------- |
| number | Number of data records inserted in batch. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000     | Inner error.                                                 |
| 14800011     | The current operation failed because the database is corrupted.                                          |
| 14800014     | The target instance is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**:

```ts
const valueBucket6: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucket7: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucket8: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets2 = new Array(valueBucket6, valueBucket7, valueBucket8);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let insertNum: number = (transaction as relationalStore.Transaction).batchInsertSync('EMPLOYEE', valueBuckets2);
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithConflictResolution<sup>18+</sup>

batchInsertWithConflictResolution(table: string, values: Array&lt;ValuesBucket&gt;, conflict: ConflictResolution): Promise&lt;number&gt;

Inserts data into a table with conflict resolutions in batches. You can use the **conflict** parameter to specify [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10). This API uses a promise to return the result.

Because the shared memory size limit is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, after obtaining a **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, use the blob type.

A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code 14800000 is returned. The number of inserted data records multiplied by the size of the union across all fields in the inserted data equals the number of parameters.

For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760).

Ensure that you comply with this constraint when calling this API to avoid errors caused by excessive parameters.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | Yes   | Name of the target table. It cannot be an empty string.             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | Yes  | An array of data to insert.|
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| Yes  | Resolution used to resolve the conflict. If **ON_CONFLICT_ROLLBACK** is used, the transaction will be rolled back when a conflict occurs.|

**Return value**

| Type                 | Description                                                       |
| --------------------- | ----------------------------------------------------------- |
| Promise&lt;number&gt; | Promise object used to return the number of data records inserted in batch. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
const valueBucket9: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucketA: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucketB: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets3 = new Array(valueBucket9, valueBucketA, valueBucketB);

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = await transaction.batchInsertWithConflictResolution(
        'EMPLOYEE',
        valueBuckets3,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithConflictResolutionSync<sup>18+</sup>

batchInsertWithConflictResolutionSync(table: string, values: Array&lt;ValuesBucket&gt;, conflict: ConflictResolution): number

Inserts data into a table with conflict resolutions in batches. You can use the **conflict** parameter to specify [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10).

Because the shared memory size limit is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, after obtaining a **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, use the blob type.

A maximum of 32766 parameters can be inserted at a time. If the number of parameters exceeds the upper limit, the error code 14800000 is returned. The number of inserted data records multiplied by the size of the union across all fields in the inserted data equals the number of parameters.

For example, if the size of the union is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760).

Ensure that you comply with this constraint when calling this API to avoid errors caused by excessive parameters.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name| Type                                      | Mandatory| Description                        |
| ------ | ------------------------------------------ | ---- | ---------------------------- |
| table  | string                                     | Yes   | Name of the target table. It cannot be an empty string.             |
| values | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | Yes  | An array of data to insert.|
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| Yes  | Resolution used to resolve the conflict. If **ON_CONFLICT_ROLLBACK** is used, the transaction will be rolled back when a conflict occurs.|

**Return value**

| Type  | Description                                          |
| ------ | ---------------------------------------------- |
| number | Number of data records inserted in batch. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
const valueBucketC: relationalStore.ValuesBucket = {
  NAME: 'Lisa',
  AGE: 18,
  SALARY: 100.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
const valueBucketD: relationalStore.ValuesBucket = {
  NAME: 'Jack',
  AGE: 19,
  SALARY: 101.5,
  CODES: new Uint8Array([6, 7, 8, 9, 10])
};
const valueBucketE: relationalStore.ValuesBucket = {
  NAME: 'Tom',
  AGE: 20,
  SALARY: 102.5,
  CODES: new Uint8Array([11, 12, 13, 14, 15])
};

let valueBuckets4 = new Array(valueBucketC, valueBucketD, valueBucketE);
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const insertNum = transaction.batchInsertWithConflictResolutionSync(
        'EMPLOYEE',
        valueBuckets4,
        relationalStore.ConflictResolution.ON_CONFLICT_REPLACE
      );
      await transaction.commit();
      console.info(`batchInsert is successful, the number of values that were inserted = ${insertNum}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`batchInsert is failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## batchInsertWithReturning<sup>23+</sup>

batchInsertWithReturning(table: string, values: Array\<ValuesBucket\>, config: ReturningConfig, conflict?: ConflictResolution): Promise\<Result\>

Inserts a batch of data into the target table. You can use the **conflict** parameter to specify the conflict resolution mode [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) when a data conflict occurs, and the API returns [Result](arkts-apis-data-relationalStore-i.md#result23). This API uses a promise to return the result.

Because the shared memory size limit is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, after you obtain the **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of **RdbStore**, calling the get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing up to 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, use the blob type.

The maximum number of parameters for a single insert is 32766. If the limit is exceeded, error code 14800001 is returned. The number of parameters is calculated as the number of inserted data records multiplied by the size of the union of all fields of the inserted data.

For example, if the size of the union of all fields of the inserted data is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760).

Ensure that you comply with this limit when calling the API to avoid errors caused by too many parameters.

It is not recommended to use the **ON_CONFLICT_FAIL** policy for the **conflict** parameter, because the correct result may not be returned.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| table    | string                                                       | Yes  | Name of the target table to insert data into. Note: A valid table name must not contain spaces, commas, or asterisks, and must not start or end with a dot. Otherwise, a parameter error is thrown. |
| values   | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | Yes  | Set of data to insert into the table. Note: An empty array or an array containing duplicate asset data throws a parameter error. |
| config   | [ReturningConfig](arkts-apis-data-relationalStore-i.md#returningconfig23) | Yes  | Configuration of the return value.                                       |
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) | No   | Conflict resolution mode. The default value is **ON_CONFLICT_NONE**.                     |

**Return value**

| Type                                                         | Description                                            |
| ------------------------------------------------------------ | ----------------------------------------------- |
| Promise\<[Result](arkts-apis-data-relationalStore-i.md#result23)> | Promise object used to return the affected data set. |

**Error codes:**

For details about the error codes, see [RDB Store Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 14800001     | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800011     | The current operation failed because the database is corrupted.         |
| 14800014     | The target instance is already closed.                 |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800032     | SQLite: Abort due to constraint violation.                   |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**

```ts
async function transBatchInsertWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = await trans.batchInsertWithReturning("EMPLOYEE", valueBuckets, config);
    console.info(`transBatchInsertWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transBatchInsertWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transBatchInsertWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## batchInsertWithReturningSync<sup>23+</sup>

batchInsertWithReturningSync(table: string, values: Array\<ValuesBucket\>, config: ReturningConfig, conflict?: ConflictResolution): Result

Inserts a group of data records into the target table. You can use the **conflict** parameter to specify the conflict resolution mode [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) when a data conflict occurs, and the API returns [Result](arkts-apis-data-relationalStore-i.md#result23).

Because the shared memory size limit is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, after you obtain the **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling the get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, use the blob type.

The maximum number of parameters for a single insert is 32766. If the limit is exceeded, error code 14800001 is returned. The number of parameters is calculated as the number of inserted data records multiplied by the size of the union of all fields of the inserted data.

For example, if the size of the union of all fields of the inserted data is 10, a maximum of 3276 data records can be inserted (3276 × 10 = 32760).

Ensure that you comply with this limit when calling the API to avoid errors caused by too many parameters.

For the **conflict** parameter, the **ON_CONFLICT_FAIL policy** is not recommended, because the correct result may not be returned.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name     | Type                                                         | Mandatory | Description                                                         |
| -------- | ------------------------------------------------------------ | --------- | ------------------------------------------------------------ |
| table    | string                                                       | Yes       | Target table to insert data into. Note: A valid table name must not contain spaces, commas, or asterisks, and must not start or end with a dot. Otherwise, a parameter error is thrown. |
| values   | Array&lt;[ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)&gt; | Yes       | Set of data to insert into the table. Note: An empty array or an array containing duplicate asset data throws a parameter error. |
| config   | [ReturningConfig](arkts-apis-data-relationalStore-i.md#returningconfig23) | Yes       | Configuration of the return value.                                       |
| conflict | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) | No        | Conflict resolution mode. The default value is **ON_CONFLICT_NONE**.                   |

**Return value**

| Type                                                    | Description                               |
| ------------------------------------------------------- | ---------------------------------- |
| [Result](arkts-apis-data-relationalStore-i.md#result23) | Affected data set. |

**Error codes:**

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 14800001     | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800011     | The current operation failed because the database is corrupted.         |
| 14800014     | The target instance is already closed.                 |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800032     | SQLite: Abort due to constraint violation.                   |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**

```ts
function transBatchInsertWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 20 };
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  const valueBuckets = new Array(valueBucket1, valueBucket2);
  try {
    let results = trans.batchInsertWithReturningSync("EMPLOYEE", valueBuckets, config);
    console.info(`transBatchInsertWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transBatchInsertWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transBatchInsertWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## update<sup>14+</sup>

update(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): Promise&lt;number&gt;

Updates data in the database based on the specified **RdbPredicates** instance. This API uses a promise to return the result asynchronously.

Because the shared memory size is limited to 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, after the **ResultSet** is obtained through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling the get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, use the blob type.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name    | Type                                       | Mandatory| Description                                                        |
| ---------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)               | Yes  | Rows of data to update in the RDB store. The key-value pair is associated with the column name in the target table.|
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md)            | Yes  | Update conditions specified by the **RdbPredicates** object.                     |
| conflict   | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| No  | Resolution used to resolve the conflict. <br>Default value: **relationalStore.ConflictResolution.ON_CONFLICT_NONE**.                                         |

**Return value**

| Type                 | Description                                     |
| --------------------- | ----------------------------------------- |
| Promise&lt;number&gt; | Promise object used to return the number of affected rows. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
const valueBucketF: relationalStore.ValuesBucket = {
  NAME: 'Rose',
  AGE: 22,
  SALARY: 200.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
let predicates = new relationalStore.RdbPredicates('EMPLOYEE');
predicates.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const rows = await transaction.update(valueBucketF, predicates, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      await transaction.commit();
      console.info(`Updated row count: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## updateSync<sup>14+</sup>

updateSync(values: ValuesBucket, predicates: RdbPredicates, conflict?: ConflictResolution): number

Updates data in the database based on the specified **RdbPredicates** instance.

Because the shared memory size limit is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, when you later obtain a **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, use the blob type.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name    | Type                                       | Mandatory| Description                                                        |
| ---------- | ------------------------------------------- | ---- | ------------------------------------------------------------ |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)               | Yes  | Rows of data to update in the RDB store. The key-value pair is associated with the column name in the target table.|
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md)             | Yes  | Update conditions specified by the **RdbPredicates** object.                     |
| conflict   | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10)| No  | Resolution used to resolve the conflict. <br>Default value: **relationalStore.ConflictResolution.ON_CONFLICT_NONE**.|

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| number | Number of rows updated.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000     | Inner error.                                                 |
| 14800011     | The current operation failed because the database is corrupted.                                          |
| 14800014     | The target instance is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**:

```ts
const valueBucketG: relationalStore.ValuesBucket = {
  NAME: 'Rose',
  AGE: 22,
  SALARY: 200.5,
  CODES: new Uint8Array([1, 2, 3, 4, 5])
};
let predicates1 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates1.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rows = transaction.updateSync(valueBucketG, predicates1, relationalStore.ConflictResolution.ON_CONFLICT_REPLACE);
      await transaction.commit();
      console.info(`Updated row count: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Updated failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## updateWithReturning<sup>23+</sup>

updateWithReturning(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig, conflict?: ConflictResolution): Promise\<Result\>

Updates data in the database based on the specified **RdbPredicates** instance. You can use the **conflict** parameter to specify the conflict resolution mode [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) when a data conflict occurs. This API returns a [Result](arkts-apis-data-relationalStore-i.md#result23) and uses a promise to return the result asynchronously.

Because the size limit of the shared memory is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, after a **ResultSet** is obtained through [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) of RdbStore, calling get methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep).

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, you are advised to use the blob type.

You are advised not to use the **ON_CONFLICT_FAIL** policy for the **conflict** parameter, because the correct result may not be returned.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                         | Mandatory | Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket) | Yes  | Data row to update in the database. The key-value pairs are associated with the column names of the database table. |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Update conditions specified by the **RdbPredicates** instance.   |
| config     | [ReturningConfig](arkts-apis-data-relationalStore-i.md#returningconfig23) | Yes  | Configuration information of the return value.               |
| conflict   | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) | No   | Conflict resolution mode. The default value is **ON_CONFLICT_NONE**. |

**Return value**

| Type                                                    | Description                                            |
| ------------------------------------------------------- | ----------------------------------------------- |
| Promise\<[Result](arkts-apis-data-relationalStore-i.md#result23)\> | Promise object used to return the affected data set. |

**Error Codes**

For details about the error codes, see [RDB Store Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 14800001     | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800011     | The current operation failed because the database is corrupted.         |
| 14800014     | The target instance is already closed.                 |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800032     | SQLite: Abort due to constraint violation.                   |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**

```ts
async function transUpdateWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = await trans.updateWithReturning(valueBucket1, predicates, config);
    console.info(`transUpdateWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transUpdateWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transUpdateWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## updateWithReturningSync<sup>23+</sup>

updateWithReturningSync(values: ValuesBucket, predicates: RdbPredicates, config: ReturningConfig, conflict?: ConflictResolution): Result

Updates data in the database based on the specified **RdbPredicates** instance. You can use the **conflict** parameter to specify the conflict resolution mode [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) when a data conflict occurs, and this API returns [Result](arkts-apis-data-relationalStore-i.md#result23).

Because the shared memory size limit is 2 MB, the size of a single data record must also be strictly less than 2 MB.

If a single data record exceeds this limit, after you obtain the **ResultSet** through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of RdbStore, calling the **get** methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) will fail to obtain the data, and may cause the operation to fail or throw an exception.

To read data larger than 2 MB, use the [queryByStep](arkts-apis-data-relationalStore-RdbStore.md#querybystep) API.

A single string type field supports writing a maximum of 8 MB. The excess part will be truncated, and only the first 8 MB of data is retained. To store content larger than 8 MB, use the blob type.

It is not recommended to use the **ON_CONFLICT_FAIL** policy for the **conflict** parameter, as it may fail to return the correct result.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                         | Mandatory | Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket) | Yes  | Data rows to update in the database. The key-value pairs are associated with the column names of the database table. |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Update conditions specified by the **RdbPredicates** instance.                      |
| config     | [ReturningConfig](arkts-apis-data-relationalStore-i.md#returningconfig23) | Yes  | Configuration information of the return value.                                       |
| conflict   | [ConflictResolution](arkts-apis-data-relationalStore-e.md#conflictresolution10) | No   | Conflict resolution mode. The default value is **ON_CONFLICT_NONE**.                   |

**Return value**

| Type                                                    | Description                               |
| ------------------------------------------------------- | ---------------------------------- |
| [Result](arkts-apis-data-relationalStore-i.md#result23) | Data set affected. |

**Error Codes**

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 14800001     | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800011     | The current operation failed because the database is corrupted.         |
| 14800014     | The target instance is already closed.                 |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800032     | SQLite: Abort due to constraint violation.                   |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**

```ts
function transUpdateWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo('NAME', 'lisi');
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    valueBucket1['NAME'] = "zhangsan";
    valueBucket1['AGE'] = 18;
    let results = trans.updateWithReturningSync(valueBucket1, predicates, config);
    console.info(`transUpdateWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transUpdateWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transUpdateWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## delete<sup>14+</sup>

delete(predicates: RdbPredicates):Promise&lt;number&gt;

Deletes data from the RDB store based on the specified **RdbPredicates** object. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name    | Type                                | Mandatory| Description                                     |
| ---------- | ------------------------------------ | ---- | ----------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Deletion conditions specified by the **RdbPredicates** object.|

**Return value**

| Type                 | Description                           |
| --------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of rows deleted.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
let predicates2 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates2.equalTo('NAME', 'Lisa');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const rows = await transaction.delete(predicates2);
      await transaction.commit();
      console.info(`Delete rows: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## deleteSync<sup>14+</sup>

deleteSync(predicates: RdbPredicates): number

Deletes data from the RDB store based on the specified **RdbPredicates** object. This API returns the result synchronously.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name    | Type                           | Mandatory| Description                                   |
| ---------- | ------------------------------- | ---- | --------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Deletion conditions specified by the **RdbPredicates** object.|

**Return value**

| Type  | Description              |
| ------ | ------------------ |
| number | Number of rows deleted.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
let predicates3 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates3.equalTo('NAME', 'Lisa');
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let rows = transaction.deleteSync(predicates3);
      await transaction.commit();
      console.info(`Delete rows: ${rows}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Delete failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## deleteWithReturning<sup>23+</sup>

deleteWithReturning(predicates: RdbPredicates, config: ReturningConfig): Promise\<Result\>

Deletes data from the database based on the **RdbPredicates** instance and returns the [Result](arkts-apis-data-relationalStore-i.md#result23). This API uses a promise to return the result asynchronously.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                         | Mandatory | Description                                    |
| ---------- | ------------------------------------------------------------ | --------- | ---------------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes       | Deletion conditions specified by the **RdbPredicates** instance. |
| config     | [ReturningConfig](arkts-apis-data-relationalStore-i.md#returningconfig23) | Yes       | Configuration information of the return value. |

**Return value**

| Type                                                    | Description                                            |
| ------------------------------------------------------- | ------------------------------------------------------ |
| Promise\<[Result](arkts-apis-data-relationalStore-i.md#result23)\> | Promise object used to return the affected data set. |

**Error codes:**

For details about the following error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ----------------- | ------------------------------------------------------------ |
| 14800001          | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800011          | The current operation failed because the database is corrupted.         |
| 14800014          | The target instance is already closed.                 |
| 14800021          | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800024          | SQLite: The database file is locked.                         |
| 14800025          | SQLite: A table in the database is locked.                   |
| 14800028          | SQLite: Some kind of disk I/O error occurred.                |
| 14800029          | SQLite: The database is full.                                |
| 14800032          | SQLite: Abort due to constraint violation.                   |
| 14800033          | SQLite: Data type mismatch.                                  |
| 14800047          | The WAL file size exceeds the default limit.                 |

**Example**

```ts
async function transDeleteWithReturningExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = await trans.deleteWithReturning(predicates, config);
    console.info(`transDeleteWithReturningExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transDeleteWithReturningExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transDeleteWithReturningExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## deleteWithReturningSync<sup>23+</sup>

deleteWithReturningSync(predicates: RdbPredicates, config: ReturningConfig): Result

Deletes data from the database based on the **RdbPredicates** instance and returns the [Result](arkts-apis-data-relationalStore-i.md#result23).

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                         | Mandatory | Description                                    |
| ---------- | ------------------------------------------------------------ | --------- | ---------------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes       | Deletion conditions specified by the **RdbPredicates** instance. |
| config     | [ReturningConfig](arkts-apis-data-relationalStore-i.md#returningconfig23) | Yes       | Configuration information of the return value. |

**Return value**

| Type                                                    | Description                               |
| ------------------------------------------------------- | ----------------------------------------- |
| [Result](arkts-apis-data-relationalStore-i.md#result23) | Data set affected by the operation. |

**Error codes:**

For details about the following error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                             |
| ----------------- | ------------------------------------------------------------ |
| 14800001          | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800011          | The current operation failed because the database is corrupted.         |
| 14800014          | The target instance is already closed.                 |
| 14800021          | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800024          | SQLite: The database file is locked.                         |
| 14800025          | SQLite: A table in the database is locked.                   |
| 14800028          | SQLite: Some kind of disk I/O error occurred.                |
| 14800029          | SQLite: The database is full.                                |
| 14800032          | SQLite: Abort due to constraint violation.                   |
| 14800033          | SQLite: Data type mismatch.                                  |
| 14800047          | The WAL file size exceeds the default limit.                 |

**Example**

```ts
function transDeleteWithReturningSyncExample(trans: relationalStore.Transaction)
{
  const valueBucket1: relationalStore.ValuesBucket = { 'NAME': 'lisi', 'AGE': 21 };
  const valueBucket2: relationalStore.ValuesBucket = { 'NAME': 'zhangsan', 'AGE': 18 };
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  const config: relationalStore.ReturningConfig = { columns: ['NAME', 'AGE'] };
  try {
    trans.batchInsertWithReturningSync("EMPLOYEE", [valueBucket1, valueBucket2], config);
    let results = trans.deleteWithReturningSync(predicates, config);
    console.info(`transDeleteWithReturningSyncExample is successful, changed is ${results.changed}`);
    while(results.resultSet.goToNextRow()) {
      const row = results.resultSet.getRow();
      console.info(`transDeleteWithReturningSyncExample, name is ${row['NAME']}, age is ${row['AGE']}`);
    }
  } catch (e) {
    console.error(`transDeleteWithReturningSyncExample failed. code is ${e.code}, message is ${e.message}`);
  }
}
```

## query<sup>14+</sup>

query(predicates: RdbPredicates, columns?: Array&lt;string&gt;): Promise&lt;ResultSet&gt;

Queries data from the RDB store based on specified conditions. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name    | Type                                | Mandatory| Description                                            |
| ---------- | ------------------------------------ | ---- | ------------------------------------------------ |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Query conditions specified by the **RdbPredicates** object.       |
| columns    | Array&lt;string&gt;                  | No  | Columns to query. If this parameter is not specified, the query applies to all columns.|

**Return value**

| Type                                                   | Description                                              |
| ------------------------------------------------------- | -------------------------------------------------- |
| Promise&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Promise object used to return the **ResultSet** object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |


**Example**:

```ts
let predicates4 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates4.equalTo('NAME', 'Rose');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const resultSet = await transaction.query(predicates4, ['ID', 'NAME', 'AGE', 'SALARY', 'CODES']);
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // Release the memory of the result set. Otherwise, fd leak and memory leak may occur.
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## querySync<sup>14+</sup>

querySync(predicates: RdbPredicates, columns?: Array&lt;string&gt;): ResultSet

Queries data in a database based on specified conditions. This API returns the result synchronously. If complex logic and a large number of loops are involved in the operations on the **resultSet** obtained by **querySync**, the freeze problem may occur. You are advised to perform this operation in the [taskpool](../apis-arkts/js-apis-taskpool.md) thread.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name    | Type                           | Mandatory| Description                                                        |
| ---------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Query conditions specified by the **RdbPredicates** object.                     |
| columns    | Array&lt;string&gt;             | No  | Columns to query. If this parameter is not specified, the query applies to all columns. The default value is null.|

**Return value**

| Type                   | Description                               |
| ----------------------- | ----------------------------------- |
| [ResultSet](arkts-apis-data-relationalStore-ResultSet.md) | **ResultSet** object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
let predicates5 = new relationalStore.RdbPredicates('EMPLOYEE');
predicates5.equalTo('NAME', 'Rose');

if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let resultSet = transaction.querySync(predicates5, ['ID', 'NAME', 'AGE', 'SALARY', 'CODES']);
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // Release the memory of the result set. Otherwise, fd leak and memory leak may occur.
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## querySql<sup>14+</sup>

querySql(sql: string, args?: Array&lt;ValueType&gt;): Promise&lt;ResultSet&gt;

Queries data in the RDB store using the specified SQL statement. The number of relational operators between expressions and operators in the SQL statement cannot exceed 1000. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name  | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql      | string                               | Yes   | SQL statement to execute. It cannot be an empty string.                                        |
| args | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | No   | Value of the parameter in the SQL statement. This value corresponds to the placeholder in the sql parameter statement. When the sql parameter statement is complete, this parameter is not required. The default value is empty. |

**Return value**

| Type                                                   | Description                                              |
| ------------------------------------------------------- | -------------------------------------------------- |
| Promise&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Promise object used to return the **ResultSet** object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const resultSet = await transaction.querySql("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'");
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // Release the memory of the result set. Failure to release it may cause fd leakage and memory leakage.
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## querySqlSync<sup>14+</sup>

querySqlSync(sql: string, args?: Array&lt;ValueType&gt;): ResultSet

Queries data in the RDB store using the specified SQL statement. The number of relational operators between expressions and operators in the SQL statement cannot exceed 1000. If complex logic and a large number of loops are involved in the operations on the **resultSet** obtained by **querySqlSync**, the freeze problem may occur. You are advised to perform this operation in the [taskpool](../apis-arkts/js-apis-taskpool.md) thread.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name  | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql      | string                               | Yes   | SQL statement to execute. It cannot be an empty string.                                        |
| args | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | No  | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, leave this parameter blank. The default value is null.|

**Return value**

| Type                   | Description                               |
| ----------------------- | ----------------------------------- |
| [ResultSet](arkts-apis-data-relationalStore-ResultSet.md) | **ResultSet** object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      let resultSet = transaction.querySqlSync("SELECT * FROM EMPLOYEE CROSS JOIN BOOK WHERE BOOK.NAME = 'sanguo'");
      console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
      // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
      while (resultSet.goToNextRow()) {
        const id = resultSet.getLong(resultSet.getColumnIndex('ID'));
        const name = resultSet.getString(resultSet.getColumnIndex('NAME'));
        const age = resultSet.getLong(resultSet.getColumnIndex('AGE'));
        const salary = resultSet.getDouble(resultSet.getColumnIndex('SALARY'));
        console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
      }
      // Release the memory of the result set. Otherwise, fd leak and memory leak may occur.
      resultSet.close();
      await transaction.commit();
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`Query failed, code is ${err.code},message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## queryWithoutRowCount<sup>23+</sup>

queryWithoutRowCount(predicates: RdbPredicates, columns?: Array&lt;string&gt;): Promise&lt;LiteResultSet&gt;

Queries data in the database based on specified conditions. This API does not calculate the row count, and its performance is better than that of [query](#query14). This API uses a promise to return the result asynchronously.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                            | Mandatory | Description                                                         |
| ---------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes   | Query conditions specified by the **RdbPredicates** instance.                      |
| columns    | Array&lt;string&gt;             | No   | Columns to query. If this parameter is left empty, the query applies to all columns. The default value is empty. |

**Return value**

| Type                    | Description                                |
| ----------------------- | ----------------------------------- |
| Promise&lt;[LiteResultSet](arkts-apis-data-relationalStore-LiteResultSet.md)&gt; | Returns the **LiteResultSet** object. |

**Error codes**

For details about the following error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 14800014     | The target instance is already closed.                 |

**Example**

```ts
async function queryWithoutRowCountExample(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = await transaction.queryWithoutRowCount(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
        if (resultSet != undefined) {
          // resultSet is a cursor of a data set. By default, it points to the -1st record, and valid data starts from 0.
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## queryWithoutRowCountSync<sup>23+</sup>

queryWithoutRowCountSync(predicates: RdbPredicates, columns?: Array&lt;string&gt;): LiteResultSet

Queries data in the database based on specified conditions without counting the number of rows. When operating on the **LiteResultSet** obtained by the synchronous API **queryWithoutRowCountSync**, if the logic is complex and the number of loops is too large, a freeze issue may occur. It is recommended that you execute this step in a [taskpool](../apis-arkts/js-apis-taskpool.md) thread.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                            | Mandatory | Description                                                         |
| ---------- | ------------------------------- | ---- | ------------------------------------------------------------ |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes   | Query conditions specified by the **RdbPredicates** instance.                      |
| columns    | Array&lt;string&gt;             | No   | Columns to query. If this parameter is left empty, the query applies to all columns. The default value is empty. |

**Return value**

| Type                    | Description                                |
| ----------------------- | ----------------------------------- |
| [LiteResultSet](arkts-apis-data-relationalStore-LiteResultSet.md) | **LiteResultSet** object. |

**Error codes:**

For details about the following error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 14800014     | The target instance is already closed.                 |

**Example**

```ts
async function queryWithoutRowCountSyncExample(store : relationalStore.RdbStore) {
  let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
  predicates.equalTo("NAME", "Rose");
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = transaction.queryWithoutRowCountSync(predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
        if (resultSet != undefined) {
          // resultSet is a cursor of a data set. By default, it points to the -1st record, and valid data starts from 0.
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## querySqlWithoutRowCount<sup>23+</sup>

querySqlWithoutRowCount(sql: string, bindArgs?: Array&lt;ValueType&gt;): Promise&lt;LiteResultSet&gt;

Queries data in the database based on the specified conditions without counting the number of rows. This API uses a promise to return the result. It delivers better performance than [querySql](#querysql14). The SQL statement can contain no more than 1000 relational operators between expressions and operators.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name     | Type                                 | Mandatory | Description                                                         |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql      | string                               | Yes  | SQL statement to execute. It cannot be an empty string.                                        |
| bindArgs | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | No   | Values of the parameters in the SQL statement. This parameter corresponds to the placeholders in the sql parameter. When the sql parameter is a complete statement, this parameter is not required. The default value is empty. |

**Return value**

| Type                                                    | Description                                               |
| ------------------------------------------------------- | -------------------------------------------------- |
| Promise&lt;[LiteResultSet](arkts-apis-data-relationalStore-LiteResultSet.md)&gt; | Promise object that returns a **LiteResultSet** object. |

**Error Codes**

For details about the following error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
|-----------| ------------------------------------------------------------ |
| 14800001  | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800014  | The target instance is already closed. |

**Example**

```ts
async function querySqlWithoutRowCountExample(store : relationalStore.RdbStore) {
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = await transaction.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
        if (resultSet != undefined) {
          // resultSet is a cursor of a data set. By default, it points to the -1st record, and valid data starts from 0.
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## querySqlWithoutRowCountSync<sup>23+</sup>

querySqlWithoutRowCountSync(sql: string, bindArgs?: Array&lt;ValueType&gt;):LiteResultSet

Queries data in the database based on the specified SQL statement without counting the number of rows. The number of relational operators between various expressions and operators in the SQL statement cannot exceed 1000. When operating the **LiteResultSet** obtained by the synchronous **querySqlWithoutRowCountSync** API, if the logic is complex and the number of loops is too large, a freeze issue may occur. It is recommended that you perform this step in a [taskpool](../apis-arkts/js-apis-taskpool.md) thread.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name     | Type                                 | Mandatory | Description                                                         |
| -------- | ------------------------------------ | --------- | ------------------------------------------------------------ |
| sql      | string                               | Yes       | SQL statement to execute. It cannot be an empty string.                                        |
| bindArgs | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | No        | Value of the parameter in the SQL statement. This value corresponds to the placeholder in the sql parameter. When the sql parameter statement is complete, this parameter is not required. The default value is empty. |

**Return value**

| Type                    | Description                                |
| ----------------------- | ----------------------------------- |
| [LiteResultSet](arkts-apis-data-relationalStore-LiteResultSet.md) | **LiteResultSet** object. |

**Error codes:**

For details about the following error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                 |
| ------------ | ------------------------------------------------------------ |
| 14800001     | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800014     | The target instance is already closed. |

**Example**

```ts
async function querySqlWithoutRowCountSyncExample(store : relationalStore.RdbStore) {
  if (store != undefined) {
    try {
      const transaction = await store.createTransaction();
      let resultSet: relationalStore.LiteResultSet | undefined;
      try {
        resultSet = transaction.querySqlWithoutRowCountSync('select * from EMPLOYEE where name = ?', ["Rose"]);
        if (resultSet != undefined) {
          // resultSet is a cursor of a data set. By default, it points to the -1st record, and valid data starts from 0.
          while (resultSet.goToNextRow()) {
            const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
            const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
            const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
            const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
            console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
          }
          // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
          resultSet.close();
        }
        await transaction.commit();
      } catch (err) {
        console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
        // Release the memory of the result set. Failure to release it may cause fd leak and memory leak.
        if (resultSet != undefined) {
          resultSet.close();
        }
        await transaction.rollback();
      }
    } catch (err) {
      console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
    }
  }
}
```

## execute<sup>14+</sup>

execute(sql: string, args?: Array&lt;ValueType&gt;): Promise&lt;ValueType&gt;

Executes an SQL statement that contains specified arguments. The number of relational operators between expressions and operators in the statement cannot exceed 1000. This API uses a promise to return a value of the ValueType type.

This API can be used to add, delete, and modify data, run SQL statements of the PRAGMA syntax, and create, delete, and modify a table. The type of the return value varies, depending on the execution result.

This API does not support query, database attachment, and transaction operations. You can use [querySql](#querysql14) or [query](#query14) to query data, and use [attach](arkts-apis-data-relationalStore-RdbStore.md#attach12) to attach a database.

Statements separated by semicolons (\;) are not supported.

Statements that start with a comment are not supported.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name  | Type                                | Mandatory| Description                                                        |
| -------- | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql      | string                               | Yes   | SQL statement to execute. It cannot be an empty string.                                        |
| args | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | No  | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If the SQL parameter statement is complete, leave this parameter blank.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | Promise used to return the SQL execution result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801       | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800033  | SQLite: Data type mismatch. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**:

```ts
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      // Delete all data from the table.
      const SQL_DELETE_TABLE = 'DELETE FROM EMPLOYEE';
      const data = await transaction.execute(SQL_DELETE_TABLE);
      await transaction.commit();
      console.info(`delete result: ${data}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```

## executeSync<sup>14+</sup>

executeSync(sql: string, args?: Array&lt;ValueType&gt;): ValueType

Executes an SQL statement that contains specified arguments. The number of relational operators between expressions and operators in the statement cannot exceed 1000. This API returns a value of the ValueType type.

This API can be used to add, delete, and modify data, run SQL statements of the PRAGMA syntax, and create, delete, and modify a table. The type of the return value varies, depending on the execution result.

This API does not support query, database attachment, and transaction operations. You can use [querySql](#querysql14) or [query](#query14) to query data, and use [attach](arkts-apis-data-relationalStore-RdbStore.md#attach12) to attach a database.

Statements separated by semicolons (\;) are not supported.

Statements that start with a comment are not supported.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name| Type                                | Mandatory| Description                                                        |
| ------ | ------------------------------------ | ---- | ------------------------------------------------------------ |
| sql    | string                               | Yes   | SQL statement to execute. It cannot be an empty string.                                        |
| args   | Array&lt;[ValueType](arkts-apis-data-relationalStore-t.md#valuetype)&gt; | No  | Arguments in the SQL statement. The value corresponds to the placeholders in the SQL parameter statement. If this parameter is left blank or set to **null** or **undefined**, the SQL statement is complete. The default value is null.|

**Return value**

| Type                   | Description               |
| ----------------------- | ------------------- |
| [ValueType](arkts-apis-data-relationalStore-t.md#valuetype) | SQL execution result.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md). For details about how to handle error 14800011, see [Database Backup and Restore](../../database/data-backup-and-restore.md).

| **ID**| **Error Message**                                                |
| ------------ | ------------------------------------------------------------ |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801       | Capability not supported the sql(attach,begin,commit,rollback etc.). |
| 14800000     | Inner error.                                                 |
| 14800011     | The current operation failed because the database is corrupted.                                          |
| 14800014     | The target instance is already closed.                                              |
| 14800021     | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist.                                       |
| 14800023     | SQLite: Access permission denied.                            |
| 14800024     | SQLite: The database file is locked.                         |
| 14800025     | SQLite: A table in the database is locked.                   |
| 14800026     | SQLite: The database is out of memory.                       |
| 14800027     | SQLite: Attempt to write a readonly database.                |
| 14800028     | SQLite: Some kind of disk I/O error occurred.                |
| 14800029     | SQLite: The database is full.                                |
| 14800031     | SQLite: TEXT or BLOB exceeds size limit.                     |
| 14800033     | SQLite: Data type mismatch.                                  |
| 14800047     | The WAL file size exceeds the default limit.                 |

**Example**:

```ts
// Delete all data from the table.
if (store != undefined) {
  try {
    const transaction = await store.createTransaction();
    try {
      const SQL_DELETE_TABLE = 'DELETE FROM EMPLOYEE';
      let data = transaction.executeSync(SQL_DELETE_TABLE);
      await transaction.commit();
      console.info(`delete result: ${data}`);
    } catch (error) {
      const err = error as BusinessError;
      await transaction.rollback();
      console.error(`delete failed, code is ${err.code}, message is ${err.message}`);
    }
  } catch (error) {
    const err = error as BusinessError;
    console.error(`createTransaction failed, code is ${err.code},message is ${err.message}`);
  }
}
```