# LiteResultSet

```TypeScript
class LiteResultSet
```

Defines APIs to access the result set obtained by querying the RDB store. This result set is the collection of results returned with the **query()** method called.

The **LiteResultSet** instance is not refreshed in real time. After using the result set, if the data in the database is changed (by being added, deleted, or modified), you need to query the result set again to obtain the latest data.

In the following API examples, you need to obtain an **LiteResultSet** instance by using a query method, such as [queryWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querywithoutrowcount) or [querySqlWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querysqlwithoutrowcount), and then call the corresponding method through this instance.

> **NOTE:** 
> 
> - The initial APIs of this class are supported since API version 23.

**Since:** 23

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## Modules to Import

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## close

```TypeScript
close(): void
```

Closes this **resultSet** to release memory. If the **resultSet** is not closed, FD or memory leaks may occur.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Examples**

```TypeScript
async function closeExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getAsset

```TypeScript
getAsset(columnIndex: number): Asset
```

Obtains the value in the specified column in the current row as an [Asset](arkts-arkdata-relationalstore-asset-i.md).

If the data type of the current column is Asset, the value is returned as an Asset. If the value in the current column is **null**, **null** is returned. If the data type of the current column is not Asset, 14800041 is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [Asset](arkts-arkdata-relationalstore-asset-i.md) | Value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-type-conversion-failure) | Type conversion failed. |

**Examples**

```TypeScript
async function getAssetExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const doc = resultSet.getAsset(resultSet.getColumnIndex("DOC"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getAssets

```TypeScript
getAssets(columnIndex: number): Assets
```

Obtains the value in the specified column in the current row as [Assets](arkts-arkdata-relationalstore-assets-t.md).

If the data type of the current column is Assets, the value is returned as Assets. If the value in the current column is **null**, **null** is returned. If the data type of the current column is not Assets, 14800041 is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [Assets](arkts-arkdata-relationalstore-assets-t.md) | Value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-type-conversion-failure) | Type conversion failed. |

**Examples**

```TypeScript
async function getAssetsExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const name = resultSet.getAssets(resultSet.getColumnIndex("DOCS"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getBlob

```TypeScript
getBlob(columnIndex: number): Uint8Array
```

Obtains the value in the specified column in the current row as a byte array.

If the data type of the current column is INTEGER, DOUBLE, TEXT, or BLOB, the data is converted to a byte array and returned. If the content of the column is null/empty, an empty byte array is returned.

If the data type of the current column is ASSET, ASSETS, FLOATVECTOR, or BIGINT, 14800041 is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-type-conversion-failure) | Type conversion failed. |

**Examples**

```TypeScript
async function getBlobExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const name = resultSet.getBlob(resultSet.getColumnIndex("CODES"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getColumnIndex

```TypeScript
getColumnIndex(columnName: string): number
```

Obtains the column index based on the column name.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnName | string | Yes | Column name. If the result set contains duplicate column names, the return value is not as expected. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Column index obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
async function getColumnIndexExample(store : relationalStore.RdbStore){
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      const idIndex = resultSet.getColumnIndex("ID");
      const nameIndex = resultSet.getColumnIndex("NAME");
      const ageIndex = resultSet.getColumnIndex("AGE");
      const salaryIndex = resultSet.getColumnIndex("SALARY");
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getColumnName

```TypeScript
getColumnName(columnIndex: number): string
```

Obtains the column name based on the column index.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the column in the result set, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Column name obtained. If the result set contains duplicate column names, the return value is not as expected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
async function getColumnNameExample(store : relationalStore.RdbStore){
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      const id = resultSet.getColumnName(0);
      const name = resultSet.getColumnName(1);
      const age = resultSet.getColumnName(2);
      const salary = resultSet.getColumnName(3);
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getColumnNames

```TypeScript
getColumnNames(): Array<string>
```

Obtains the names of all columns in the result set.

The column names are returned in a string array. The sequence of strings in the array is the same as that of columns in the result set.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;string&gt; | Names of all columns in the result set obtained. Duplicate column names can be obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
async function getColumnNamesExample(store: relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    // Query EMPLOYEE1 and EMPLOYEE2 and obtain the duplicate column names. store is the obtained RdbStore instance.
    resultSet = await store.querySqlWithoutRowCount("SELECT e1.NAME, e2.NAME, e1.AGE, e2.AGE FROM EMPLOYEE1 e1 LEFT JOIN EMPLOYEE2 e2 ON e1.SALARY=e2.SALARY");
    if (resultSet != undefined) {
      const names = resultSet.getColumnNames();
      resultSet!.close();
    }
  } catch (err) {
    console.error(`Failed to get column names: code:${err.code}, message:${err.message}`);
  }
}
```

## getColumnType

```TypeScript
getColumnType(columnIdentifier: number | string): Promise<ColumnType>
```

Obtains the column type based on the specified column index or column name. This API uses a promise to return the result.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIdentifier | number &#124; string | Yes | Index or name of the column in the result set. The index starts from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ColumnType](arkts-arkdata-relationalstore-columntype-e.md)&gt; | Promise used to return the column type obtained. If the result set contains duplicate column names, the return value is not as expected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
async function getColumnTypeExample(store : relationalStore.RdbStore){
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      //Method 1: Obtain the column type by column name.
      let idType = await resultSet.getColumnType("ID");
      let nameType = await resultSet.getColumnType("NAME");
      let ageType = await resultSet.getColumnType("AGE");
      let salaryType = await resultSet.getColumnType("SALARY");
      let codesType = await resultSet.getColumnType("CODES");
      //Method 2: Obtain the column type by column index.
      let identityType = await resultSet.getColumnType(5);
      let assetDataType = await resultSet.getColumnType(6);
      let assetsDataType = await resultSet.getColumnType(7);
      let floatArrayType = await resultSet.getColumnType(8);
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getColumnTypeSync

```TypeScript
getColumnTypeSync(columnIdentifier: number | string): ColumnType
```

Obtains the column type based on the specified column index or column name.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIdentifier | number &#124; string | Yes | Index or name of the column in the result set. The index starts from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [ColumnType](arkts-arkdata-relationalstore-columntype-e.md) | Column type obtained. If the result set contains duplicate column names, the return value is not as expected. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
async function getColumnTypeSyncExample(store : relationalStore.RdbStore){
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      //Method 1: Obtain the column type by column name.
      let idType = resultSet.getColumnTypeSync("ID");
      let nameType = resultSet.getColumnTypeSync("NAME");
      let ageType = resultSet.getColumnTypeSync("AGE");
      let salaryType = resultSet.getColumnTypeSync("SALARY");
      let codesType = resultSet.getColumnTypeSync("CODES");
      //Method 2: Obtain the column type by column index.
      let identityType = resultSet.getColumnTypeSync(5);
      let assetDataType = resultSet.getColumnTypeSync(6);
      let assetsDataType = resultSet.getColumnTypeSync(7);
      let floatArrayType = resultSet.getColumnTypeSync(8);
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getCurrentRowData

```TypeScript
getCurrentRowData(): RowData
```

Obtains the values of all columns in this row.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [RowData](arkts-arkdata-relationalstore-rowdata-t.md) | Values of all columns in this row obtained. The values of columns with the same name can be obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
async function getCurrentRowDataExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    // Query EMPLOYEE1 and EMPLOYEE2 and obtain the values of the current row that contain duplicate column names. store is the obtained RdbStore instance.
    resultSet = await store.querySqlWithoutRowCount("SELECT e1.NAME, e2.NAME, e1.AGE, e2.AGE FROM EMPLOYEE1 e1 LEFT JOIN EMPLOYEE2 e2 ON e1.SALARY=e2.SALARY");
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const rowData = resultSet.getCurrentRowData();
      console.info(`rowData: ${JSON.stringify(rowData)}`);
      resultSet!.close();
    }
  } catch (err) {
    console.error(`Failed to get row data: code:${err.code}, message:${err.message}`);
  }
}
```

## getDouble

```TypeScript
getDouble(columnIndex: number): number
```

Obtains the value in the specified column in the current row as a Double.

If the data type of the current column is INTEGER, DOUBLE, or TEXT, the value is converted to the Double type and returned. Non-numeric TEXT and BLOB types return **0.0**. If the content of the column is null/empty, **0.0** is returned.

If the data type of the current column is ASSET, ASSETS, FLOATVECTOR, or BIGINT, 14800041 is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-type-conversion-failure) | Type conversion failed. |

**Examples**

```TypeScript
async function getDoubleExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getLong

```TypeScript
getLong(columnIndex: number): number
```

Obtains the value from the specified column in the current row, and returns a value of Long type.

If the data type of the current column is INTEGER, DOUBLE, TEXT, or BLOB, a value of Long type is returned. If the column is null, **0** is returned. If the data type is INTEGER and the value is greater than **Number.MAX_SAFE_INTEGER** or less than **Number.MIN_SAFE_INTEGER**, you are advised to use the [getString](#getstring) API to obtain the value without losing precision. If the data type in the specified column is DOUBLE, you are advised to use the [getDouble](#getdouble) API to obtain the value without precision loss.

If the data type of the current column is ASSET, ASSETS, FLOATVECTOR, or BIGINT, 14800041 is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value obtained. <br>The value range supported by this API is **Number.MIN_SAFE_INTEGER** to **Number.MAX_SAFE_INTEGER**. If the value is out of this range, use [getDouble](#getdouble) for DOUBLE values and [getString](#getstring) for INTEGER values. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-type-conversion-failure) | Type conversion failed. |

**Examples**

```TypeScript
async function getLongExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getRow

```TypeScript
getRow(): ValuesBucket
```

Obtains data for the current row.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md) | Value of the specified row. If the result set contains duplicate column names, the return value is not as expected. You are advised to use the [getCurrentRowData](#getcurrentrowdata) API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |

**Examples**

```TypeScript
async function getRowExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const rowData = resultSet.getRow();
      console.info(`rowData: ${JSON.stringify(rowData)}`);
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getRows

```TypeScript
getRows(maxCount: number, position?: number): Promise<Array<ValuesBucket>>
```

Obtains a specified amount of data from the result set. This API uses a promise to return the result. Do not call this API concurrently with other APIs of [LiteResultSet](arkts-arkdata-data-relationalstore.md). Otherwise, unexpected data may be obtained.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxCount | number | Yes | Number of rows to obtain. The value is a positive integer. |
| position | number | No | Start position for obtaining data from the result set. The value is a non-negative integer. If this parameter is not specified, data is obtained from the current row of the result set (by default, it is the first row of the result set when data is obtained for the first time). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ValuesBucket](arkts-arkdata-relationalstore-valuesbucket-t.md)&gt;&gt; | Promise used to return **maxCount** rows of data obtained. If the number of remaining records is less than **maxCount**, the remaining records are returned. Returning an empty array indicates that the end of the result set is reached. If the result set contains duplicate column names, the return values are not as expected. You are advised to use the [getRowsData](#getrowsdata) API. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |

**Examples**

```TypeScript
async function getRowsExample(store : relationalStore.RdbStore) {
  // Obtain 100 rows of data.
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    // Example 1: Specify only maxCount.
    if (resultSet != undefined) {
      let rows: Array<relationalStore.ValuesBucket>;
      let maxCount: number = 50;
      // Obtain data from the current row of the result set. By default, the first fetch starts from the first row of the current result set. Subsequent fetches start from the row following the last row retrieved.
      // getRows automatically moves the current row of the result set to the next row after the end position of the last retrieval by getRows. You do not need to use the goToNextRow API to move the row.
      while ((rows = await resultSet.getRows(maxCount)).length != 0) {
        console.info(JSON.stringify(rows[0]));
      }
    }
  
    // Example 2: Specify maxCount and position.
    if (resultSet != undefined) {
      let rows: Array<relationalStore.ValuesBucket>;
      let maxCount: number = 50;
      let position: number = 50;
      while ((rows = await resultSet.getRows(maxCount, position)).length != 0) {
        console.info(JSON.stringify(rows[0]));
        position += rows.length;
      }
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getRowsData

```TypeScript
getRowsData(maxCount: number, position?: number): Promise<RowsData>
```

Obtains data of a specified number of rows from the specified position. This API uses a promise to return the result. Do not call this API concurrently with other APIs of [ResultSet](arkts-arkdata-data-relationalstore.md). Otherwise, unexpected data may be obtained.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxCount | number | Yes | Number of rows to obtain. The value is a positive integer. If the value is not a positive integer, error 14800001 will be thrown. |
| position | number | No | Start position for obtaining data from the result set. The value is a non-negative integer. If this parameter is not specified, data is obtained from the current row of the result set (by default, it is the first row of the result set when data is obtained for the first time). If the value is not a non-negative integer, error code 14800001 will be thrown. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RowsData](arkts-arkdata-relationalstore-rowsdata-t.md)&gt; | Promise used to return **maxCount** rows of data obtained. If the number of remaining records is less than **maxCount**, the remaining records are returned. Returning an empty array indicates that the end of the result set is reached. The values of columns with the same name can be obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |

**Examples**

```TypeScript
async function getRowsDataExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    // Query EMPLOYEE1 and EMPLOYEE2 and obtain the values of multiple rows that contain duplicate column names. store is the obtained RdbStore instance.
    resultSet = await store.querySqlWithoutRowCount("SELECT e1.NAME, e2.NAME, e1.AGE, e2.AGE FROM EMPLOYEE1 e1 LEFT JOIN EMPLOYEE2 e2 ON e1.SALARY=e2.SALARY");
    // Obtain 50 rows of data.
    // Example 1: Specify only maxCount.
    if (resultSet != undefined) {
      let rowsData: relationalStore.RowsData;
      // Obtain data from the current row of the result set. By default, the first fetch starts from the first row of the current result set. Subsequent fetches start from the row following the last row retrieved.
      // getRowsData automatically moves the current row of the result set to the next row after the end position of the last retrieval by getRowsData. You do not need to use the goToNextRow API to move the row.
      let maxCount: number = 50;
      let rowCount: number = 0;
      while ((rowsData = await resultSet.getRowsData(maxCount)).length != 0) {
        rowsData.forEach((rowData, index) => {
          // Query result of the row specified by rowCount + index + 1
          console.info(`${rowCount + index + 1}: ${rowData}`);
        });
        rowCount += rowsData.length;
      }
    }
  
    // Example 2: Specify maxCount and position.
    if (resultSet != undefined) {
      let rowsData: relationalStore.RowsData;
      let maxCount: number = 50;
      let position: number = 50;
      while ((rowsData = await resultSet.getRowsData(maxCount, position)).length != 0) {
        rowsData.forEach((rowData, index) => {
          // Query result of the row specified by position + index + 1
          console.info(`${position + index + 1}: ${rowData}`);
        });
        position += rowsData.length;
      }
      resultSet!.close();
    }
  } catch (err) {
    console.error(`Failed to get rows data: code:${err.code}, message:${err.message}`);
  }
}
```

## getString

```TypeScript
getString(columnIndex: number): string
```

Obtains the value in the specified column in the current row as a string.

If the data type of the current column is INTEGER, DOUBLE, TEXT, or BLOB type, the value is returned as a string. If the content of the column is null/empty, an empty string **""** is returned.

If the data type of the current column is DOUBLE, precision loss may occur. You are advised to use [getDouble](#getdouble) API to obtain the value.

If the data type of the current column is ASSET, ASSETS, FLOATVECTOR, or BIGINT, 14800041 is returned.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-type-conversion-failure) | Type conversion failed. |

**Examples**

```TypeScript
async function getStringExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## getValue

```TypeScript
getValue(columnIndex: number): ValueType
```

Obtains the value of the specified column in the current row.

If the value type is INTEGER and the value is greater than **Number.MAX_SAFE_INTEGER** or less than **Number.MIN_SAFE_INTEGER**, you are advised to use the [getString](#getstring) API to obtain the value without precision loss.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| [ValueType](arkts-arkdata-relationalstore-valuetype-t.md) | Type of the data field returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |

**Examples**

```TypeScript
async function getValueExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const name = resultSet.getValue(resultSet.getColumnIndex("NAME"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## goToNextRow

```TypeScript
goToNextRow(): boolean
```

Moves the result set to the next row.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the result set is successfully moved to the next row; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlite-text-or-blob-exceeds-the-limit) | SQLite: TEXT or BLOB exceeds size limit. |

**Examples**

```TypeScript
async function goToNextRowExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```

## isColumnNull

```TypeScript
isColumnNull(columnIndex: number): boolean
```

Checks whether the value in the specified column is null.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the value is null; returns **false** otherwise. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-invalid-parameter) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-database-file-corrupted) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql-query-statement-required) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite-generic-error) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite-insufficient-database-memory) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite-io-error) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite-unable-to-open-the-database-file) | SQLite: Unable to open the database file |

**Examples**

```TypeScript
async function isColumnNullExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      const name = resultSet.isColumnNull(resultSet.getColumnIndex("NAME"));
      resultSet!.close();
    }
  } catch (err) {
    console.error(`failed, code is ${err.code}, message is ${err.message}`);
  }
}
```
