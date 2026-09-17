# LiteResultSet

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

## getFloat32Array

```TypeScript
getFloat32Array(columnIndex: number): Float32Array
```

Obtains the value of the specified column in the current row as a float array. The implementation class determines whether to throw an exception if the value of the specified column in the current row is null or the specified column is not of the float array type.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Indicates the specified column index, which starts from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Float32Array | The value of the specified column as a float array. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [14800012](../errorcode-data-rdb.md#14800012-result-set-is-empty-or-pointer-index-is-out-of-bounds) | ResultSet is empty or pointer index is out of bounds. |
| [14800013](../errorcode-data-rdb.md#14800013-column-index-out-of-range) | Column index is out of bounds. |
| [14800014](../errorcode-data-rdb.md#14800014-target-instance-closed) | The target instance is already closed. |
| [14800041](../errorcode-data-rdb.md#14800041-type-conversion-failure) | Type conversion failed. |
