# LiteResultSet

提供查询数据库后生成的结果集的访问方法。结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。 LiteResultSet实例不会实时刷新。使用结果集后，如果数据库中的数据发生变化（如增删改操作），需要重新查询才能获取到最新的数据。 下列API示例中，都需先使用[queryWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querywithoutrowcount)、 [querySqlWithoutRowCount](arkts-arkdata-relationalstore-rdbstore-i.md#querysqlwithoutrowcount)等query类方法中任一方法获取到LiteResultSet实例，再 通过此实例调用对应方法。 > **说明：** > > - 本class首批接口从API version 23开始支持。

**起始版本：** 23

<!--Device-relationalStore-class LiteResultSet--><!--Device-relationalStore-class LiteResultSet-End-->

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

<!--Device-LiteResultSet-close(): void--><!--Device-LiteResultSet-close(): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## getAsset

```TypeScript
getAsset(columnIndex: int): Asset
```

以[Asset](arkts-arkdata-relationalstore-asset-i.md)形式获取当前行中指定列的值。 如果当前列的数据类型为Asset类型，会以Asset类型返回指定值；如果当前列中的值为null时，会返回null；如果当前列的数据类型非Asset类型，则返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getAsset(columnIndex: int): Asset--><!--Device-LiteResultSet-getAsset(columnIndex: int): Asset-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Asset | 以Asset形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## getAssets

```TypeScript
getAssets(columnIndex: int): Assets
```

以[Assets](arkts-arkdata-relationalstore-assets-t.md)形式获取当前行中指定列的值。 如果当前列的数据类型为Assets类型，会以Assets类型返回指定值；如果当前列中的值为null时，会返回null；如果当前列的数据类型非Assets类型，则返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getAssets(columnIndex: int): Assets--><!--Device-LiteResultSet-getAssets(columnIndex: int): Assets-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Assets | 以Assets形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## getBlob

```TypeScript
getBlob(columnIndex: int): Uint8Array
```

以字节数组的形式获取当前行中指定列的值。 如果当前列的数据类型为INTEGER、DOUBLE、TEXT、BLOB类型，会转成字节数组类型返回指定值，如果该列内容为空时，会返回空字节数组。 如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会抛出错误码14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getBlob(columnIndex: int): Uint8Array--><!--Device-LiteResultSet-getBlob(columnIndex: int): Uint8Array-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 以字节数组的形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## getColumnIndex

```TypeScript
getColumnIndex(columnName: string): int
```

根据指定的列名获取列索引。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getColumnIndex(columnName: string): int--><!--Device-LiteResultSet-getColumnIndex(columnName: string): int-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnName | string | 是 | 表示结果集中指定列的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| int | 返回指定列的索引。当结果集中包含重名列时，返回值会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getColumnName

```TypeScript
getColumnName(columnIndex: int): string
```

根据指定的列索引获取列名。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getColumnName(columnIndex: int): string--><!--Device-LiteResultSet-getColumnName(columnIndex: int): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 表示结果集中指定列的索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定列的名称。当结果集中包含重名列时，返回值会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getColumnNames

```TypeScript
getColumnNames(): Array<string>
```

获取结果集中所有列的名称。 列名以字符串数组的形式返回，数组中字符串的顺序与结果集中列的顺序一致。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getColumnNames(): Array<string>--><!--Device-LiteResultSet-getColumnNames(): Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;string&gt; | 返回结果集中所有列的名称。支持获取包含重名列的列名。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getColumnType

```TypeScript
getColumnType(columnIdentifier: int | string): Promise<ColumnType>
```

根据指定的列索引或列名称获取列数据类型，使用Promise异步回调。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getColumnType(columnIdentifier: int | string): Promise<ColumnType>--><!--Device-LiteResultSet-getColumnType(columnIdentifier: int | string): Promise<ColumnType>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIdentifier | int \| string | 是 | 表示结果集中指定列的索引或名称，索引从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[ColumnType](arkts-arkdata-relationalstore-columntype-e.md)&gt; | Promise对象。返回指定列的数据类型。当结果集中包含重名列时，通过列名获取的结果会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getColumnTypeSync

```TypeScript
getColumnTypeSync(columnIdentifier: int | string): ColumnType
```

根据指定的列索引或列名称获取列数据类型。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getColumnTypeSync(columnIdentifier: int | string): ColumnType--><!--Device-LiteResultSet-getColumnTypeSync(columnIdentifier: int | string): ColumnType-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIdentifier | int \| string | 是 | 表示结果集中指定列的索引或名称，索引从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ColumnType](arkts-arkdata-relationalstore-columntype-e.md) | 返回指定列的数据类型。当结果集中包含重名列时，通过列名获取的结果会不符合预期。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getCurrentRowData

