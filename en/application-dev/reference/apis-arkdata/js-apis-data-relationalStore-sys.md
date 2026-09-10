# @ohos.data.relationalStore (RDB Store) (System API)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=68d7b8030be7ba5da7e711fc0d0ad9a1a6eb2337 translatedAt=2026-09-04T03:40:56.110Z pushedAt=2026-09-09T09:11:03.723Z -->

A relational database (RDB) is a database that manages data based on the relational model. Based on the SQLite component, the relational database provides a complete mechanism for managing local databases and a series of APIs for adding, deleting, modifying, and querying data. It can also directly execute SQL statements entered by users to meet complex scenario requirements. Worker threads are not supported.

The basic data types supported on the ArkTS side are number, string, binary data, and boolean. To ensure successful data insertion and reading, the size of a single data record must be strictly less than 2 MB. If this size limit is exceeded, the insertion operation still succeeds, but subsequent reading will fail.

The **relationalStore** module provides the following functions:

- [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md): provides predicates indicating the nature, feature, or relationship of a data entity in an RDB store. It is used to define the operation conditions for an RDB store.
- [RdbStore](arkts-apis-data-relationalStore-RdbStore.md): provides APIs for managing data in an RDB store.
- [ResultSet](arkts-apis-data-relationalStore-ResultSet.md): provides APIs for accessing the result set obtained from the RDB store.
- [LiteResultSet](arkts-apis-data-relationalStore-LiteResultSet.md): provides the result set returned after a user calls the relational database query API.

> **NOTE**
> 
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.data.relationalStore](arkts-apis-data-relationalStore.md).

## Modules to Import

```ts
import { relationalStore } from '@kit.ArkData';
```

## StoreConfig

Defines the configuration of an RDB store.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| isSearchable<sup>11+</sup> | boolean | No| Yes| Whether the RDB store is searchable. The value **true** means the RDB store is searchable; the value **false** means the opposite. The default value is **false**.<br>**System API**: This is a system API.<br>This parameter is supported since API version 11.|
| haMode<sup>12+</sup> | [HAMode](#hamode12) | No| Yes| High availability (HA) mode.<br>The value **SINGLE** means data can be written only to a single RDB store. The value **MAIN_REPLICA** means data can be written to the main and replica RDB stores to ensure HA. However, this mode is not supported in encryption and attach scenarios. The default value is **SINGLE**. The value **MAIN_REPLICA** may affect the database write performance.<br>**System API**: This is a system API.<br>This parameter is supported since API version 12.|
| autoCleanDeviceDirtyData | boolean | No | Yes | Whether the local device automatically cleans up the data synchronized from the remote device after the remote device deletes it. The value **true** indicates automatic cleanup, and **false** indicates manual cleanup. The default value is **true**. If this parameter is set to **false**, you need to actively call [cleanDeviceDirtyData](#cleandevicedirtydata) to clean up dirty data.<br/>The distributed data table configuration does not take effect in the [multi-device collaborative table mode](../../database/data-sync-of-rdb-store.md#data-sync-storage-mechanism).<br/>**System API:** This API is a system API.<br/>**Since:** 26.0.0<br/>**Model constraint:** This API is only used in the Stage model.<br/> |

## HAMode<sup>12+</sup>

Enumerates the HA modes of an RDB store.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**System API**: This is a system API.

| Name                             | Value  | Description            |
| ------------------------------- | --- | -------------- |
| SINGLE      | 0 | The data is to be written to a single RDB store.     |
| MAIN_REPLICA | 1 | The data is written to both the primary relational database storage and the replica relational database storage. Encryption scenarios and attach scenarios are not supported, which degrades database write performance. |

## Reference<sup>11+</sup>

Represents the reference between tables by field. If table **b** references table **a**, table **a** is the source table and **b** is the target table.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
| ---- | ---- | ---- | ---- | ---- |
| sourceTable | string | No| No| Name of the table referenced.  |
| targetTable | string | No| No| Name of the table that references the source table.  |
| refFields   | Record<string, string> | No| No|Fields referenced. In a KV pair, the key indicates the field in the source table, and the value indicates the field in the target table.      |

## DistributedConfig<sup>10+</sup>

Defines the configuration of the distributed mode of tables.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

| Name    | Type   | Read-Only | Optional| Description                                                        |
| -------- | ------- | ----  | ---- | ------------------------------------------------------------ |
| references<sup>11+</sup> | Array&lt;[Reference](#reference11)&gt; | No| Yes  | References between tables. You can reference multiple fields, and their values must be the same in the source and target tables. By default, database tables are not referenced with each other.<br>**System API**: This is a system API.<br>This parameter is supported since API version 11.|

## CloudSyncConfig

Defines the cloud sync configuration information.

**Since**: 26.0.0

**System capability:** SystemCapability.DistributedDataManager.CloudSync.Client

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

| Name | Type | Read-Only | Optional | Description |
|------|------|------|------|----------------------------------------------------------------------------|
| downloadOnly | boolean | No | Yes | Whether to download only cloud data to the local device. The value **true** means to download only cloud data to the local device, and **false** means to first download cloud data to the local device and then upload local data to the cloud. The default value is **false**. |

## RdbStore

Provides APIs for managing data in an RDB store.

Before using the following APIs, you should obtain a **RdbStore** instance by calling the [getRdbStore](arkts-apis-data-relationalStore-f.md#relationalstoregetrdbstore-1) method and then call the corresponding method through the instance.

In addition, use [execute](arkts-apis-data-relationalStore-RdbStore.md#execute12) to initialize the database table structure and related data first, ensuring that the prerequisites for related API calls are met.

### update

update(table: string, values: ValuesBucket, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback&lt;number&gt;):void

Updates data based on the specified **DataSharePredicates** object. This API uses an asynchronous callback to return the result. Due to the limit of the shared memory, the size of a single data record cannot exceed 2 MB. Otherwise, data cannot be obtained using the **get** methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) after **ResultSet** is obtained through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of **RdbStore**. As a result, the operation may fail or an exception may be thrown.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| table      | string                                                       | Yes   | Name of the specified target table. It cannot be an empty string.                                             |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)                                | Yes  | Rows of data to update in the RDB store. The key-value pair is associated with the column name in the target table.|
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes  | Update conditions specified by the **DataSharePredicates** object.               |
| callback   | AsyncCallback&lt;number&gt;                                  | Yes   | Callback function used to return the number of affected rows.                   |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800030  | SQLite: Unable to open the database file. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { ValuesBucket } from '@kit.ArkData';

let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4,
};
const valueBucket2: ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4,
};
const valueBucket3: ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4,
};

