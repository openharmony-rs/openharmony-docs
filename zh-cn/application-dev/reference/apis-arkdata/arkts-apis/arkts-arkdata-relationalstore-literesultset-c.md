# LiteResultSet

提供查询数据库后生成的结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。LiteResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。下列API示例中，都需先使用[queryWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querywithoutrowcount)、 [querySqlWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querysqlwithoutrowcount)等query类方法中任一方法获取到LiteResultSet实例，再 通过此实例调用对应方法。

> **说明：**
> 
> - 本class首批接口从API version 23开始支持。

**起始版本：** 23

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## 导入模块

```TypeScript
import { relationalStore } from '@kit.ArkData';
```

## close

```TypeScript
close(): void
```

关闭结果集，若不关闭可能会引起fd泄漏和内存泄漏。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例**

```TypeScript
if (resultSet != undefined) {
  (resultSet as relationalStore.ResultSet).close();
}
```

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

以[Asset](arkts-arkdata-relationalstore-asset-i.md)形式获取当前行中指定列的值。如果当前列的数据类型为Asset类型，会以Asset类型返回指定值；如果当前列中的值为null时，会返回null；如果当前列的数据类型非Asset类型，则返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Asset | 以Asset形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |

**示例**

```TypeScript
if (resultSet != undefined) {
  const doc = (resultSet as relationalStore.ResultSet).getAsset((resultSet as relationalStore.ResultSet).getColumnIndex("DOC"));
}
```

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

以[Assets](arkts-arkdata-relationalstore-assets-t.md)形式获取当前行中指定列的值。如果当前列的数据类型为Assets类型，会以Assets类型返回指定值；如果当前列中的值为null时，会返回null；如果当前列的数据类型非Assets类型，则返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Assets | 以Assets形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |

**示例**

```TypeScript
if (resultSet != undefined) {
  const docs = (resultSet as relationalStore.ResultSet).getAssets((resultSet as relationalStore.ResultSet).getColumnIndex("DOCS"));
}
```

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

以字节数组的形式获取当前行中指定列的值。如果当前列的数据类型为INTEGER、DOUBLE、TEXT、BLOB类型，会转成字节数组类型返回指定值，如果该列内容为空时，会返回空字节数组。如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会抛出错误码14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 以字节数组的形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |

**示例**

```TypeScript
if (resultSet != undefined) {
  const codes = (resultSet as relationalStore.ResultSet).getBlob((resultSet as relationalStore.ResultSet).getColumnIndex("CODES"));
}
```

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

根据指定的列名获取列索引。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnName | string | 是 | 表示结果集中指定列的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定列的索引。当结果集中包含重名列时，返回值会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
if (resultSet != undefined) {
  const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
  const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
  const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
  const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
}
```

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

根据指定的列索引获取列名。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 表示结果集中指定列的索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定列的名称。当结果集中包含重名列时，返回值会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
if (resultSet != undefined) {
  const id = (resultSet as relationalStore.ResultSet).getColumnName(0);
  const name = (resultSet as relationalStore.ResultSet).getColumnName(1);
  const age = (resultSet as relationalStore.ResultSet).getColumnName(2);
}
```

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

