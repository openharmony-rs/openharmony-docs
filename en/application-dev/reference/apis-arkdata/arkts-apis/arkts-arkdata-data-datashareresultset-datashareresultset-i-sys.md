# DataShareResultSet (System API)

Provides APIs for accessing the result sets returned.

The column or key names are returned as a string array, in which the strings are in the same order as the columns or keys in the result set.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { DataShareResultSet, DataType } from '@kit.ArkData';
```

## close

```TypeScript
close(): void
```

Closes this result set.

Calling this API will invalidate the result set and release all its resources.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Examples**

```TypeScript
if (resultSet != undefined) {
  (resultSet as DataShareResultSet).close();
}
```

## getBlob

```TypeScript
getBlob(columnIndex: number): Uint8Array
```

Obtains the value in the form of a byte array based on the specified column and the current row.

If the specified column or key is empty or the value is not of the Blob type, you need to determine whether to throw an exception.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Value obtained. |

**Examples**

```TypeScript
let columnIndex = 1;
if (resultSet != undefined) {
  let goToFirstRow = (resultSet as DataShareResultSet).goToFirstRow();
  if (!goToFirstRow) {
    console.error("failed to go to first row");
  } else {
    let getBlob = (resultSet as DataShareResultSet).getBlob(columnIndex);
    console.info('resultSet.getBlob: ' + getBlob);
  }
}
```

## getColumnIndex

```TypeScript
getColumnIndex(columnName: string): number
```

Obtains the column index based on a column name.

The column name is passed in as an input parameter.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnName | string | Yes | Column name. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Column index obtained. |

**Examples**

```TypeScript
let columnName = "name";
if (resultSet != undefined) {
  let getColumnIndex = (resultSet as DataShareResultSet).getColumnIndex(columnName);
  console.info('resultSet.getColumnIndex: ' + getColumnIndex);
}
```

## getColumnName

```TypeScript
getColumnName(columnIndex: number): string
```

Obtains the column name based on a column index.

The column index is passed in as an input parameter.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Column index. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Column name obtained. |

**Examples**

```TypeScript
let columnIndex = 1;
if (resultSet != undefined) {
  let getColumnName = (resultSet as DataShareResultSet).getColumnName(columnIndex);
  console.info('resultSet.getColumnName: ' + getColumnName);
}
```

## getDataType

```TypeScript
getDataType(columnIndex: number): DataType
```

Obtains the data type based on the specified column index.

If the specified column or key is empty or the value is not of the DataType type, you need to determine whether to throw an exception.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Column index. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataType](arkts-arkdata-data-datashareresultset-datatype-e-sys.md) | Data type obtained. |

**Examples**

```TypeScript
let columnIndex = 1;
if (resultSet != undefined) {
  let goToFirstRow = (resultSet as DataShareResultSet).goToFirstRow();
  if (!goToFirstRow) {
    console.error("failed to go to first row");
  } else {
    let getDataType = (resultSet as DataShareResultSet).getDataType(columnIndex);
    console.info('resultSet.getDataType: ' + getDataType);
  }
}
```

## getDouble

```TypeScript
getDouble(columnIndex: number): number
```

Obtains the value in the form of a double-precision floating-point number based on the specified column and the current row.

If the specified column or key is empty or the value is not of the double type, you need to determine whether to throw an exception.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value obtained. |

**Examples**

```TypeScript
let columnIndex = 1;
if (resultSet != undefined) {
  let goToFirstRow = (resultSet as DataShareResultSet).goToFirstRow();
  if (!goToFirstRow) {
    console.error("failed to go to first row");
  } else {
    let getDouble = (resultSet as DataShareResultSet).getDouble(columnIndex);
    console.info('resultSet.getDouble: ' + getDouble);
  }
}
```

## getLong

```TypeScript
getLong(columnIndex: number): number
```

Obtains the value in the form of a long integer based on the specified column and the current row.

If the specified column or key is empty or the value is not of the long type, you need to determine whether to throw an exception.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value obtained. |

**Examples**

```TypeScript
let columnIndex = 1;
if (resultSet != undefined) {
  let goToFirstRow = (resultSet as DataShareResultSet).goToFirstRow();
  if (!goToFirstRow) {
    console.error("failed to go to first row");
  } else {
    let getLong = (resultSet as DataShareResultSet).getLong(columnIndex);
    console.info('resultSet.getLong: ' + getLong);
  }
}
```

## getString

```TypeScript
getString(columnIndex: number): string
```

Obtains the value in the form of a string based on the specified column and the current row.

If the specified column or key is empty or the value is not of the string type, you need to determine whether to throw an exception.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the target column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value obtained. |

**Examples**

```TypeScript
let columnIndex = 1;
if (resultSet != undefined) {
  let goToFirstRow = (resultSet as DataShareResultSet).goToFirstRow();
  if (!goToFirstRow) {
    console.error("failed to go to first row");
  } else {
    let getString = (resultSet as DataShareResultSet).getString(columnIndex);
    console.info('resultSet.getString: ' + getString);
  }
}
```

## goTo

```TypeScript
goTo(offset: number): boolean
```

Moves based on the specified offset.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset relative to the current position. A negative value means to move forward, and a positive value means to move backward. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let goToNum = 1;
if (resultSet != undefined) {
  let isGoTo = (resultSet as DataShareResultSet).goTo(goToNum);
  console.info('resultSet.goTo: ' + isGoTo);
}
```

## goToFirstRow

```TypeScript
goToFirstRow(): boolean
```

Moves to the first row of the result set.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
// Create a resultSet object. For details, see Usage in this topic.
if (resultSet != undefined) {
  let isGoToFirstRow = (resultSet as DataShareResultSet).goToFirstRow();
  console.info('resultSet.goToFirstRow: ' + isGoToFirstRow);
}
```

## goToLastRow

```TypeScript
goToLastRow(): boolean
```

Moves to the last row of the result set.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
if (resultSet != undefined) {
  let isGoToLastRow = (resultSet as DataShareResultSet).goToLastRow();
  console.info('resultSet.goToLastRow: ' + isGoToLastRow);
}
```

## goToNextRow

```TypeScript
goToNextRow(): boolean
```

Moves to the next row in the result set.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
if (resultSet != undefined) {
  let isGoToNextRow = (resultSet as DataShareResultSet).goToNextRow();
  console.info('resultSet.goToNextRow: ' + isGoToNextRow);
}
```

## goToPreviousRow

```TypeScript
goToPreviousRow(): boolean
```

Moves to the previous row in the result set.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
if (resultSet != undefined) {
  let isGoToPreviousRow = (resultSet as DataShareResultSet).goToPreviousRow();
  console.info('resultSet.goToPreviousRow: ' + isGoToPreviousRow);
}
```

## goToRow

```TypeScript
goToRow(position: number): boolean
```

Moves to the specified row in the result set.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Position to move to, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let goToRowNum = 2;
if (resultSet != undefined) {
  let isGoToRow = (resultSet as DataShareResultSet).goToRow(goToRowNum);
  console.info('resultSet.goToRow: ' + isGoToRow);
}
```

## columnCount

```TypeScript
columnCount: number
```

Number of columns in the result set.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

## columnNames

```TypeScript
columnNames: Array<string>
```

Names of all columns in the result set.

**Type:** Array&lt;string&gt;

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

## isClosed

```TypeScript
isClosed: boolean
```

Whether the result set is closed. The value **true** means the result set is closed; the value **false** means the opposite.

**Type:** boolean

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

## rowCount

```TypeScript
rowCount: number
```

Number of rows in the result set.

**Type:** number

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.