let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update("EMPLOYEE", valueBucket1, predicates, (err, rows) => {
    if (err) {
      console.error(`Updated failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Updated row count: ${rows}`);
  });
}
```

### update

update(table: string, values: ValuesBucket, predicates: dataSharePredicates.DataSharePredicates):Promise&lt;number&gt;

Updates data based on the specified **DataSharePredicates** object. This API uses a promise to return the result. Due to the limit of the shared memory, the size of a single data record cannot exceed 2 MB. Otherwise, data cannot be obtained using the **get** methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) after **ResultSet** is obtained through the [query](arkts-apis-data-relationalStore-RdbStore.md#query) or [querySql](arkts-apis-data-relationalStore-RdbStore.md#querysql) API of **RdbStore**. As a result, the operation may fail or an exception may be thrown.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| table      | string                                                       | Yes   | Name of the specified target table. It cannot be an empty string.                                             |
| values     | [ValuesBucket](arkts-apis-data-relationalStore-t.md#valuesbucket)                                | Yes  | Rows of data to update in the RDB store. The key-value pair is associated with the column name in the target table.|
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes  | Update conditions specified by the **DataSharePredicates** object.               |

**Return value**

| Type                 | Description                                     |
| --------------------- | ----------------------------------------- |
| Promise&lt;number&gt; | Promise object used to return the affected row count. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |
| 14800021  | SQLite: Generic error. Possible causes: Insert failed or the updated data does not exist. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800030  | SQLite: Unable to open the database file. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { ValuesBucket } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let value1 = "Rose";
let value2 = 22;
let value3 = 200.5;
let value4 = new Uint8Array([1, 2, 3, 4, 5]);

// You can use either of the following:
const valueBucket1: ValuesBucket = {
  'NAME': value1,
  'AGE': value2,
  'SALARY': value3,
  'CODES': value4,
};
const valueBucket2: ValuesBucket = {
  NAME: value1,
  AGE: value2,
  SALARY: value3,
  CODES: value4,
};
const valueBucket3: ValuesBucket = {
  "NAME": value1,
  "AGE": value2,
  "SALARY": value3,
  "CODES": value4,
};

let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).update("EMPLOYEE", valueBucket1, predicates).then((rows: number) => {
    console.info(`Updated row count: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Updated failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

### delete

delete(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback&lt;number&gt;):void

Deletes data from the RDB store based on the specified **DataSharePredicates** object. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                         |
| ---------- | ------------------------------------------------------------ | ---- | --------------------------------------------- |
| table      | string                                                       | Yes  | Name of the target table, which cannot be an empty string.             |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes  | Deletion conditions specified by the **DataSharePredicates** object.|
| callback   | AsyncCallback&lt;number&gt;                                  | Yes   | Callback function. If the data is deleted successfully, **err** is **undefined** and **data** is the number of affected rows; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |
| 14800021  | SQLite: Generic error. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800030  | SQLite: Unable to open the database file. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';

