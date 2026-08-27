# ResultSet

结果集是指用户调用关系型数据库查询接口之后返回的结果集合，提供了多种灵活的数据访问方式，以便用户获取各项数据。

> **说明：**
> 
> 从API Version 9开始，该接口不再维护，推荐使用新接口[ResultSet](arkts-arkdata-relationalstore-resultset-i.md)。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [relationalStore](arkts-data-relationalstore.md)

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## close

```TypeScript
close(): void
```

关闭结果集。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** close

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**示例**

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

以字节数组的形式获取当前行中指定列的值。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getBlob

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 以字节数组的形式返回指定列的值。 |

**示例**

```TypeScript
const codes = resultSet.getBlob(resultSet.getColumnIndex("CODES"));
```

## getColumnIndex

```TypeScript
getColumnIndex(columnName: string): number
```

根据指定的列名获取列索引。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getColumnIndex

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnName | string | 是 | 表示结果集中指定列的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定列的索引。 |

**示例**

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

根据指定的列索引获取列名。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getColumnName

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 表示结果集中指定列的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定列的名称。 |

**示例**

```TypeScript
const id = resultSet.getColumnName(0);
const name = resultSet.getColumnName(1);
const age = resultSet.getColumnName(2);
```

## getDouble

```TypeScript
getDouble(columnIndex: number): number
```

以double形式获取当前行中指定列的值。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getDouble

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 以double形式返回指定列的值。 |

**示例**

```TypeScript
const salary = resultSet.getDouble(resultSet.getColumnIndex("SALARY"));
```

## getLong

```TypeScript
getLong(columnIndex: number): number
```

以Long形式获取当前行中指定列的值。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getLong

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 以Long形式返回指定列的值。 |

**示例**

```TypeScript
const age = resultSet.getLong(resultSet.getColumnIndex("AGE"));
```

## getString

```TypeScript
getString(columnIndex: number): string
```

以字符串形式获取当前行中指定列的值。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getString

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以字符串形式返回指定列的值。 |

**示例**

```TypeScript
const name = resultSet.getString(resultSet.getColumnIndex("NAME"));
```

## goTo

```TypeScript
goTo(offset: number): boolean
```

向前或向后移至结果集的指定行，相对于其当前位置偏移。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** goTo

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 表示相对于当前位置的偏移量。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例**

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

转到结果集的第一行。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** goToFirstRow

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集到第一行，则为true；否则为false。 |

**示例**

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

转到结果集的最后一行。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** goToLastRow

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集到最后一行，则为true；否则为false。 |

**示例**

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

转到结果集的下一行。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** goToNextRow

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集到下一行，则为true；否则为false。 |

**示例**

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

转到结果集的上一行。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** goToPreviousRow

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集到上一行，则为true；否则为false。 |

**示例**

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

转到结果集的指定行。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** goToRow

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 表示要移动到的指定位置。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例**

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

检查当前行中指定列的值是否为null。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isColumnNull

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果当前行中指定列的值为null，则返回true，否则返回false。 |

**示例**

```TypeScript
const isColumnNull = resultSet.isColumnNull(resultSet.getColumnIndex("CODES"));
```

## columnCount

```TypeScript
columnCount: number
```

columnCount: number获取结果集中的列数。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** columnCount

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## columnNames

```TypeScript
columnNames: Array<string>
```

columnNames: Array&lt;string&gt;获取结果集中所有列的名称。

**类型：** Array&lt;string&gt;

**起始版本：** 7

**废弃版本：** 9

**替代接口：** columnNames

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isAtFirstRow

```TypeScript
isAtFirstRow: boolean
```

isAtFirstRow: boolean检查结果集是否位于第一行。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isAtFirstRow

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isAtLastRow

```TypeScript
isAtLastRow: boolean
```

isAtLastRow: boolean检查结果集是否位于最后一行。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isAtLastRow

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isClosed

```TypeScript
isClosed: boolean
```

isClosed: boolean检查当前结果集是否关闭。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isClosed

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isEnded

```TypeScript
isEnded: boolean
```

isEnded: boolean检查结果集是否位于最后一行之后。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isEnded

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## isStarted

```TypeScript
isStarted: boolean
```

isStarted: boolean检查指针是否移动过。

**类型：** boolean

**起始版本：** 7

**废弃版本：** 9

**替代接口：** isStarted

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## rowCount

```TypeScript
rowCount: number
```

rowCount: number获取结果集中的行数。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** rowCount

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core

## rowIndex

```TypeScript
rowIndex: number
```

rowIndex: number获取结果集当前行的索引。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** rowIndex

**系统能力：** SystemCapability.DistributedDataManager.RelationalStore.Core
