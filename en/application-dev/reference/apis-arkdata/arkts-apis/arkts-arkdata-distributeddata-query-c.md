# Query

```TypeScript
class Query
```

Provides APIs to create a **Query** object, which defines different data query criteria.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** Query

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
```

## and

```TypeScript
and(): Query
```

Creates a **Query** object with the AND condition.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** and

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value1");
    query.and();
    query.notEqualTo("field", "value2");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## beginGroup

```TypeScript
beginGroup(): Query
```

Creates a **Query** object for a query condition group with a left parenthesis.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** beginGroup

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.beginGroup();
    query.isNotNull("field");
    query.endGroup();
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## constructor

```TypeScript
constructor()
```

Defines a constructor used to create a **Query** instance.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** constructor

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId(deviceId: string): Query
```

Creates a **Query** object with the device ID as the key prefix.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** deviceId

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | Device ID. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.deviceId("deviceId");
    console.info("query is " + query.getSqlLike());
} catch (e) {
    console.error("should be ok on Method Chaining : " + e);
}
```

## endGroup

```TypeScript
endGroup(): Query
```

Creates a **Query** object for a query condition group with a right parenthesis.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** endGroup

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.beginGroup();
    query.isNotNull("field");
    query.endGroup();
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## equalTo

```TypeScript
equalTo(field: string, value: number | string | boolean): Query
```

Creates a **Query** object to search for the records with the specified field that are equal to the given value.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** equalTo

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | number &#124; string &#124; boolean | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.equalTo("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## getSqlLike

```TypeScript
getSqlLike(): string
```

Obtains the query statement of the **Query** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** getSqlLike

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Query statement obtained. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    let sql1 = query.getSqlLike();
    console.info("GetSqlLike sql=" + sql1);
} catch (e) {
    console.error("duplicated calls should be ok : " + e);
}
```

## greaterThan

```TypeScript
greaterThan(field: string, value: number | string | boolean): Query
```

Creates a **Query** object to search for the records with the specified field that are greater than the given value.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** greaterThan

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | number &#124; string &#124; boolean | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.greaterThan("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: number | string): Query
```

Creates a **Query** object to search for the records with the specified field that are greater than or equal to the given value.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** greaterThanOrEqualTo

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | number &#124; string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.greaterThanOrEqualTo("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## inNumber

```TypeScript
inNumber(field: string, valueList: number[]): Query
```

Creates a **Query** object to search for the records with the specified field that are within the given number list.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** inNumber

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| valueList | number[] | Yes | List of numbers to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.inNumber("field", [0, 1]);
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## inString

```TypeScript
inString(field: string, valueList: string[]): Query
```

Creates a **Query** object to search for the records with the specified field that are within the given string list.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** inString

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| valueList | string[] | Yes | List of strings to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.inString("field", ['test1', 'test2']);
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## isNotNull

```TypeScript
isNotNull(field: string): Query
```

Creates a **Query** object to search for the records whose value is not **null**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** isNotNull

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.isNotNull("field");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## isNull

```TypeScript
isNull(field: string): Query
```

Creates a **Query** object to search for the records with the specified field that are **null**.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** isNull

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.isNull("field");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## lessThan

```TypeScript
lessThan(field: string, value: number | string): Query
```

Creates a **Query** object to search for the records with the specified field that are less than the given value.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** lessThan

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | number &#124; string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.lessThan("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: number | string): Query
```

Creates a **Query** object to search for the records with the specified field that are less than or equal to the given value.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** lessThanOrEqualTo

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | number &#124; string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.lessThanOrEqualTo("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## like

```TypeScript
like(field: string, value: string): Query
```

Creates a **Query** object to search for the records with the specified field that are similar to the given string.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** like

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | string | Yes | String to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.like("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## limit

```TypeScript
limit(total: number, offset: number): Query
```

Creates a **Query** object to specify the number of records in the query result and the start position.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** limit

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| total | number | Yes | Number of records in the query result. |
| offset | number | Yes | Start position. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
let total = 10;
let offset = 1;
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    query.limit(total, offset);
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: number | string | boolean): Query
```

Creates a **Query** object to search for the records with the specified field that are not equal to the given value.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** notEqualTo

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | number &#124; string &#124; boolean | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## notInNumber

```TypeScript
notInNumber(field: string, valueList: number[]): Query
```

Creates a **Query** object to search for the records with the specified field that are not within the given number list.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** notInNumber

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| valueList | number[] | Yes | List of numbers to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notInNumber("field", [0, 1]);
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## notInString

```TypeScript
notInString(field: string, valueList: string[]): Query
```

Creates a **Query** object to search for the records with the specified field that are not within the given string list.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** notInString

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| valueList | string[] | Yes | List of strings to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notInString("field", ['test1', 'test2']);
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## or

```TypeScript
or(): Query
```

Creates a **Query** object with the OR condition.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** or

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value1");
    query.or();
    query.notEqualTo("field", "value2");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## orderByAsc

```TypeScript
orderByAsc(field: string): Query
```

Creates a **Query** object to sort the query results in ascending order.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** orderByAsc

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    query.orderByAsc("field");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## orderByDesc

```TypeScript
orderByDesc(field: string): Query
```

Creates a **Query** object to sort the query results in descending order.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** orderByDesc

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.notEqualTo("field", "value");
    query.orderByDesc("field");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## prefixKey

```TypeScript
prefixKey(prefix: string): Query
```

Creates a **Query** object with a specified key prefix.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** prefixKey

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| prefix | string | Yes | Key prefix. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.prefixKey("$.name");
    query.prefixKey("0");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```

## reset

```TypeScript
reset(): Query
```

Resets the **Query** object.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** reset

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object reset. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.equalTo("key", "value");
    console.info("query is " + query.getSqlLike());
    query.reset();
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("simply calls should be ok :" + e);
}
```

## setSuggestIndex

```TypeScript
setSuggestIndex(index: string): Query
```

Creates a **Query** object with an index preferentially used for query.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** setSuggestIndex

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | string | Yes | Index preferentially used for query. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.setSuggestIndex("$.name");
    query.setSuggestIndex("0");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
   console.error("duplicated calls should be ok :" + e);
}
```

## unlike

```TypeScript
unlike(field: string, value: string): Query
```

Creates a **Query** object to search for the records with the specified field that are not similar to the given string.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** unlike

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to query. It cannot contain '^'. |
| value | string | Yes | String to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributeddata-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
try {
    let query = new distributedData.Query();
    query.unlike("field", "value");
    console.info("query is " + query.getSqlLike());
    query = null;
} catch (e) {
    console.error("duplicated calls should be ok :" + e);
}
```