```TypeScript
getCurrentRowData(): RowData
```

获取当前行所有列的值。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getCurrentRowData(): RowData--><!--Device-LiteResultSet-getCurrentRowData(): RowData-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RowData](arkts-arkdata-relationalstore-rowdata-t.md) | 返回当前行所有列的值。支持获取包含重名列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getDouble

```TypeScript
getDouble(columnIndex: int): double
```

以double形式获取当前行中指定列的值。 如果当前列的数据类型为INTEGER、DOUBLE、TEXT会转成double类型返回指定值，非数字的TEXT、BLOB类型会返回0.0。如果该列内容为空时，会返回0.0。 如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getDouble(columnIndex: int): double--><!--Device-LiteResultSet-getDouble(columnIndex: int): double-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| double | 以double形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## getLong

```TypeScript
getLong(columnIndex: int): long
```

以Long形式获取当前行中指定列的值。 如果当前列的数据类型为INTEGER、DOUBLE、TEXT会转成Long类型返回指定值，非数字的TEXT、BLOB类型会返回0。如果该列内容为空时，会返回0。 如果当前列的数据类型为INTEGER，值大于Number.MAX_SAFE_INTEGER 或小于Number.MIN_SAFE_INTEGER时，如果不希望丢失精度，建议使用 [getString](#getstring)接口获取。 如果当前列的数据类型为DOUBLE时，如果不希望丢失精度，建议使用[getDouble](#getdouble)接口获取。 如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getLong(columnIndex: int): long--><!--Device-LiteResultSet-getLong(columnIndex: int): long-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 以Long形式返回指定列的值。 <br>该接口支持的精度范围是：Number.MIN_SAFE_INTEGER ~ Number.MAX_SAFE_INTEGER，若超出该范围，建议对于DOUBLE类型的值使用 [getDouble]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## getRow

```TypeScript
getRow(): ValuesBucket
```

获取当前行的数据。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getRow(): ValuesBucket--><!--Device-LiteResultSet-getRow(): ValuesBucket-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValuesBucket | 返回指定行的值。当结果集中包含重名列时，返回值会不符合预期，建议使用 [getCurrentRowData]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getRows

```TypeScript
getRows(maxCount: int, position?: int): Promise<Array<ValuesBucket>>
```

从结果集中获取指定数量的数据，使用Promise异步回调。禁止与[LiteResultSet](#literesultset)的其他接口并发调用，否则获取的数据可能非预期。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getRows(maxCount: int, position?: int): Promise<Array<ValuesBucket>>--><!--Device-LiteResultSet-getRows(maxCount: int, position?: int): Promise<Array<ValuesBucket>>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxCount | int | 是 | 正整数，指定要从结果集中获取数据的条数。 |
| position | int | 否 | 非负整数，指定从结果集中获取数据的起始位置，不填则从结果集的当前行（默认首次获取数据时为当前结果集的第一行）开始获取数据。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;ValuesBucket&gt;&gt; | 返回maxCount条数据，剩余数据不足maxCount条则返回剩余数据，返回空数组时代表已经遍历到结果集的末尾。当结果集中包含重名列时，返回 值会不符合预期，建议使用[getRowsData]{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getRowsData

```TypeScript
getRowsData(maxCount: int, position?: int): Promise<RowsData>
```

从指定位置position开始，最多获取maxCount行数据。使用Promise异步回调。禁止与[LiteResultSet](#literesultset)的其他接口并发调用，否则 获取的数据可能非预期。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getRowsData(maxCount: int, position?: int): Promise<RowsData>--><!--Device-LiteResultSet-getRowsData(maxCount: int, position?: int): Promise<RowsData>-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| maxCount | int | 是 | 正整数，指定从结果集中获取数据的条数。不为正整数则参数非法，抛出错误码14800001。 |
| position | int | 否 | 非负整数，指定从结果集中获取数据的起始位置，不填则从结果集的当前行（默认首次获取数据时为当前结果集的第一行）开始获取数据。不为非负整数则参数非法，抛出错误码1480000 1。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[RowsData](arkts-arkdata-relationalstore-rowsdata-t.md)&gt; | 返回maxCount条数据，剩余数据不足maxCount条则返回剩余数据，返回空数组时代表已经遍历到结果集的末尾。支持获取包含重名列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## getString

```TypeScript
getString(columnIndex: int): string
```

以字符串形式获取当前行中指定列的值。 如果当前列中的值为INTEGER、DOUBLE、TEXT、BLOB类型，会以字符串形式返回指定值；如果该列内容为空，则会返回空字符串""。 如果当前列中的值为DOUBLE类型，可能存在精度的丢失，建议使用[getDouble](#getdouble)接口获取。 如果当前列的数据类型为ASSET、ASSETS、FLOATVECTOR、BIGINT类型，会返回14800041。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getString(columnIndex: int): string--><!--Device-LiteResultSet-getString(columnIndex: int): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以字符串形式返回指定列的值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800041](../errorcode-data-rdb.md#14800041-类型转换失败) | Type conversion failed. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## getValue

```TypeScript
getValue(columnIndex: int): ValueType
```

获取当前行中指定列的值。 如果值类型为INTEGER，值大于Number.MAX_SAFE_INTEGER或小于Number.MIN_SAFE_INTEGER时，如果不希望丢失精度，建议使用 [getString](#getstring)接口获取。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-getValue(columnIndex: int): ValueType--><!--Device-LiteResultSet-getValue(columnIndex: int): ValueType-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValueType | 允许返回的数据字段类型。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |

## goToNextRow

```TypeScript
goToNextRow(): boolean
```

移动结果集到下一行。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-goToNextRow(): boolean--><!--Device-LiteResultSet-goToNextRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集到下一行，返回true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800031](../errorcode-data-rdb.md#14800031-sqlitetext或blob超出大小限制) | SQLite: TEXT or BLOB exceeds size limit. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file. |

## isColumnNull

```TypeScript
isColumnNull(columnIndex: int): boolean
```

检查当前行中指定列的值是否为null。

**起始版本：** 23

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-LiteResultSet-isColumnNull(columnIndex: int): boolean--><!--Device-LiteResultSet-isColumnNull(columnIndex: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | int | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果当前行中指定列的值为null，则返回true；否则返回false。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [14800001](../errorcode-data-rdb.md#14800001-无效的参数) | Invalid arguments. Possible causes: 1. Parameter is out of valid range. |
| [14800019](../errorcode-data-rdb.md#14800019-sql必须是查询语句) | The SQL must be a query statement. |
| [14800021](../errorcode-data-rdb.md#14800021-sqlite通用错误) | SQLite: Generic error. |
| [14800011](../errorcode-data-rdb.md#14800011-数据库文件异常) | The current operation failed because the database is corrupted. |
| [14800026](../errorcode-data-rdb.md#14800026-sqlite数据库内存不足) | SQLite: The database is out of memory. |
| [14800013](../errorcode-data-rdb.md#14800013-列索引越界) | Column index is out of bounds. |
| [14800012](../errorcode-data-rdb.md#14800012-结果集为空或指针索引越界) | ResultSet is empty or pointer index is out of bounds. |
| [14800028](../errorcode-data-rdb.md#14800028-sqlite发生了某种磁盘io错误) | SQLite: Some kind of disk I/O error occurred. |
| [14800014](../errorcode-data-rdb.md#14800014-目标实例已关闭) | The target instance is already closed. |
| [14800030](../errorcode-data-rdb.md#14800030-sqlite无法打开数据库文件) | SQLite: Unable to open the database file |

