# @ohos.data.dataAbility (DataAbility Predicates)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @baijidong-->
<!--Designer: @htt1997-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=322f3406587b0e3e9fd2ec3098ccc13904d7d66a translatedAt=2026-09-04T03:23:51.795Z pushedAt=2026-09-09T09:11:03.704Z -->

The **DataAbility** module provides APIs to create predicates for querying data from relational database (RDB) stores.

> **NOTE**
>
> The initial APIs of this module are supported since API version 7. Newly added APIs will be marked with a superscript to indicate their earliest API version.


## Modules to Import

```js
import { dataAbility } from '@kit.ArkData';
```

## dataAbility.createRdbPredicates

createRdbPredicates(name: string, dataAbilityPredicates: DataAbilityPredicates): rdb.RdbPredicates

Creates an **RdbPredicates** object with a table name and **DataAbilityPredicates** object.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| name | string | Yes | Name of the database table. It cannot be an empty string. |
| dataAbilityPredicates | [DataAbilityPredicates](#dataabilitypredicates) | Yes| **DataAbilityPredicates** object.  |

**Return value**

| Type| Description|
| -------- | -------- |
| rdb.[RdbPredicates](js-apis-data-rdb.md#rdbpredicates) | **RdbPredicates** object that matches the specified field. |

**Example**

  ```js
  let dataAbilityPredicates = new dataAbility.DataAbilityPredicates();
  dataAbilityPredicates.equalTo("NAME", "Rose");
  // EMPLOYEE is a table created in an RDB store.
  let predicates = dataAbility.createRdbPredicates("EMPLOYEE", dataAbilityPredicates);
  ```

## DataAbilityPredicates

Provides APIs for creating diverse query conditions.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Initialization**

  ```js
  let dataAbilityPredicates = new dataAbility.DataAbilityPredicates();
  ```

### equalTo

equalTo(field: string, value: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are equal to the given value.

This API is similar to the "=" operator in an SQL statement.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table, which cannot be an empty string. |
| value | [ValueType](#valuetype) | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.equalTo("NAME", "lisi");
  ```

### notEqualTo

notEqualTo(field: string, value: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are not equal to the given value.

This API is similar to the "!=" operator in an SQL statement.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | [ValueType](#valuetype) | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.notEqualTo("NAME", "lisi");
  ```

### beginWrap

beginWrap(): DataAbilityPredicates

Adds a left parenthesis to the predicate. This API is similar to "(" in an SQL statement and must be used with [endWrap](#endwrap).

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | Predicate with a left parenthesis. |

**Example**

  ```js
  dataAbilityPredicates.equalTo("NAME", "lisi")
      .beginWrap()
      .equalTo("AGE", 18)
      .or()
      .equalTo("SALARY", 200.5)
      .endWrap();
  ```

### endWrap

endWrap(): DataAbilityPredicates

Adds a right parenthesis to the predicate. This API is similar to ")" in an SQL statement and must be used with [beginWrap](#beginwrap).

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | Returns a predicate with a right parenthesis. |

**Example**

  ```js
  dataAbilityPredicates.equalTo("NAME", "lisi")
      .beginWrap()
      .equalTo("AGE", 18)
      .or()
      .equalTo("SALARY", 200.5)
      .endWrap();
  ```

### or

or(): DataAbilityPredicates

Adds the logical OR condition to the predicate.

This API is similar to the "or" operator in an SQL statement.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | Predicate with logical OR. |

**Example**

  ```js
  dataAbilityPredicates.equalTo("NAME", "Lisa")
      .or()
      .equalTo("NAME", "Rose");
  ```

### and

and(): DataAbilityPredicates

Adds the logical AND condition to the predicate.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | Predicate with logical AND. |

**Example**

  ```js
  dataAbilityPredicates.equalTo("NAME", "Lisa")
      .and()
      .equalTo("SALARY", 200.5);
  ```

### contains

contains(field: string, value: string): DataAbilityPredicates

Configures a predicate to match fields whose data type is string and whose value contains the specified string.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | string | Yes | String to match against the predicate. |

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.contains("NAME", "os");
  ```

### beginsWith

beginsWith(field: string, value: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that begin with the given value.

This API is similar to "value%" in an SQL statement.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | string | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.beginsWith("NAME", "os");
  ```

### endsWith

endsWith(field: string, value: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that end with the given value.

This API is similar to "%value" in an SQL statement.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | string | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.endsWith("NAME", "se");
  ```

### isNull

isNull(field: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are **null**.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.isNull("NAME");
  ```

### isNotNull

isNotNull(field: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are not **null**.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. Cannot be an empty string. |

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.isNotNull("NAME");
  ```

### like

like(field: string, value: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are similar to the given value.

This API is similar to the SQL **like** statement.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. Cannot be an empty string. |
| value | string | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.like("NAME", "%os%");
  ```

### glob

glob(field: string, value: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that match the given string. Different from **like**, the input parameters of this API are case-sensitive.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | string | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.glob("NAME", "?h*g");

  // Only matches the "NAME" field with the value "Lisa".
  dataAbilityPredicates.glob("NAME", "Lisa");

  // Only matches the "NAME" field with the value "lisa".
  dataAbilityPredicates.glob("NAME", "lisa");
  ```

### between

between(field: string, low: ValueType, high: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are within the given range.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| low | [ValueType](#valuetype) | Yes| Minimum value to match.|
| high | [ValueType](#valuetype) | Yes| Maximum value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.between("AGE", 10, 50);
  ```

### notBetween

notBetween(field: string, low: ValueType, high: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are out of the given range.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| low | [ValueType](#valuetype) | Yes| Minimum value to match.|
| high | [ValueType](#valuetype) | Yes| Maximum value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.notBetween("AGE", 10, 50);
  ```

### greaterThan

greaterThan(field: string, value: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are greater than the given value.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table, which cannot be an empty string. |
| value | [ValueType](#valuetype) | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.greaterThan("AGE", 18);
  ```

### lessThan

lessThan(field: string, value: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are less than the given value.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | [ValueType](#valuetype) | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.lessThan("AGE", 20);
  ```

### greaterThanOrEqualTo

greaterThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are greater than or equal to the given value.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | [ValueType](#valuetype) | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.greaterThanOrEqualTo("AGE", 18);
  ```

### lessThanOrEqualTo

lessThanOrEqualTo(field: string, value: ValueType): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are less than or equal to the given value.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table, which cannot be an empty string. |
| value | [ValueType](#valuetype) | Yes| Value to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.lessThanOrEqualTo("AGE", 20);
  ```

### orderByAsc

orderByAsc(field: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to sort the records in the specified column in ascending order. When there are multiple **orderByAsc**s, the first **orderByAsc** used has the highest priority.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  // Sort by the "NAME" field first, then by the "AGE" field when the values are the same, and finally by "SALARY".
  dataAbilityPredicates.orderByAsc("NAME").orderByAsc("AGE").orderByAsc("SALARY");
  ```

### orderByDesc

orderByDesc(field: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to sort the records in the specified column in descending order. When there are multiple **orderByDesc**s, the first **orderByDesc** used has the highest priority.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  // Sort by "AGE" first, and by "SALARY" when the values are the same.
  dataAbilityPredicates.orderByDesc("AGE").orderByDesc("SALARY");
  ```

### distinct

distinct(): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to filter out duplicate records.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.equalTo("NAME", "Rose").distinct();
  ```

### limitAs

limitAs(value: number): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to limit the number of records.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| value | number | Yes| Maximum number of records. The value should be a positive integer. If a value less than or equal to **0** is specified, the number of records is not limited.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.equalTo("NAME", "Rose").limitAs(3);
  ```

### offsetAs

offsetAs(rowOffset: number): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to set the start position of the query result. This API must be used together with [limitAs](#limitas) to specify the number of results. Otherwise, no result will be returned. To query all rows after the specified offset, pass -1 to [limitAs](#limitas).

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| rowOffset | number | Yes | Start position of the returned result. If a positive integer is passed in, the result is returned from the specified position. If the value passed in is less than or equal to 0, the query result is returned from the first element. |

**Return value**
| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  // Display the three data records following the first three records.
  dataAbilityPredicates.equalTo("NAME", "Rose").offsetAs(3).limitAs(3);
  ```

### groupBy

groupBy(fields: Array&lt;string&gt;): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to group the query results based on the specified columns.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| fields | Array&lt;string&gt; | Yes| Names of columns to group.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.groupBy(["AGE", "NAME"]);
  ```

### indexedBy

indexedBy(field: string): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to specify the index column. Before calling this API, you need to create an index column.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Name of the index to create. |

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

```js
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

### in

in(field: string, value: Array&lt;ValueType&gt;): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are in the given range.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. Cannot be an empty string. |
| value | Array&lt;[ValueType](#valuetype)&gt; | Yes| Array of **ValueType**s to match.|


**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.in("AGE", [18, 20]);
  ```

### notIn

notIn(field: string, value: Array&lt;ValueType&gt;): DataAbilityPredicates

Creates a **DataAbilityPredicates** object to search for the records in the specified column that are out of the given range.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

**Parameters**

| Name| Type| Mandatory| Description|
| -------- | -------- | -------- | -------- |
| field | string | Yes | Column name in the database table. It cannot be an empty string. |
| value | Array&lt;[ValueType](#valuetype)&gt; | Yes| Array of **ValueType**s to match.|

**Return value**

| Type| Description|
| -------- | -------- |
| [DataAbilityPredicates](#dataabilitypredicates) | **DataAbilityPredicates** object created.|

**Example**

  ```js
  dataAbilityPredicates.notIn("NAME", ["Lisa", "Rose"]);
  ```

## ValueType

type ValueType = number | string | boolean

Defines the value types.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Core

| Type   | Description                |
| ------- | -------------------- |
| number  | The value is a number.  |
| string  | The value is a string.   |
| boolean | The value is a boolean.|
