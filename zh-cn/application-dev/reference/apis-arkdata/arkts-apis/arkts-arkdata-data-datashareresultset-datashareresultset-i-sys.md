# DataShareResultSet（系统接口）

提供通过查询数据库生成的结果集的相关访问方法。

列或键名称作为字符串数组返回，其中字符串的顺序与结果集中的列或键的顺序相同。

**起始版本：** 9

<!--Device-unnamed-export default interface DataShareResultSet--><!--Device-unnamed-export default interface DataShareResultSet-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { DataType } from '@kit.ArkData';
```

<a id="close"></a>
## close

```TypeScript
close(): void
```

关闭结果集。

对结果集调用此方法将释放其所有资源并使其无效。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-close(): void--><!--Device-DataShareResultSet-close(): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**示例：**

```TypeScript
if (resultSet != undefined) {
  (resultSet as DataShareResultSet).close();
}

```

<a id="getblob"></a>
## getBlob

```TypeScript
getBlob(columnIndex: number): Uint8Array
```

以字节数组的形式获取当前行中指定列的值。

如果当前行中指定的列或键的值为空，或者指定的列或键不是Blob类型，则使用方需要确定是否抛出此异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-getBlob(columnIndex: int): Uint8Array--><!--Device-DataShareResultSet-getBlob(columnIndex: int): Uint8Array-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Uint8Array | 以字节数组的形式返回指定列的值。 |

**示例：**

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

<a id="getcolumnindex"></a>
## getColumnIndex

```TypeScript
getColumnIndex(columnName: string): number
```

根据指定的列名获取列索引。

列名作为输入参数传递。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-getColumnIndex(columnName: string): int--><!--Device-DataShareResultSet-getColumnIndex(columnName: string): int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnName | string | 是 | 表示结果集中指定列的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回指定列的索引。 |

**示例：**

```TypeScript
let ColumnName = "name";
if (resultSet != undefined) {
  let getColumnIndex = (resultSet as DataShareResultSet).getColumnIndex(ColumnName);
  console.info('resultSet.getColumnIndex: ' + getColumnIndex);
}

```

<a id="getcolumnname"></a>
## getColumnName

```TypeScript
getColumnName(columnIndex: number): string
```

根据指定的列索引获取列名。

列索引作为输入参数传递。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-getColumnName(columnIndex: int): string--><!--Device-DataShareResultSet-getColumnName(columnIndex: int): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 表示结果集中指定列的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回指定列的名称。 |

**示例：**

```TypeScript
let columnIndex = 1;
if (resultSet != undefined) {
  let getColumnName = (resultSet as DataShareResultSet).getColumnName(columnIndex);
  console.info('resultSet.getColumnName: ' + getColumnName);
}

```

<a id="getdatatype"></a>
## getDataType

```TypeScript
getDataType(columnIndex: number): DataType
```

指定列索引获取该列的数据类型。

如果当前行中指定的列或键的值为空，或者指定的列或键不是DataType类型，则使用方需要确定是否抛出此异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-getDataType(columnIndex: int): DataType--><!--Device-DataShareResultSet-getDataType(columnIndex: int): DataType-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 表示结果集中指定列的索引。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [DataType](../../apis-ability-kit/arkts-apis/arkts-ability-screenlockfilemanager-datatype-e.md) | 返回指定列的类型。 |

**示例：**

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

<a id="getdouble"></a>
## getDouble

```TypeScript
getDouble(columnIndex: number): number
```

以值类型为双浮点数形式获取当前行中指定列的值。

如果当前行中指定的列或键的值为空，或者指定的列或键不是double类型，则使用方需要确定是否抛出此异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-getDouble(columnIndex: int): double--><!--Device-DataShareResultSet-getDouble(columnIndex: int): double-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | Value obtained. |

**示例：**

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

<a id="getlong"></a>
## getLong

```TypeScript
getLong(columnIndex: number): number
```

以长整数值形式获取当前行中指定列的值。

如果当前行中指定的列或键的值为空，或者指定的列或键不是long类型，则使用方需要确定是否抛出此异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-getLong(columnIndex: int): long--><!--Device-DataShareResultSet-getLong(columnIndex: int): long-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 以长整数值形式返回指定列的值。 |

**示例：**

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

<a id="getstring"></a>
## getString

```TypeScript
getString(columnIndex: number): string
```

以字符串形式获取当前行中指定列的值。

如果当前行中指定的列或键的值为空，或者指定的列或键不是string类型，则使用方需要确定是否抛出此异常。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-getString(columnIndex: int): string--><!--Device-DataShareResultSet-getString(columnIndex: int): string-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| columnIndex | number | 是 | 指定的列索引，从0开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 以字符串形式返回指定列的值。 |

**示例：**

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

<a id="goto"></a>
## goTo

```TypeScript
goTo(offset: number): boolean
```

相对于当前位置向前或向后移动指定行数。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-goTo(offset: int): boolean--><!--Device-DataShareResultSet-goTo(offset: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 表示相对于当前位置的偏移量。offset为负值表示向前偏移，正值则表示向后偏移。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例：**

```TypeScript
let goToNum = 1;
if (resultSet != undefined) {
  let isGoTo = (resultSet as DataShareResultSet).goTo(goToNum);
  console.info('resultSet.goTo: ' + isGoTo);
}

