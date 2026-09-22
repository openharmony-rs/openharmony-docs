# DataAbilityPredicates

```TypeScript
class DataAbilityPredicates
```

Provides APIs for creating diverse query conditions.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

## Modules to Import

```TypeScript
import { dataAbility } from '@kit.ArkData';
```

## and

```TypeScript
and(): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to add the AND condition.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object with the AND condition. |

**Examples**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Lisa")
    .and()
    .equalTo("SALARY", 200.5);
```

## beginsWith

```TypeScript
beginsWith(field: string, value: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that begin with the given value.

This API is similar to the percent sign (%) in SQL statements.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.beginsWith("NAME", "os");
```

## beginWrap

```TypeScript
beginWrap(): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to add a left parenthesis. This API is similar to "(" in an SQL statement and must be used with **endWrap**.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object with a left parenthesis. |

**Examples**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap();
```

## between

```TypeScript
between(field: string, low: ValueType, high: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are within the given range.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| low | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Minimum value to match. |
| high | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Maximum value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.between("AGE", 10, 50);
```

## contains

```TypeScript
contains(field: string, value: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that contain the given value.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.contains("NAME", "os");
```

## distinct

```TypeScript
distinct(): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to filter out duplicate records.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Rose").distinct();
```

## endsWith

```TypeScript
endsWith(field: string, value: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that end with the given value.

This API is similar to the percent sign (%) in SQL statements.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.endsWith("NAME", "se");
```

## endWrap

```TypeScript
endWrap(): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to add a right parenthesis. This API is similar to ")" in an SQL statement and must be used with **beginWrap**.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object with a right parenthesis. |

**Examples**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap();
```

## equalTo

```TypeScript
equalTo(field: string, value: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are equal to the given value.

This API is similar to the SQL equal to (=) operator.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "lisi");
```

## glob

```TypeScript
glob(field: string, value: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that match the given string. Different from **like**, the input parameters of this API are case-sensitive.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.glob("NAME", "?h*g");

// Only matches the "NAME" field with the value "Lisa".
dataAbilityPredicates.glob("NAME", "Lisa");

// Only matches the "NAME" field with the value "lisa".
dataAbilityPredicates.glob("NAME", "lisa");
```

## greaterThan

