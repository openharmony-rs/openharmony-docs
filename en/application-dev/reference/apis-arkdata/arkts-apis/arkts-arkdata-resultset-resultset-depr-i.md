# ResultSet

A result set is a set of results returned after the relational database (RDB) query APIs are called. You can use the **resultset** APIs to obtain required data.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [relationalStore](arkts-arkdata-data-relationalstore.md)

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## close

```TypeScript
close(): void
```

Closes this result set.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** close

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Examples**

```TypeScript
let predicatesClose = new dataRdb.RdbPredicates("EMPLOYEE");
let promiseClose = rdbStore.query(predicatesClose, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
promiseClose.then((resultSet) => {
  resultSet.close();
}).catch((err) => {
  console.error('resultset close failed');
});
```

## getBlob

```TypeScript
getBlob(columnIndex: number): Uint8Array
```

Obtains the value from the specified column in the current row as a byte array.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getBlob

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the specified column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Uint8Array | Value in the specified column as a byte array. |

**Examples**

```TypeScript
const codes = resultSet.getBlob(resultSet.getColumnIndex("CODES"));
```

## getColumnIndex

```TypeScript
getColumnIndex(columnName: string): number
```

Obtains the column index based on the column name.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getColumnIndex

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnName | string | Yes | Column name specified. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Index of the column obtained. |

**Examples**

```TypeScript
const success = resultSet.goToFirstRow();
if (success) {
  const id = resultSet.getLong(resultSet.getColumnIndex("ID"));
  const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
  const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
  const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
}
```

## getColumnName

```TypeScript
getColumnName(columnIndex: number): string
```

Obtains the column name based on the column index.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getColumnName

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Column index specified. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Column name obtained. |

**Examples**

```TypeScript
const id = resultSet.getColumnName(0);
const name = resultSet.getColumnName(1);
const age = resultSet.getColumnName(2);
```

## getDouble

```TypeScript
getDouble(columnIndex: number): number
```

Obtains the value from the specified column in the current row as a Double.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getDouble

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the specified column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value in the specified column as a Double. |

**Examples**

```TypeScript
const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
```

## getLong

```TypeScript
getLong(columnIndex: number): number
```

Obtains the value from the specified column in the current row as a Long.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getLong

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the specified column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Value in the specified column as a Long. <br>The value range supported by this API is **Number.MIN_SAFE_INTEGER** to **Number.MAX_SAFE_INTEGER**. If the value is out of this range, use [getDouble](#getdouble). |

**Examples**

```TypeScript
const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
```

## getString

```TypeScript
getString(columnIndex: number): string
```

Obtains the value from the specified column in the current row as a string.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getString

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the specified column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| string | Value in the specified column as a string. |

**Examples**

```TypeScript
const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
```

## goTo

```TypeScript
goTo(offset: number): boolean
```

Moves the result set forward or backward to the specified row with an offset relative to the current position.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** goTo

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| offset | number | Yes | Offset relative to the current position. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let predicatesgoto = new dataRdb.RdbPredicates("EMPLOYEE");
let promisequerygoto = rdbStore.query(predicatesgoto, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
promisequerygoto.then((resultSet) => {
  resultSet.goTo(1);
  resultSet.close();
}).catch((err) => {
  console.error('query failed');
});
```

## goToFirstRow

```TypeScript
goToFirstRow(): boolean
```

Moves the cursor to the first row of the result set.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** goToFirstRow

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let predicatesgoFirst = new dataRdb.RdbPredicates("EMPLOYEE");
let promisequerygoFirst = rdbStore.query(predicatesgoFirst, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
promisequerygoFirst.then((resultSet) => {
  resultSet.goToFirstRow();
  resultSet.close();
}).catch((err) => {
  console.error('query failed');
});
```

## goToLastRow

```TypeScript
goToLastRow(): boolean
```

Moves the cursor to the last row of the result set.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** goToLastRow

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let predicatesgoLast = new dataRdb.RdbPredicates("EMPLOYEE");
let promisequerygoLast = rdbStore.query(predicatesgoLast, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
promisequerygoLast.then((resultSet) => {
  resultSet.goToLastRow();
  resultSet.close();
}).catch((err) => {
  console.error('query failed');
});
```

## goToNextRow

```TypeScript
goToNextRow(): boolean
```

Moves the cursor to the next row in the result set.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** goToNextRow

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let predicatesgoNext = new dataRdb.RdbPredicates("EMPLOYEE");
let promisequerygoNext = rdbStore.query(predicatesgoNext, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
promisequerygoNext.then((resultSet) => {
  resultSet.goToNextRow();
  resultSet.close();
}).catch((err) => {
  console.error('query failed');
});
```

## goToPreviousRow

```TypeScript
goToPreviousRow(): boolean
```

Moves the cursor to the previous row in the result set.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** goToPreviousRow

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let predicatesgoPrev = new dataRdb.RdbPredicates("EMPLOYEE");
let promisequerygoPrev = rdbStore.query(predicatesgoPrev, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
promisequerygoPrev.then((resultSet) => {
  resultSet.goToPreviousRow();
  resultSet.close();
}).catch((err) => {
  console.error('query failed');
});
```

## goToRow

```TypeScript
goToRow(position: number): boolean
```

Moves the cursor to the specified row in the result set.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** goToRow

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| position | number | Yes | Position to which the cursor is to be moved. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |

**Examples**

```TypeScript
let predicatesgotorow = new dataRdb.RdbPredicates("EMPLOYEE");
let promisequerygotorow = rdbStore.query(predicatesgotorow, ["ID", "NAME", "AGE", "SALARY", "CODES"]);
promisequerygotorow.then((resultSet) => {
  resultSet.goToRow(5);
  resultSet.close();
}).catch((err) => {
  console.error('query failed');
});
```

## isColumnNull

```TypeScript
isColumnNull(columnIndex: number): boolean
```

Checks whether the value in the specified column of the current row is null.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** isColumnNull

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| columnIndex | number | Yes | Index of the specified column, starting from 0. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the value is null; returns **false** otherwise. |

**Examples**

```TypeScript
const isColumnNull = resultSet.isColumnNull(resultSet.getColumnIndex("CODES"));
```

## columnCount

```TypeScript
columnCount: number
```

Number of columns in the result set.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** columnCount

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## columnNames

```TypeScript
columnNames: Array<string>
```

Names of all columns in the result set.

**Type:** Array&lt;string&gt;

**Since:** 7

**Deprecated since:** 9

**Substitutes:** columnNames

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## isAtFirstRow

```TypeScript
isAtFirstRow: boolean
```

Whether the cursor is in the first row of the result set.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** isAtFirstRow

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## isAtLastRow

```TypeScript
isAtLastRow: boolean
```

Whether the cursor is in the last row of the result set.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** isAtLastRow

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## isClosed

```TypeScript
isClosed: boolean
```

Whether the result set is closed.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** isClosed

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## isEnded

```TypeScript
isEnded: boolean
```

Whether the cursor is after the last row of the result set.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** isEnded

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## isStarted

```TypeScript
isStarted: boolean
```

Whether the cursor has been moved.

**Type:** boolean

**Since:** 7

**Deprecated since:** 9

**Substitutes:** isStarted

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## rowCount

```TypeScript
rowCount: number
```

Number of rows in the result set.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** rowCount

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core

## rowIndex

```TypeScript
rowIndex: number
```

Index of the current row in the result set.

**Type:** number

**Since:** 7

**Deprecated since:** 9

**Substitutes:** rowIndex

**System capability:** SystemCapability.DistributedDataManager.RelationalStore.Core