```

<a id="gotofirstrow"></a>
## goToFirstRow

```TypeScript
goToFirstRow(): boolean
```

转到结果集的第一行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-goToFirstRow(): boolean--><!--Device-DataShareResultSet-goToFirstRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例：**

```TypeScript
// resultSet需依照本页的使用说明进行创建。
if (resultSet != undefined) {
  let isGoToFirstRow = (resultSet as DataShareResultSet).goToFirstRow();
  console.info('resultSet.goToFirstRow: ' + isGoToFirstRow);
}

```

<a id="gotolastrow"></a>
## goToLastRow

```TypeScript
goToLastRow(): boolean
```

转到结果集的最后一行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-goToLastRow(): boolean--><!--Device-DataShareResultSet-goToLastRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例：**

```TypeScript
if (resultSet != undefined) {
  let isGoToLastRow = (resultSet as DataShareResultSet).goToLastRow();
  console.info('resultSet.goToLastRow: ' + isGoToLastRow);
}

```

<a id="gotonextrow"></a>
## goToNextRow

```TypeScript
goToNextRow(): boolean
```

转到结果集的下一行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-goToNextRow(): boolean--><!--Device-DataShareResultSet-goToNextRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例：**

```TypeScript
if (resultSet != undefined) {
  let isGoToNextRow = (resultSet as DataShareResultSet).goToNextRow();
  console.info('resultSet.goToNextRow: ' + isGoToNextRow);
}

```

<a id="gotopreviousrow"></a>
## goToPreviousRow

```TypeScript
goToPreviousRow(): boolean
```

转到结果集的上一行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-goToPreviousRow(): boolean--><!--Device-DataShareResultSet-goToPreviousRow(): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例：**

```TypeScript
if (resultSet != undefined) {
  let isGoToPreviousRow = (resultSet as DataShareResultSet).goToPreviousRow();
  console.info('resultSet.goToPreviousRow: ' + isGoToPreviousRow);
}

```

<a id="gotorow"></a>
## goToRow

```TypeScript
goToRow(position: number): boolean
```

转到结果集的指定行。

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-goToRow(position: int): boolean--><!--Device-DataShareResultSet-goToRow(position: int): boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| position | number | 是 | 表示要移动到的指定位置，从 0 开始。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 如果成功移动结果集，则为true；否则返回false。 |

**示例：**

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

结果集中的列数。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-columnCount: int--><!--Device-DataShareResultSet-columnCount: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

## columnNames

```TypeScript
columnNames: Array<string>
```

结果集中所有列的名称。

**类型：** Array&lt;string&gt;

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-columnNames: Array<string>--><!--Device-DataShareResultSet-columnNames: Array<string>-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

## isClosed

```TypeScript
isClosed: boolean
```

标识当前结果集是否关闭。如果结果集已关闭，则为true；否则为false。

**类型：** boolean

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-isClosed: boolean--><!--Device-DataShareResultSet-isClosed: boolean-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

## rowCount

```TypeScript
rowCount: number
```

结果集中的行数。

**类型：** number

**起始版本：** 9

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-DataShareResultSet-rowCount: int--><!--Device-DataShareResultSet-rowCount: int-End-->

**系统能力：** SystemCapability.DistributedDataManager.DataShare.Core

**系统接口：** 此接口为系统接口。