```TypeScript
greaterThan(field: string, value: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are greater than the given value.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.greaterThan("AGE", 18);
```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are greater than or equal to the given value.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.greaterThanOrEqualTo("AGE", 18);
```

## groupBy

```TypeScript
groupBy(fields: Array<string>): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to group the query results based on the specified columns.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;string&gt; | Yes | Names of columns to group. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.groupBy(["AGE", "NAME"]);
```

## in

```TypeScript
in(field: string, value: Array<ValueType>): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are in the given range.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | Array&lt;[ValueType](arkts-arkdata-dataability-valuetype-t.md)&gt; | Yes | Array of **ValueType**s to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.in("AGE", [18, 20]);
```

## indexedBy

```TypeScript
indexedBy(field: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to specify the index column. Before calling this API, you need to create an index column.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Name of the index. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
import { UIAbility } from '@kit.AbilityKit';
import { dataAbility, relationalStore } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

export default class EntryAbility extends UIAbility {
  async onCreate(): Promise<void> {
    let store: relationalStore.RdbStore | undefined = undefined;
    let context = this.context;

    try {
      const STORE_CONFIG: relationalStore.StoreConfig = {
        name: 'RdbTest.db', // Database file name.
        securityLevel: relationalStore.SecurityLevel.S3,
      };
      // Table structure: EMPLOYEE (ID, NAME, AGE, SALARY, CODES)
      const SQL_CREATE_TABLE =
        'CREATE TABLE IF NOT EXISTS EMPLOYEE (ID INTEGER PRIMARY KEY AUTOINCREMENT, NAME TEXT NOT NULL, AGE INTEGER, SALARY REAL, CODES BLOB)'; // SQL statement for creating a data table.
      store = await relationalStore.getRdbStore(context, STORE_CONFIG);
      console.info('Succeeded in getting RdbStore.');
      await store.executeSql(SQL_CREATE_TABLE); // Create a data table.
    } catch (e) {
      const err = e as BusinessError;
      console.error(`Failed to get RdbStore. Code:${err.code}, message:${err.message}`);
    }

    if (!store) {
      return;
    }

    // Create an index.
    const SQL_CREATE_INDEX = 'CREATE INDEX SALARY_INDEX ON EMPLOYEE(SALARY)';
    await store.executeSql(SQL_CREATE_INDEX);
    // ...

    let dataAbilityPredicates = new dataAbility.DataAbilityPredicates();
    dataAbilityPredicates.indexedBy("SALARY_INDEX");

    // ...
  }
}
```

## isNotNull

```TypeScript
isNotNull(field: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are not **null**.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.isNotNull("NAME");
```

## isNull

```TypeScript
isNull(field: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are **null**.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.isNull("NAME");
```

## lessThan

```TypeScript
lessThan(field: string, value: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are less than the given value.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.lessThan("AGE", 20);
```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are less than or equal to the given value.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.lessThanOrEqualTo("AGE", 20);
```

## like

```TypeScript
like(field: string, value: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are similar to the given value.

This API is similar to the SQL **like** statement.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.like("NAME", "%os%");
```

## limitAs

```TypeScript
limitAs(value: number): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to limit the number of records.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| value | number | Yes | Maximum number of records. The value should be a positive integer. If a value less than or equal to **0** is specified, the number of records is not limited. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Rose").limitAs(3);
```

## notBetween

```TypeScript
notBetween(field: string, low: ValueType, high: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are out of the given range.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| low | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Minimum value to match. |
| high | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Maximum value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.notBetween("AGE", 10, 50);
```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: ValueType): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are not equal to the given value.

This API is similar to the SQL not equal (!=) operator.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | [ValueType](arkts-arkdata-dataability-valuetype-t.md) | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.notEqualTo("NAME", "lisi");
```

## notIn

```TypeScript
notIn(field: string, value: Array<ValueType>): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are out of the given range.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |
| value | Array&lt;[ValueType](arkts-arkdata-dataability-valuetype-t.md)&gt; | Yes | Array of **ValueType**s to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
dataAbilityPredicates.notIn("NAME", ["Lisa", "Rose"]);
```

## offsetAs

```TypeScript
offsetAs(rowOffset: number): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to set the start position of the query result. This API must be used together with **limitAs**. Otherwise, no result will be returned. To query all rows after the specified offset, pass in **-1** in **limitAs**.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rowOffset | number | Yes | Start position. The value should be a positive integer. If a value less than or equal to **0** is specified, the query result is returned from the first element. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
// Display the three data records following the first three records.
dataAbilityPredicates.equalTo("NAME", "Rose").offsetAs(3).limitAs(3);
```

## or

```TypeScript
or(): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to add the OR condition.

This API is similar to the SQL **or** operator.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object with the OR condition. |

**Examples**

```TypeScript
dataAbilityPredicates.equalTo("NAME", "Lisa")
    .or()
    .equalTo("NAME", "Rose");
```

## orderByAsc

```TypeScript
orderByAsc(field: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to sort the records in the specified column in ascending order. When there are multiple **orderByAsc**s, the first **orderByAsc** used has the highest priority.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
// Sort by the "NAME" field first, then by the "AGE" field when the values are the same, and finally by "SALARY".
dataAbilityPredicates.orderByAsc("NAME").orderByAsc("AGE").orderByAsc("SALARY");
```

## orderByDesc

```TypeScript
orderByDesc(field: string): DataAbilityPredicates
```

Creates a **DataAbilityPredicates** object to sort the records in the specified column in descending order. When there are multiple **orderByDesc**s, the first **orderByDesc** used has the highest priority.

**Since:** 7

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the table. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataAbilityPredicates](arkts-arkdata-dataability-dataabilitypredicates-c.md) | **DataAbilityPredicates** object created. |

**Examples**

```TypeScript
// Sort by "AGE" first, and by "SALARY" when the values are the same.
dataAbilityPredicates.orderByDesc("AGE").orderByDesc("SALARY");
```