let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).delete("EMPLOYEE", predicates, (err, rows) => {
    if (err) {
      console.error(`Delete failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`Delete rows: ${rows}`);
  });
}
```

### delete

delete(table: string, predicates: dataSharePredicates.DataSharePredicates):Promise&lt;number&gt;

Deletes data from the RDB store based on the specified **DataSharePredicates** object. This API uses a promise to return the result.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                         |
| ---------- | ------------------------------------------------------------ | ---- | --------------------------------------------- |
| table      | string                                                       | Yes   | Specified target table name, which cannot be an empty string.                              |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes  | Deletion conditions specified by the **DataSharePredicates** object.|

**Return value**

| Type                 | Description                           |
| --------------------- | ------------------------------- |
| Promise&lt;number&gt; | Promise used to return the number of rows deleted.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**     |
|-----------| --------------------- |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |
| 14800021  | SQLite: Generic error. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800030  | SQLite: Unable to open the database file. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |
| 14800047  | The WAL file size exceeds the default limit. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Lisa");
if (store != undefined) {
  (store as relationalStore.RdbStore).delete("EMPLOYEE", predicates).then((rows: number) => {
    console.info(`Delete rows: ${rows}`);
  }).catch((err: BusinessError) => {
    console.error(`Delete failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

### query<sup>10+</sup>

query(table: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback&lt;ResultSet&gt;):void

Queries data from the RDB store based on specified conditions. This API uses an asynchronous callback to return the result. Due to the limit of the shared memory, the size of a single data record cannot exceed 2 MB. Otherwise, data cannot be obtained using the **get** methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) after **ResultSet** is obtained. As a result, the operation may fail or an exception may be thrown.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                                       |
| ---------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| table      | string                                                       | Yes   | Name of the specified target table, which cannot be an empty string.                                            |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes  | Query conditions specified by the **DataSharePredicates** object.              |
| callback   | AsyncCallback&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Yes   | Callback used to return the **ResultSet** object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**          |
|-----------| ------------------ |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';

let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query("EMPLOYEE", predicates, (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
    // Release the dataset memory.
    resultSet.close();
  });
}
```

### query

query(table: string, predicates: dataSharePredicates.DataSharePredicates, columns: Array&lt;string&gt;, callback: AsyncCallback&lt;ResultSet&gt;):void

Queries data from the RDB store based on specified conditions (for example, column). This API uses an asynchronous callback to return the result. Due to the limit of the shared memory, the size of a single data record cannot exceed 2 MB. Otherwise, data cannot be obtained using the **get** methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) after **ResultSet** is obtained. As a result, the operation may fail or an exception may be thrown.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                                       |
| ---------- | ------------------------------------------------------------ | ---- | ----------------------------------------------------------- |
| table      | string                                                       | Yes   | Name of the specified target table. It cannot be an empty string.                                            |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes  | Query conditions specified by the **DataSharePredicates** object.              |
| columns    | Array&lt;string&gt;                                          | Yes  | Columns to query. If this parameter is not specified, the query applies to all columns.           |
| callback   | AsyncCallback&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Yes   | Callback used to return the **ResultSet** object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**     |
|-----------| --------------- |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';

let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query("EMPLOYEE", predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"], (err, resultSet) => {
    if (err) {
      console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
    // Release the dataset memory.
    resultSet.close();
  });
}
```

### query

query(table: string, predicates: dataSharePredicates.DataSharePredicates, columns?: Array&lt;string&gt;):Promise&lt;ResultSet&gt;

Queries data from the RDB store based on specified conditions. This API uses a promise to return the result. Due to the limit of the shared memory, the size of a single data record cannot exceed 2 MB. Otherwise, data cannot be obtained using the **get** methods such as [getValue](arkts-apis-data-relationalStore-ResultSet.md#getvalue12) and [getString](arkts-apis-data-relationalStore-ResultSet.md#getstring) after **ResultSet** is obtained. As a result, the operation may fail or an exception may be thrown.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                            |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------ |
| table      | string                                                       | Yes   | Name of the specified target table. It cannot be an empty string.                                 |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes  | Query conditions specified by the **DataSharePredicates** object.   |
| columns    | Array&lt;string&gt;                                          | No  | Columns to query. If this parameter is not specified, the query applies to all columns.|

**Return value**

| Type                                                   | Description                                              |
| ------------------------------------------------------- | -------------------------------------------------- |
| Promise&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Returns a **ResultSet** object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**        |
|-----------| ----------- |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 14800000  | Inner error. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose");
if (store != undefined) {
  (store as relationalStore.RdbStore).query("EMPLOYEE", predicates, ["ID", "NAME", "AGE", "SALARY", "CODES"]).then((resultSet: relationalStore.ResultSet) => {
    console.info(`ResultSet column names: ${resultSet.columnNames}, column count: ${resultSet.columnCount}`);
    // resultSet is a cursor of a data set. By default, the cursor points to the -1st record. Valid data starts from 0.
    while (resultSet.goToNextRow()) {
      const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      console.info(`id=${id}, name=${name}, age=${age}, salary=${salary}`);
    }
    // Release the dataset memory.
    resultSet.close();
  }).catch((err: BusinessError) => {
    console.error(`Query failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

### cloudSync<sup>11+</sup>

cloudSync(mode: SyncMode, predicates: RdbPredicates, progress: Callback&lt;ProgressDetails&gt;, callback: AsyncCallback&lt;void&gt;): void

Manually performs device-cloud sync based on specified conditions. This API uses an asynchronous callback to return the result. The cloud sync function must be implemented. Otherwise, this API cannot be used.

> **NOTE**
>
> Since API version 18, you can specify assets in predicates when performing manual device-cloud sync. In this case, the sync mode must be **relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST**.
>
> When specifying the predicates, you can use the primary key (mandatory) and asset (optional) as sync conditions. If assets are specified, the predicate supports only [equalTo](arkts-apis-data-relationalStore-RdbPredicates.md#equalto), with a limit of 50 assets. If more assets are involved, you are advised to use only the primary key as the sync condition.

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**System API**: This is a system API.

**Parameters**

| Name        | Type                            | Mandatory| Description                           |
|-------------|--------------------------------| ---- |-------------------------------|
| mode        | [SyncMode](arkts-apis-data-relationalStore-e.md#syncmode)          | Yes  | Sync mode of the database.                  |
| predicates  | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md)                  | Yes  | Conditions for data sync.                 |
| progress    | Callback&lt;[ProgressDetails](arkts-apis-data-relationalStore-i.md#progressdetails10)&gt; | Yes  | Callback used to process database sync details.          |
| callback    | AsyncCallback&lt;void&gt;      | Yes   | Callback function. When the synchronization succeeds, **err** is **undefined**; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**    |
|-----------|--------------|
| 202       | if permission verification failed, application which is not a system application uses system API. |
| 401       | Parameter error. Possible causes: 1. Need 2 - 4  parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The tablesNames must be not empty. 5. The progress must be a callback type. 6.The callback must be a function.|
| 801       | Capability not supported.  |
| 14800014  | The target instance is already closed.      |

**Example 1**: Manually sync data on the local device with the cloud.

```ts
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.in("id", ["id1", "id2"]);

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, predicates, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail.schedule}`);
  }, (err) => {
    if (err) {
      console.error(`cloudSync failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('Cloud sync succeeded');
  });
};
```
**Example 2**: Download the specified asset.
```ts
let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
let asset: relationalStore.Asset = {
  name: "name",
  uri: "uri",
  path: "path",
  createTime: new Date().getTime().toString(),
  modifyTime: new Date().getTime().toString(),
  size: "1024"
};
// Specify the primary key and asset (asset column in the database) in the predicates.
predicates.beginWrap().equalTo("id", "id1").and().equalTo("asset", asset).endWrap();

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, predicates, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail.schedule}`);
  }, (err) => {
    if (err) {
      console.error(`cloud sync failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    console.info('cloud sync succeeded');
  });
};
```

### cloudSync<sup>11+</sup>

cloudSync(mode: SyncMode, predicates: RdbPredicates, progress: Callback&lt;ProgressDetails&gt;): Promise&lt;void&gt;

Manually performs device-cloud sync based on specified conditions. This API uses a promise to return the result. The cloud sync function must be implemented. Otherwise, this API cannot be used.

> **NOTE**
>
> Since API version 18, you can specify assets in predicates when performing manual device-cloud sync. In this case, the sync mode must be **relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST**.
>
> When specifying the predicates, you can use the primary key (mandatory) and asset (optional) as sync conditions. If assets are specified, the predicate supports only [equalTo](arkts-apis-data-relationalStore-RdbPredicates.md#equalto), with a limit of 50 assets. If more assets are involved, you are advised to use only the primary key as the sync condition.

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**System API**: This is a system API.

**Parameters**

| Name       | Type                             | Mandatory| Description                 |
|------------|---------------------------------| ---- |---------------------|
| mode       | [SyncMode](arkts-apis-data-relationalStore-e.md#syncmode)           | Yes  | Sync mode of the database.        |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md)                   | Yes  | Conditions for data sync.               |
| progress   | Callback&lt;[ProgressDetails](arkts-apis-data-relationalStore-i.md#progressdetails10)&gt; | Yes  | Callback used to process database sync details.|

**Return value**

| Type               | Description                                   |
| ------------------- | --------------------------------------- |
| Promise&lt;void&gt; | Promise used to return the synchronization result. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**           |
|-----------|---------------------------|
| 202       | if permission verification failed, application which is not a system application uses system API.  |
| 401       | Parameter error. Possible causes: 1. Need 2 - 4  parameter(s). 2. The RdbStore must be not nullptr. 3. The mode must be a SyncMode of cloud. 4. The tablesNames must be not empty. 5. The progress must be a callback type. |
| 801       | Capability not supported.       |
| 14800014  | The target instance is already closed.      |

**Example 1**: Manually sync data on the local device with the cloud.

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
predicates.in("id", ["id1", "id2"]);

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, predicates, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail.schedule}`);
  }).then(() => {
    console.info('cloud sync succeeded');
  }).catch((err: BusinessError) => {
    console.error(`cloud sync failed, code is ${err.code}, message is ${err.message}`);
  });
};
```
**Example 2**: Download the specified asset.
```ts
import { BusinessError } from '@kit.BasicServicesKit';

let predicates = new relationalStore.RdbPredicates("EMPLOYEE");
let asset: relationalStore.Asset = {
  name: "name",
  uri: "uri",
  path: "path",
  createTime: new Date().getTime().toString(),
  modifyTime: new Date().getTime().toString(),
  size: "1024"
};
// Specify the primary key and asset (asset column in the database) in the predicates.
predicates.beginWrap().equalTo("id", "id1").and().equalTo("asset", asset).endWrap();

if (store != undefined) {
  (store as relationalStore.RdbStore).cloudSync(relationalStore.SyncMode.SYNC_MODE_CLOUD_FIRST, predicates, (progressDetail: relationalStore.ProgressDetails) => {
    console.info(`progress: ${progressDetail.schedule}`);
  }).then(() => {
    console.info('Cloud sync succeeded');
  }).catch((err: BusinessError) => {
    console.error(`cloudSync failed, code is ${err.code}, message is ${err.message}`);
  });
};
```

### querySharingResource<sup>11+</sup>

querySharingResource(predicates: RdbPredicates, columns?: Array&lt;string&gt;): Promise&lt;ResultSet&gt;

Finds the shared resource of the data records that match the specified predicates and returns the result set. If columns are specified, the result set also contains the field values of the corresponding columns. This API uses a promise to return the result asynchronously. To use this API, the device-cloud sync capability must be implemented.

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                              |
| -------- | ----------------------------------------------------- | ---- | -------------------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Query conditions.   |
| columns    | Array&lt;string&gt;      | No  | Columns to be searched for. If this parameter is not specified, the returned result set contains only the shared resource ID.|

**Return value**

| Type | Description |
| -------- | ------------------------------------------------- |
| Promise&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Promise used to return the query result set. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**          |
|-----------|-------------|
| 401       | Parameter error. Possible causes: 1. Need 1 - 3  parameter(s)! 2. The RdbStore must be not nullptr. 3. The predicates must be an RdbPredicates. 4. The columns must be a string array. |
| 801       | Capability not supported.       |
| 14800000  | Inner error.                      |
| 14800011  | The current operation failed because the database is corrupted.           |
| 14800014  | The target instance is already closed.                        |
| 14800015  | The database does not respond.          |
| 14800021  | SQLite: Generic error. |
| 14800022  | SQLite: Callback routine requested an abort.          |
| 14800023  | SQLite: Access permission denied.         |
| 14800024  | SQLite: The database file is locked.         |
| 14800025  | SQLite: A table in the database is locked.           |
| 14800026  | SQLite: The database is out of memory.            |
| 14800027  | SQLite: Attempt to write a readonly database.         |
| 14800028  | SQLite: Some kind of disk I/O error occurred.             |
| 14800029  | SQLite: The database is full.           |
| 14800030  | SQLite: Unable to open the database file.        |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit.           |
| 14800032  | SQLite: Abort due to constraint violation.        |
| 14800033  | SQLite: Data type mismatch.             |
| 14800034  | SQLite: Library used incorrectly.          |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

let sharingResource: string;
let predicates = new relationalStore.RdbPredicates('test_table');
predicates.equalTo('data', 'data_test');
if (store != undefined) {
  (store as relationalStore.RdbStore).querySharingResource(predicates, ['uuid', 'data']).then((resultSet) => {
    if (!resultSet.goToFirstRow()) {
      console.error(`resultSet error`);
      return;
    }
    const res = resultSet.getString(resultSet.getColumnIndex(relationalStore.Field.SHARING_RESOURCE_FIELD));
    console.info(`sharing resource: ${res}`);
    sharingResource = res;
    resultSet.close();
  }).catch((err: BusinessError) => {
    console.error(`query sharing resource failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

### querySharingResource<sup>11+</sup>

querySharingResource(predicates: RdbPredicates, callback: AsyncCallback&lt;ResultSet&gt;): void

Finds the shared resource of the data records that match the specified predicates and returns the result set. This API uses an asynchronous callback to return the result. To use this API, the device-cloud sync capability must be implemented.

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                              |
| -------- | ----------------------------------------------------- | ---- | -------------------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md)              | Yes  | Query conditions.          |
| callback   | AsyncCallback&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt; | Yes  | Callback used to return the result set.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**     |
|-----------|------|
| 401       | Parameter error. Possible causes: 1. Need 1 - 3  parameter(s)! 2. The RdbStore must be not nullptr. 3. The predicates must be an RdbPredicates. |
| 801       | Capability not supported.                 |
| 14800000  | Inner error.          |
| 14800011  | The current operation failed because the database is corrupted.       |
| 14800014  | The target instance is already closed.      |
| 14800015  | The database does not respond.        |
| 14800021  | SQLite: Generic error. |
| 14800022  | SQLite: Callback routine requested an abort.         |
| 14800023  | SQLite: Access permission denied.                    |
| 14800024  | SQLite: The database file is locked.            |
| 14800025  | SQLite: A table in the database is locked.           |
| 14800026  | SQLite: The database is out of memory.           |
| 14800027  | SQLite: Attempt to write a readonly database.            |
| 14800028  | SQLite: Some kind of disk I/O error occurred.         |
| 14800029  | SQLite: The database is full.       |
| 14800030  | SQLite: Unable to open the database file.       |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit.         |
| 14800032  | SQLite: Abort due to constraint violation.      |
| 14800033  | SQLite: Data type mismatch.         |
| 14800034  | SQLite: Library used incorrectly.     |


**Example**

```ts
let sharingResource: string;
let predicates = new relationalStore.RdbPredicates('test_table');
predicates.equalTo('data', 'data_test');
if (store != undefined) {
  (store as relationalStore.RdbStore).querySharingResource(predicates, (err, resultSet) => {
    if (err) {
      console.error(`sharing resource failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    if (!resultSet.goToFirstRow()) {
      console.error(`resultSet error`);
      return;
    }
    const res = resultSet.getString(resultSet.getColumnIndex(relationalStore.Field.SHARING_RESOURCE_FIELD));
    console.info(`sharing resource: ${res}`);
    sharingResource = res;
    resultSet.close();
  });
}
```

### querySharingResource<sup>11+</sup>

querySharingResource(predicates: RdbPredicates, columns: Array&lt;string&gt;, callback: AsyncCallback&lt;ResultSet&gt;): void

Finds the shared resources of the data records that match the specified predicates, returns the result set of the found shared resources, and also returns the field values of the specified columns that match the predicates in the result set. This API uses an asynchronous callback to return the result. To use this API, the device-cloud sync capability must be implemented.

**System capability**: SystemCapability.DistributedDataManager.CloudSync.Client

**System API**: This is a system API.

**Parameters**

| Name  | Type                                                 | Mandatory| Description                                              |
| -------- | ----------------------------------------------------- | ---- | -------------------------------------------------- |
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes  | Query conditions.          |
| columns    | Array&lt;string&gt;              | Yes  | Columns to be searched for.          |
| callback   | AsyncCallback&lt;[ResultSet](arkts-apis-data-relationalStore-ResultSet.md)&gt;  | Yes  | Callback used to return the result set.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**      |
|-----------|--------------|
| 401       | Parameter error. Possible causes: 1. Need 1 - 3  parameter(s)! 2. The RdbStore must be not nullptr. 3. The predicates must be an RdbPredicates. 4. The columns must be a string array. |
| 801       | Capability not supported.       |
| 14800000  | Inner error.            |
| 14800011  | The current operation failed because the database is corrupted.         |
| 14800014  | The target instance is already closed.          |
| 14800015  | The database does not respond.          |
| 14800021  | SQLite: Generic error. |
| 14800022  | SQLite: Callback routine requested an abort.    |
| 14800023  | SQLite: Access permission denied.     |
| 14800024  | SQLite: The database file is locked.     |
| 14800025  | SQLite: A table in the database is locked.       |
| 14800026  | SQLite: The database is out of memory.      |
| 14800027  | SQLite: Attempt to write a readonly database.    |
| 14800028  | SQLite: Some kind of disk I/O error occurred.       |
| 14800029  | SQLite: The database is full.       |
| 14800030  | SQLite: Unable to open the database file.       |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit.      |
| 14800032  | SQLite: Abort due to constraint violation.       |
| 14800033  | SQLite: Data type mismatch.        |
| 14800034  | SQLite: Library used incorrectly.          |


**Example**

```ts
let sharingResource: string;
let predicates = new relationalStore.RdbPredicates('test_table');
predicates.equalTo('data', 'data_test');
if (store != undefined) {
  (store as relationalStore.RdbStore).querySharingResource(predicates, ['uuid', 'data'], (err, resultSet) => {
    if (err) {
      console.error(`sharing resource failed, code is ${err.code}, message is ${err.message}`);
      return;
    }
    if (!resultSet.goToFirstRow()) {
      console.error(`resultSet error`);
      return;
    }
    const res = resultSet.getString(resultSet.getColumnIndex(relationalStore.Field.SHARING_RESOURCE_FIELD));
    console.info(`sharing resource: ${res}`);
    sharingResource = res;
    resultSet.close();
  });
}
```


### lockCloudContainer<sup>12+</sup>

lockCloudContainer(): Promise&lt;number&gt;

Manually locks the cloud database of an application. This API uses a promise to return the result.

> **NOTE**
>
> After the cloud database is locked, data of the same application logged in with the same account on other devices cannot be synced to the cloud. The cloud sync function must be implemented. Otherwise, this API cannot be used.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**System API**: This is a system API.

**Return value**

| Type               | Description                                   |
| ------------------- | ---------------------------------------|
| Promise&lt;number&gt; | Promise object. If the lock is successful, returns the valid duration of the lock; if the lock fails, returns **0**, unit: ms. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **ID**| **Error Message**           |
|-----------|---------------------------|
| 202       | Permission verification failed, application which is not a system application uses system API.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).lockCloudContainer().then((time: number) => {
    console.info('lockCloudContainer succeeded time:' + time);
  }).catch((err: BusinessError) => {
    console.error(`lockCloudContainer failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

### unlockCloudContainer<sup>12+</sup>

unlockCloudContainer(): Promise&lt;void&gt;

Manually unlocks the cloud database of an application. This API uses a promise to return the result. The cloud sync function must be implemented. Otherwise, this API cannot be used.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**System API**: This is a system API.

**Return value**

| Type               | Description                                   |
| ------------------- | --------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md).

| **ID**| **Error Message**           |
|-----------|---------------------------|
| 202       | Permission verification failed, application which is not a system application uses system API.  |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).unlockCloudContainer().then(() => {
    console.info('unlockCloudContainer succeeded');
  }).catch((err: BusinessError) => {
    console.error(`unlockCloudContainer failed, code is ${err.code}, message is ${err.message}`);
  });
}
```

### restore<sup>12+</sup>

restore(): Promise&lt;void&gt;

Restores data from a replica RDB store file. This API uses a promise to return the result. This API can be used only when [HAMode](#hamode12) is **MAIN_REPLICA**, and cannot be used in transactions.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**System API**: This is a system API.

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**                                                |
|-----------| ------------------------------------------------------------ |
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 14800000  | Inner error. |
| 14800010  | Failed to open or delete the database by an invalid database path. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |
| 14800021  | SQLite: Generic error. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800030  | SQLite: Unable to open the database file. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  let promiseRestore = (store as relationalStore.RdbStore).restore();
  promiseRestore.then(() => {
    console.info('Succeeded in restoring.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to restore, code is ${err.code}, message is ${err.message}`);
  });
}
```

### retainDeviceData<sup>24+</sup>

retainDeviceData(retainDevices?: Record\<string, Array\<string>>): Promise\<void>

Retains the data synchronized from the corresponding devices in the distributed data table of the [single-version table mode](../../database/data-sync-of-rdb-store.md#data-sync-storage-mechanism), and deletes the data synchronized from other devices. This API uses a promise to return the result asynchronously.

Deletion is not supported for the distributed data table of the [multi-device collaborative table mode](../../database/data-sync-of-rdb-store.md#data-sync-storage-mechanism).

The more data to be deleted, the longer the execution takes.

> **NOTE**
>
> The input parameter can be empty, and the device ID list corresponding to a database table name can also be empty. However, neither the database table name nor the device ID can be an empty string.
>
> If the input parameter is empty, all data synchronized from other devices in all single-version distributed tables of the current database is deleted.
>
> If the device ID list corresponding to a database table name in the input parameter is empty, all data synchronized from other devices in the table is deleted.
>
> Data written locally and data synchronized from the device IDs passed in are retained, while data synchronized from other device IDs is deleted.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name       | Type                                                               | Mandatory | Description                                       |
| ------------ | ----------------------------------------------------------------- | ---- | ----------------------------------------- |
| retainDevices  | Record<string, Array\<string>> |  No  | Distributed database table names and corresponding device IDs to retain. There is no default value. If this parameter is not passed in, all synchronized data in all single-version distributed tables of the current database is deleted.|

**Return value**

| Type          | Description                       |
| -------------- | ------------------------ |
| Promise\<void> | Promise object that returns no value.  |

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                             |
| ------------ | ----------------------------------------------------------------------- |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 14800001     | Invalid arguments. Possible causes: 1. Parameter is out of valid range.  |
| 14800011     | The current operation failed because the database is corrupted.                    |
| 14800014     | The target instance is already closed.                            |
| 14800021     | SQLite: Generic error. |
| 14800024     | SQLite: The database file is locked.                                    |
| 14800042     | The database does not exist. Possible causes: 1. The database is deleted; 2. The database is not created. |
| 14800043     | The database does not support this scenario. Possible causes: 1. The database type is not supported;2. The table type is not supported; 3. This is a read-only database.|

**Example**

```ts
import { distributedDeviceManager } from '@kit.DistributedServiceKit';

async function retainDeviceData(store : relationalStore.RdbStore){
  const deviceManager = distributedDeviceManager.createDeviceManager('com.example.myapplication4');
  const deviceList = deviceManager.getAvailableDeviceListSync();
  const devices: string[] = [];
  deviceList.forEach(item => {
    if (item.networkId) {
      devices.push(item.networkId);
    }
  });
  console.info(`retainDeviceData, length is ${devices.length}`);
  if (store != undefined) {
    try {
      const retainDevices: Record<string, string[]> = {};
      retainDevices['EMPLOYEE'] = devices;
      await store.retainDeviceData(retainDevices);
      console.info(`retainDeviceData success`);
    } catch (e) {
      console.error(`retainDeviceData failed, code is ${e.code},message is ${e.message}`);
    }
  }
}
```

### updateDistributedInfo<sup>24+</sup>

updateDistributedInfo(info: DistributedInfo, predicates: RdbPredicates): Promise&lt;number&gt;

Updates distributed information. This API supports only the single-version table mode and uses a promise to return the result asynchronously.

It does not support updating distributed data tables in the multi-device collaborative table mode.

The more data to update, the longer the execution takes.

> **NOTE**
>
> If the device ID is passed in the input parameter **info**, it must be the ID of a device that has established a network connection with the current device.
>
> If [ORIGIN_ORIDEVICE](#distributedfield24) is passed in the input parameter **predicates**, only the equal-to-empty or not-equal-to-empty condition is allowed.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name       | Type                                                               | Required | Description                                       |
| ------------ | ----------------------------------------------------------------- | ---- | ----------------------------------------- |
| info  | [DistributedInfo](#distributedinfo24) |  Yes  | Distributed information to update.|
| predicates | [RdbPredicates](arkts-apis-data-relationalStore-RdbPredicates.md) | Yes   | Query conditions specified by the **RdbPredicates** instance object.        |

**Return value**

| Type          | Description                       |
| -------------- | ------------------------ |
| Promise&lt;number&gt; | Promise used to return the number of updated data records. |

**Error codes:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                                             |
| ------------ | ----------------------------------------------------------------------- |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 14800001     | Invalid arguments. Possible causes: 1. Parameter is out of valid range.  |
| 14800011     | The current operation failed because the database is corrupted.                    |
| 14800014     | The target instance is already closed.                            |
| 14800015     | The database does not respond. |
| 14800021     | SQLite: Generic error. |
| 14800024     | SQLite: The database file is locked.                                    |
| 14800043     | The database does not support this scenario. Possible causes: 1. The database type is not supported;2. The table type is not supported; 3. This is a read-only database.|

**Example**

```ts
import { distributedDeviceManager } from '@kit.DistributedServiceKit';
async function updateDistributedInfoInsert(store : relationalStore.RdbStore){
  const deviceManager = distributedDeviceManager.createDeviceManager('com.example.myapplication4');
  const deviceList = deviceManager.getAvailableDeviceListSync();
  const devices: string[] = [];
  deviceList.forEach(item => {
    if (item.networkId) {
      devices.push(item.networkId);
    }
  });
  console.info(`updateDistributedInfoInsert, length is ${devices.length}`);
  if (store != undefined && devices.length > 0) {
    try {
      const DISTRIBUTEDINFOINSERT:relationalStore.DistributedInfo = {
        flag: relationalStore.DistributedOrigin.ORI_REMOTE,
        oriDevice: devices[0]
      }
      const predicates = new relationalStore.RdbPredicates('EMPLOYEE');
      predicates.equalTo(relationalStore.DistributedField.ORIGIN, relationalStore.DistributedOrigin.ORI_LOCAL);
      predicates.equalTo(relationalStore.DistributedField.ORIGIN_ORIDEVICE, "");
      await store.updateDistributedInfo(DISTRIBUTEDINFOINSERT, predicates);
      console.info(`updateDistributedInfoInsert success`);
    } catch (e) {
      console.error(`updateDistributedInfoInsert failed, code is ${e.code},message is ${e.message}`);
    }
  }
}

async function updateDistributedInfoUpdate(store : relationalStore.RdbStore){
  if (store != undefined) {
    try {
      const DISTRIBUTEDINFOUPDATE:relationalStore.DistributedInfo = {
        flag: relationalStore.DistributedOrigin.ORI_REMOTE,
      }
      const predicates = new relationalStore.RdbPredicates('EMPLOYEE');
      predicates.equalTo(relationalStore.DistributedField.ORIGIN, relationalStore.DistributedOrigin.ORI_LOCAL);
      predicates.notEqualTo(relationalStore.DistributedField.ORIGIN_ORIDEVICE, "");
      await store.updateDistributedInfo(DISTRIBUTEDINFOUPDATE, predicates);
      console.info(`updateDistributedInfoUpdate success`);
    } catch (e) {
      console.error(`updateDistributedInfoUpdate failed, code is ${e.code},message is ${e.message}`);
    }
  }
}
```

## cleanDeviceDirtyData

cleanDeviceDirtyData(table: string, cursor?: number): Promise&lt;void&gt;

Manually cleans up the data synchronized from the peer device after the peer device deletes it. This API uses a promise to return the result asynchronously.

**Since**: 26.0.0

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name   | Type                                                  | Mandatory | Description                                               |
| -------- | ----------------------------------------------------- | ---- | -------------------------------------------------- |
| table     | string           | Yes   | Name of the database table to be cleaned up. The table name can contain only letters, digits, and underscores, and its length ranges from 1 to 256.           |
| cursor    | number           | No   | Data cursor. Dirty data whose cursor is not greater than this value will be cleaned up. It is an integer greater than 0. If a value less than or equal to 0 is passed in, an exception is thrown with the message indicating invalid parameters. If this parameter is not specified, all dirty data in the current table is cleaned up. |

**Return value**

| Type     | Description                                              |
| -------- | ------------------------------------------------- |
| Promise\<void> | Promise object that returns no value.        |

**Error code:**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**     |
|-----------|---------------|
| 202       | Permission verification failed, application which is not a system application uses system API. |
| 14800001  | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800014  | The target instance is already closed. |
| 14800015  | The database does not respond. |
| 14800021  | SQLite: Generic error. |
| 14800024  | SQLite: The database file is locked. |
| 14800043  | The database does not support this scenario. Possible causes: 1. The database type is not support;2. The table type is not supported; 3. This is a read-only database.|

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

if (store != undefined) {
  (store as relationalStore.RdbStore).cleanDeviceDirtyData('test_table', 100).then(() => {
    console.info('Succeeded in cleaning device dirty data.');
  }).catch((err: BusinessError) => {
    console.error(`Failed to clean device dirty data: code is ${err.code}, message is ${err.message}.`);
  });
}
```

## ResultSet

Provides APIs to access the **resultSet** object returned by **query()**.

### getFloat32Array<sup>12+</sup>

getFloat32Array(columnIndex: number): Float32Array

Obtains the value of the specified column in the current row as a floating-point array. This API is available only in a vector database (configured with **vector** set to **true** in [StoreConfig](arkts-apis-data-relationalStore-i.md#storeconfig)).

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name     | Type  | Mandatory| Description                   |
| ----------- | ------ | ---- | ----------------------- |
| columnIndex | number | Yes  | Index of the target column, starting from 0.|

**Return value**

| Type      | Description                            |
| ---------- | -------------------------------- |
| Float32Array | Value obtained, in a Float32Array.|

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [RDB Store Error Codes](errorcode-data-rdb.md).

| **ID**| **Error Message**         |
|-----------| ------------ |
| 401       | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801       | The capability is not supported because the database is not a vector DB. |
| 14800011  | The current operation failed because the database is corrupted. |
| 14800013  | Column index is out of bounds. |
| 14800014  | The target instance is already closed. |
| 14800021  | SQLite: Generic error. |
| 14800022  | SQLite: Callback routine requested an abort. |
| 14800023  | SQLite: Access permission denied. |
| 14800024  | SQLite: The database file is locked. |
| 14800025  | SQLite: A table in the database is locked. |
| 14800026  | SQLite: The database is out of memory. |
| 14800027  | SQLite: Attempt to write a readonly database. |
| 14800028  | SQLite: Some kind of disk I/O error occurred. |
| 14800029  | SQLite: The database is full. |
| 14800030  | SQLite: Unable to open the database file. |
| 14800031  | SQLite: TEXT or BLOB exceeds size limit. |
| 14800032  | SQLite: Abort due to constraint violation. |
| 14800033  | SQLite: Data type mismatch. |
| 14800034  | SQLite: Library used incorrectly. |

**Example**

```ts
let resultSet: relationalStore.ResultSet | undefined;

const id = (resultSet as relationalStore.ResultSet).getFloat32Array(0);
```

## LiteResultSet<sup>23+</sup>

Provides access methods for the database result set generated by querying the database. A result set is the collection of results returned after a user calls the relational database query API. It provides multiple flexible data access methods for users to obtain various data.

### getFloat32Array<sup>23+</sup>

getFloat32Array(columnIndex: number): Float32Array

Obtains the value of the specified column in the current row as a float array. This API is available only in a vector database (with **vector** set to **true** in [StoreConfig](arkts-apis-data-relationalStore-i.md#storeconfig)).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters**

| Name        | Type   | Required | Description                              |
| ----------- | ------ | -------- | ---------------------------------------- |
| columnIndex | number | Yes      | Index of the target column, starting from 0. |

**Return value**

| Type         | Description                                        |
| ------------ | -------------------------------------------------- |
| Float32Array | Value of the specified column returned as a float array. |

**Error Codes**

For details about the following error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| **Error Code ID** | **Error Message**                                             |
| ----------------- | ------------------------------------------------------------ |
| 14800012          | ResultSet is empty or pointer index is out of bounds. |
| 14800013          | Column index is out of bounds. |
| 14800014          | The target instance is already closed. |
| 14800041          | Type conversion failed. |

**Example**

```ts
async function getFloat32ArrayExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const name = resultSet.getFloat32Array(resultSet.getColumnIndex("FLOATARRAY"));
      resultSet.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## DistributedOrigin<sup>24+</sup>

Represents the data origin. Use the enum name instead of the enum value.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

| Name           | Value | Description                               |
| -------------- | ---- | ---------------------------------- |
| ORI_LOCAL       |  0  | Local data.      |
| ORI_CLOUD       |  1  | Data synchronized from the cloud.     |
| ORI_REMOTE      |  2  | Data synchronized between devices. |

## DistributedField<sup>24+</sup>

Represents the special fields used for predicate query conditions. Use the enum names instead of the enum values.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

| Name           | Value   | Description                               |
| -------------- | ---- | ---------------------------------- |
| ORIGIN      | '#_origin'     | Field name used to specify the data source during lookup or update.    |
| ORIGIN_ORIDEVICE  | '#_ori_device' | Device ID of the data producer specified during lookup or update. If this value is empty, it indicates the local device; if not empty, it indicates another networked device.|
| CURSOR_FIELD      | '#_cursor'     | Field name used for cursor lookup.<br/>**Since:** 26.0.0<br/> |
| DELETED_FLAG_FIELD  | '#_deleted_flag' | Field filled in when the result set returned by cursor lookup is returned. **true** indicates data deleted by the peer device and synchronized to the local device. **false** indicates data written or updated by the peer device and synchronized to the local device, or data written or updated by the local device.<br/>**Since:** 26.0.0<br/> |

## DistributedInfo<sup>24+</sup>

Records distributed information.

**Model restriction**: This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

| Name | Type | Read-Only | Optional | Description |
| ---- | ---- | ---- | ---- | ---- |
| flag | [DistributedOrigin](#distributedorigin24) | No | Yes | Data source. If not passed, the original value is retained. |
| oriDevice | string | No | Yes | Device ID of the data producer. If not passed, the original device ID is retained. |