获取结果集中所有列的名称。列名以字符串数组的形式返回，数组中字符串的顺序与结果集中列的顺序一致。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array & lt;string & gt; | 返回结果集中所有列的名称。支持获取包含重名列的列名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
try {
  // 联表查询EMPLOYEE1和EMPLOYEE2，并获取重名的列名。store为获取到的RdbStore实例。
  let resultSet: relationalStore.ResultSet = await store.querySql("SELECT e1.NAME, e2.NAME, e1.AGE, e2.AGE FROM EMPLOYEE1 e1 LEFT JOIN EMPLOYEE2 e2 ON e1.SALARY=e2.SALARY");
  if (resultSet != undefined) {
    const names = resultSet.getColumnNames();
    resultSet.close();
  }
} catch (err) {
  console.error(`Failed to get column names: code:${err.code}, message:${err.message}`);
}
```

```TypeScript
async function getColumnNamesExample(store: relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    // 联表查询EMPLOYEE1和EMPLOYEE2，并获取重名的列名。store为获取到的RdbStore实例。
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

根据指定的列索引或列名称获取列数据类型，使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIdentifier | number \| string | 是 | 表示结果集中指定列的索引或名称，索引从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ColumnType](arkts-arkdata-relationalstore-columntype-e.md)&gt; | Promise对象。返回指定列的数据类型。当结果集中包含重名列时，通过列名获取的结果会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
if (resultSet != undefined) {
  let idType = await (resultSet as relationalStore.ResultSet).getColumnType("ID") as relationalStore.ColumnType;
  let nameType = await (resultSet as relationalStore.ResultSet).getColumnType("NAME") as relationalStore.ColumnType;
  let ageType = await (resultSet as relationalStore.ResultSet).getColumnType("AGE") as relationalStore.ColumnType;
  let salaryType = await (resultSet as relationalStore.ResultSet).getColumnType("SALARY") as relationalStore.ColumnType;
  let codesType = await (resultSet as relationalStore.ResultSet).getColumnType("CODES") as relationalStore.ColumnType;
  let identityType = await (resultSet as relationalStore.ResultSet).getColumnType(5) as relationalStore.ColumnType;
  let assetDataType = await (resultSet as relationalStore.ResultSet).getColumnType(6) as relationalStore.ColumnType;
  let assetsDataType = await (resultSet as relationalStore.ResultSet).getColumnType(7) as relationalStore.ColumnType;
  let floatArrayType = await (resultSet as relationalStore.ResultSet).getColumnType(8) as relationalStore.ColumnType;
}
```

```TypeScript
async function getColumnTypeExample(store : relationalStore.RdbStore){
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      // 方式一：通过列名获取列数据类型
      let idType = await resultSet.getColumnType("ID");
      let nameType = await resultSet.getColumnType("NAME");
      let ageType = await resultSet.getColumnType("AGE");
      let salaryType = await resultSet.getColumnType("SALARY");
      let codesType = await resultSet.getColumnType("CODES");
      // 方式二：通过列索引获取列数据类型
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

根据指定的列索引或列名称获取列数据类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIdentifier | number \| string | 是 | 表示结果集中指定列的索引或名称，索引从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColumnType](arkts-arkdata-relationalstore-columntype-e.md) | 返回指定列的数据类型。当结果集中包含重名列时，通过列名获取的结果会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
if (resultSet != undefined) {
  let idType = (resultSet as relationalStore.ResultSet).getColumnTypeSync("ID") as relationalStore.ColumnType;
  let nameType = (resultSet as relationalStore.ResultSet).getColumnTypeSync("NAME") as relationalStore.ColumnType;
  let ageType = (resultSet as relationalStore.ResultSet).getColumnTypeSync("AGE") as relationalStore.ColumnType;
  let salaryType = (resultSet as relationalStore.ResultSet).getColumnTypeSync("SALARY") as relationalStore.ColumnType;
  let codesType = (resultSet as relationalStore.ResultSet).getColumnTypeSync("CODES") as relationalStore.ColumnType;
  let identityType = (resultSet as relationalStore.ResultSet).getColumnTypeSync(5) as relationalStore.ColumnType;
  let assetDataType = (resultSet as relationalStore.ResultSet).getColumnTypeSync(6) as relationalStore.ColumnType;
  let assetsDataType = (resultSet as relationalStore.ResultSet).getColumnTypeSync(7) as relationalStore.ColumnType;
  let floatArrayType = (resultSet as relationalStore.ResultSet).getColumnTypeSync(8) as relationalStore.ColumnType;
}
```

```TypeScript
async function getColumnTypeSyncExample(store : relationalStore.RdbStore){
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    if (resultSet != undefined) {
      resultSet.goToNextRow();
      // 方式一：通过列名获取列数据类型
      let idType = resultSet.getColumnTypeSync("ID");
      let nameType = resultSet.getColumnTypeSync("NAME");
      let ageType = resultSet.getColumnTypeSync("AGE");
      let salaryType = resultSet.getColumnTypeSync("SALARY");
      let codesType = resultSet.getColumnTypeSync("CODES");
      // 方式二：通过列索引获取列数据类型
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

获取当前行所有列的值。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RowData](arkts-arkdata-relationalstore-rowdata-t.md) | 返回当前行所有列的值。支持获取包含重名列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
try {
  // 联表查询EMPLOYEE1和EMPLOYEE2，并获取当前行包含重名列名的值。store为获取到的RdbStore实例。
  let resultSet: relationalStore.ResultSet = await store.querySql("SELECT e1.NAME, e2.NAME, e1.AGE, e2.AGE FROM EMPLOYEE1 e1 LEFT JOIN EMPLOYEE2 e2 ON e1.SALARY=e2.SALARY");
  if (resultSet != undefined) {
    resultSet.goToFirstRow();
    const rowData = resultSet.getCurrentRowData();
    resultSet.close();
  }
} catch (err) {
  console.error(`Failed to get row data: code:${err.code}, message:${err.message}`);
}
```

```TypeScript
async function getCurrentRowDataExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    // 联表查询EMPLOYEE1和EMPLOYEE2，并获取当前行包含重名列名的值。store为获取到的RdbStore实例。
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

以double形式获取当前行中指定列的值。如果当前列的数据类型为INTEGER、DOUBLE、TEXT会转成double类型返回指定值，非数字的TEXT、BLOB类型会返回0.0。如果该列内容为空时，会返回0.0。如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 以double形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |

**示例**

```TypeScript
if (resultSet !== undefined) {
  while (resultSet.goToNextRow()) {
    const colIndex = resultSet.getColumnIndex("SALARY");
    if (colIndex > -1) {
      const salary = resultSet.getDouble(colIndex);
      console.info(`Get double success, salary is ${salary}`);
    }
  }
}
```

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

以Long形式获取当前行中指定列的值。如果当前列的数据类型为INTEGER、DOUBLE、TEXT会转成Long类型返回指定值，非数字的TEXT、BLOB类型会返回0。如果该列内容为空时，会返回0。如果当前列的数据类型为INTEGER，值大于Number.MAX_SAFE_INTEGER 或小于Number.MIN_SAFE_INTEGER时，如果不希望丢失精度，建议使用 [getString](#getstring)接口获取。如果当前列的数据类型为DOUBLE时，如果不希望丢失精度，建议使用[getDouble](#getdouble)接口获取。如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 以Long形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |

**示例**

```TypeScript
if (resultSet !== undefined) {
  while (resultSet.goToNextRow()) {
    const colIndex = resultSet.getColumnIndex("AGE");
    if (colIndex > -1) {
      const age = resultSet.getLong(colIndex);
      console.info(`Get long success, age is ${age}`);
    }
  }
}
```

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

获取当前行的数据。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValuesBucket | 返回指定行的值。当结果集中包含重名列时，返回值会不符合预期，建议使用 [getCurrentRowData]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

**示例**

```TypeScript
if (resultSet != undefined) {
  const row = (resultSet as relationalStore.ResultSet).getRow();
}
```

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

从结果集中获取指定数量的数据，使用Promise异步回调。禁止与[LiteResultSet](#literesultset)的其他接口并发调用，否则获取的数据可能非预期。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxCount | number | 是 | 正整数，指定要从结果集中获取数据的条数。 |
| position | number | 否 | 非负整数，指定从结果集中获取数据的起始位置，不填则从结果集的当前行（默认首次获取数据时为当前结果集的第一行）开始获取数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Array & lt;ValuesBucket & gt; & gt; | 返回maxCount条数据，剩余数据不足maxCount条则返回剩余数据，返回空数组时代表已经遍历到结果集的末尾。当结果集中包含重名列时，返回 值会不符合预期，建议使用[getRowsData]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |

**示例**

```TypeScript
// 以查到100条数据为例
async function processRows(resultSet: relationalStore.ResultSet) {
  // 示例1：仅指定maxCount
  if (resultSet != undefined) {
    let rows: Array<relationalStore.ValuesBucket>;
    let maxCount: number = 50;
    // 从结果集的当前行（默认首次获取数据时为当前结果集的第一行，后续为上次获取数据结束位置的下一行）开始获取数据
    // getRows会自动移动结果集当前行到上次getRows获取结束位置的下一行，无需使用goToFirstRow、goToNextRow等接口移动
    while ((rows = await (resultSet as relationalStore.ResultSet).getRows(maxCount)).length != 0) {
      console.info(JSON.stringify(rows[0]));
    }
  }

  // 示例2：指定maxCount和起始的position
  if (resultSet != undefined) {
    let rows: Array<relationalStore.ValuesBucket>;
    let maxCount: number = 50;
    let position: number = 50;
    while ((rows = await (resultSet as relationalStore.ResultSet).getRows(maxCount, position)).length != 0) {
      console.info(JSON.stringify(rows[0]));
      position += rows.length;
    }
  }
}
```

```TypeScript
async function getRowsExample(store : relationalStore.RdbStore) {
  // 以查到100条数据为例
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    resultSet = await store.querySqlWithoutRowCount('select * from EMPLOYEE where name = ?', ["Rose"]);
    // 示例1：仅指定maxCount
    if (resultSet != undefined) {
      let rows: Array<relationalStore.ValuesBucket>;
      let maxCount: number = 50;
      // 从结果集的当前行（默认首次获取数据时为当前结果集的第一行，后续为上次获取数据结束位置的下一行）开始获取数据
      // getRows会自动移动结果集当前行到上次getRows获取结束位置的下一行，goToNextRow等接口移动
      while ((rows = await resultSet.getRows(maxCount)).length != 0) {
        console.info(JSON.stringify(rows[0]));
      }
    }
  
    // 示例2：指定maxCount和起始的position
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

从指定位置position开始，最多获取maxCount行数据。使用Promise异步回调。禁止与[LiteResultSet](#literesultset)的其他接口并发调用，否则 获取的数据可能非预期。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxCount | number | 是 | 正整数，指定从结果集中获取数据的条数。不为正整数则参数非法，抛出错误码14800001。 |
| position | number | 否 | 非负整数，指定从结果集中获取数据的起始位置，不填则从结果集的当前行（默认首次获取数据时为当前结果集的第一行）开始获取数据。不为非负整数则参数非法，抛出错误码1480000 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RowsData](arkts-arkdata-relationalstore-rowsdata-t.md)&gt; | 返回maxCount条数据，剩余数据不足maxCount条则返回剩余数据，返回空数组时代表已经遍历到结果集的末尾。支持获取包含重名列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |

**示例**

```TypeScript
try {
  // 联表查询EMPLOYEE1和EMPLOYEE2，并获取多行包含重名列名的值。store为获取到的RdbStore实例。
  let resultSet: relationalStore.ResultSet = await store.querySql("SELECT e1.NAME, e2.NAME, e1.AGE, e2.AGE FROM EMPLOYEE1 e1 LEFT JOIN EMPLOYEE2 e2 ON e1.SALARY=e2.SALARY");
  // 以查到50条数据为例
  // 示例1：仅指定maxCount
  if (resultSet != undefined) {
    let rowsData: relationalStore.RowsData;
    // 从结果集的当前行（默认首次获取数据时为当前结果集的第一行，后续为上次获取数据结束位置的下一行）开始获取数据
    // getRowsData会自动移动结果集当前行到上次getRowsData获取结束位置的下一行，无需使用goToFirstRow、goToNextRow等接口移动
    let maxCount: number = 50;
    let rowCount: number = 0;
    while ((rowsData = await resultSet.getRowsData(maxCount)).length != 0) {
      rowsData.forEach((rowData, index) => {
        // 第rowCount + index + 1行的查询结果
        console.info(`${rowCount + index + 1}：${rowData}`);
      });
      rowCount += rowsData.length;
    }
  }

  // 示例2：指定maxCount和起始的position
  if (resultSet != undefined) {
    let rowsData: relationalStore.RowsData;
    let maxCount: number = 50;
    let position: number = 50;
    while ((rowsData = await resultSet.getRowsData(maxCount, position)).length != 0) {
      rowsData.forEach((rowData, index) => {
        // 第position + index + 1行的查询结果
        console.info(`${position + index + 1}：${rowData}`);
      });
      position += rowsData.length;
    }
  }
  resultSet.close();
} catch (err) {
  console.error(`Failed to get rows data: code:${err.code}, message:${err.message}`);
}
```

```TypeScript
async function getRowsDataExample(store : relationalStore.RdbStore) {
  try {
    let resultSet: relationalStore.LiteResultSet | undefined;
    // 联表查询EMPLOYEE1和EMPLOYEE2，并获取多行包含重名列名的值。store为获取到的RdbStore实例。
    resultSet = await store.querySqlWithoutRowCount("SELECT e1.NAME, e2.NAME, e1.AGE, e2.AGE FROM EMPLOYEE1 e1 LEFT JOIN EMPLOYEE2 e2 ON e1.SALARY=e2.SALARY");
    // 以查到50条数据为例
    // 示例1：仅指定maxCount
    if (resultSet != undefined) {
      let rowsData: relationalStore.RowsData;
      // 从结果集的当前行（默认首次获取数据时为当前结果集的第一行，后续为上次获取数据结束位置的下一行）开始获取数据
      // getRowsData会自动移动结果集当前行到上次getRowsData获取结束位置的下一行，无需使用goToNextRow接口移动
      let maxCount: number = 50;
      let rowCount: number = 0;
      while ((rowsData = await resultSet.getRowsData(maxCount)).length != 0) {
        rowsData.forEach((rowData, index) => {
          // 第rowCount + index + 1行的查询结果
          console.info(`${rowCount + index + 1}：${rowData}`);
        });
        rowCount += rowsData.length;
      }
    }
  
    // 示例2：指定maxCount和起始的position
    if (resultSet != undefined) {
      let rowsData: relationalStore.RowsData;
      let maxCount: number = 50;
      let position: number = 50;
      while ((rowsData = await resultSet.getRowsData(maxCount, position)).length != 0) {
        rowsData.forEach((rowData, index) => {
          // 第position + index + 1行的查询结果
          console.info(`${position + index + 1}：${rowData}`);
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

以字符串形式获取当前行中指定列的值。如果当前列中的值为INTEGER、DOUBLE、TEXT、BLOB类型，会以字符串形式返回指定值；如果该列内容为空，则会返回空字符串""。如果当前列中的值为DOUBLE类型，可能存在精度的丢失，建议使用[getDouble](#getdouble)接口获取。如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以字符串形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |

**示例**

```TypeScript
if (resultSet != undefined) {
  const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
}
```

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

获取当前行中指定列的值。如果值类型为INTEGER，值大于Number.MAX_SAFE_INTEGER或小于Number.MIN_SAFE_INTEGER时，如果不希望丢失精度，建议使用 [getString](#getstring)接口获取。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValueType | 允许返回的数据字段类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

**示例**

```TypeScript
if (resultSet !== undefined) {
  while (resultSet.goToNextRow()) {
    const colIndex = resultSet.getColumnIndex("NAME");
    if (colIndex > -1) {
      const name = resultSet.getValue(colIndex);
      console.info(`Get value success, name is ${name}`);
    }
  }
}
```

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

移动结果集到下一行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集到下一行，返回true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |

**示例**

```TypeScript
if (resultSet != undefined) {
  (resultSet as relationalStore.ResultSet).goToNextRow();
}
```

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

检查当前行中指定列的值是否为null。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果当前行中指定列的值为null，则返回true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file |

**示例**

```TypeScript
if (resultSet !== undefined) {
  while (resultSet.goToNextRow()) {
    const colIndex = resultSet.getColumnIndex("CODES");
    if (colIndex > -1) {
      const isColumnNull = resultSet.isColumnNull(colIndex);
      console.info(`Column is null: ${isColumnNull}`);
    }
  }
}
```

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
