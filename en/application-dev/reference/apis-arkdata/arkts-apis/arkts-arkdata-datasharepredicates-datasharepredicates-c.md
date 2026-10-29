# DataSharePredicates

```TypeScript
class DataSharePredicates
```

Provides APIs for setting different **DataSharePredicates** objects. This type is not multi-thread safe. If a **DataSharePredicates** instance is operated by multiple threads at the same time in an application, use a lock for it.

**Since:** 10

<!--Device-dataSharePredicates-class DataSharePredicates--><!--Device-dataSharePredicates-class DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

## Modules to Import

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
```

## and

```TypeScript
and(): DataSharePredicates
```

Creates a **DataSharePredicates** object to add the AND condition.

Currently, both the RDB store and KV store support this predicate.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataSharePredicates-and(): DataSharePredicates--><!--Device-DataSharePredicates-and(): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object with the AND operator. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .and()
    .equalTo("SALARY", 200.5);
```

## beginWrap

```TypeScript
beginWrap(): DataSharePredicates
```

Adds a left parenthesis to this **DataSharePredicates**. This API is similar to "(" in an SQL statement and must be used with the right parenthesis.

Currently, only RDB store supports this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-beginWrap(): DataSharePredicates--><!--Device-DataSharePredicates-beginWrap(): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object with a left parenthesis. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap();
```

## between

```TypeScript
between(field: string, low: ValueType, high: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is within the specified range, including the start and end values.

Currently, only RDB store supports this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-between(field: string, low: ValueType, high: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-between(field: string, low: ValueType, high: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string **'null'** or **'undefined'**, the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| low | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Indicate matching with the predicate as the minimum value. When **low** is a number, sort by numeric value to specify the matching range. When **low** is a string, sort in lexicographical order to specify the matching range. When **low** is a boolean, sort by numeric value to specify the matching range. |
| high | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Indicate matching with the predicate as the maximum value. When **high** is a number, sort by numeric value to specify the matching range. When **high** is a string, sort in lexicographical order to specify the matching range. When **high** is a boolean, sort by numeric value to specify the matching range. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.between("AGE", 10, 50);
```

## endWrap

```TypeScript
endWrap(): DataSharePredicates
```

Adds a right parenthesis to this **DataSharePredicates**. This API is similar to ")" in an SQL statement and must be used with the left parenthesis.

Currently, only RDB store supports this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-endWrap(): DataSharePredicates--><!--Device-DataSharePredicates-endWrap(): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object with a right parenthesis. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .beginWrap()
    .equalTo("AGE", 18)
    .or()
    .equalTo("SALARY", 200.5)
    .endWrap();
```

## equalTo

```TypeScript
equalTo(field: string, value: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to search for the records in the specified column that are equal to the given value.

Currently, both the RDB store and KV store support this predicate.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-equalTo(field: string, value: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this interface call is invalid. |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Value to match with the predicate. If **value** is **undefined** or **null**, the predicate configured by this interface call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose");
```

## greaterThan

```TypeScript
greaterThan(field: string, value: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is greater than the specified value.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-greaterThan(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-greaterThan(field: string, value: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string **'null'** or **'undefined'**, the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Value to match with the predicate. If **value** is **undefined** or **null**, the predicate configured by this API call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.greaterThan("AGE", 10);
```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is greater than or equal to the specified value.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-greaterThanOrEqualTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-greaterThanOrEqualTo(field: string, value: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string **'null'** or **'undefined'**, the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Value to match with the predicate. If **value** is **undefined** or **null**, the predicate configured by this API call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.greaterThanOrEqualTo("AGE", 10);
```

## in

```TypeScript
in(field: string, value: Array<ValueType>): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is within the specified range.

Currently, both the RDB store and KV store support this predicate.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataSharePredicates-in(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-in(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string **'null'** or **'undefined'**, the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| value | Array&lt;[ValueType](arkts-arkdata-valuetype-t.md)&gt; | Yes | Value to match, specified as an array of the ValueType type. If **value** is **undefined** or **null**, the predicate configured by this API call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.in("AGE", [18, 20]);
```

## lessThan

```TypeScript
lessThan(field: string, value: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is less than the specified value.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-lessThan(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-lessThan(field: string, value: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **null** or **undefined**, the predicate configured by calling this API is invalid. If this parameter is set to **'null'** or **'undefined'** in string, the matching result may not be as expected or an exception may be thrown when the predicate is used by the KV store and RDB store APIs. |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Value to match with the predicate. If **value** is **undefined** or **null**, the predicate configured by calling this API is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.lessThan("AGE", 50);
```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is less than or equal to the specified value.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-lessThanOrEqualTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-lessThanOrEqualTo(field: string, value: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string **'null'** or **'undefined'**, the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Value to match with the predicate. If **value** is **undefined** or **null**, the predicate configured by this API call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.lessThanOrEqualTo("AGE", 50);
```

## like

```TypeScript
like(field: string, value: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that matches the specified wildcard expression.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-like(field: string, value: string): DataSharePredicates--><!--Device-DataSharePredicates-like(field: string, value: string): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string **'null'** or **'undefined'**, the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| value | string | Yes | Wildcard expression to match with the predicate. In the expression, '%' represents zero, one, or more digits or characters, and '_' represents a single digit or character. It is case insensitive. If **value** is **undefined** or **null**, the predicate configured by this API call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.like("NAME", "%os%");
```

## limit

```TypeScript
limit(total: number, offset: number): DataSharePredicates
```

Creates a **DataSharePredicates** object to specify the number of records in the result and the start position.

Currently, both the RDB store and KV store support this predicate.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates--><!--Device-DataSharePredicates-limit(total: int, offset: int): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| total | number | Yes | Maximum number of records. If the key-value database is used and **total** is **undefined** or **null**, the maximum number of records is limited to 0. If the relational database is used and **total** is **undefined** or **null**, the maximum number of records is not limited. When using a key-value database, for details about the value range, see the description of the **total** parameter in [limit](arkts-arkdata-distributedkvstore-query-c.md#limit). When using a relational database, for details about the value range, see the description of the **value** parameter in [limitAs](arkts-arkdata-relationalstore-rdbpredicates-c.md#limitas). |
| offset | number | Yes | Start position of the query result. If **offset** is **undefined** or **null**, the start position is the beginning of the result set. When using a key-value database, for details about the value range, see the description of the **offset** parameter in [limit](arkts-arkdata-distributedkvstore-query-c.md#limit). When using a relational database, for details about the value range, see the description of the **rowOffset** parameter in [offsetAs](arkts-arkdata-relationalstore-rdbpredicates-c.md#offsetas). |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").limit(10, 3);
```

## notBetween

```TypeScript
notBetween(field: string, low: ValueType, high: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is out of the specified range, excluding the start and end values.

Currently, only RDB store supports this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-notBetween(field: string, low: ValueType, high: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-notBetween(field: string, low: ValueType, high: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string 'null' or 'undefined', the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| low | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Minimum value matching with the predicate. If **low** is number, sort by numeric value to specify the matching range. If **low** is string, sort in lexicographical order to specify the matching range. If **low** is boolean, sort by numeric value to specify the matching range. |
| high | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Maximum value matching with the predicate. If **high** is number, sort by numeric value to specify the matching range. If **high** is string, sort in lexicographical order to specify the matching range. If **high** is boolean, sort by numeric value to specify the matching range. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notBetween("AGE", 10, 50);
```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: ValueType): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is not equal to the specified value.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-notEqualTo(field: string, value: ValueType): DataSharePredicates--><!--Device-DataSharePredicates-notEqualTo(field: string, value: ValueType): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If this parameter is set to **undefined** or **null**, the predicate used is invalid. If this parameter is set to 'null' or 'undefined' in string, the matching result may not be as expected or an exception may be thrown when the predicate is used by the key-value database and relational database APIs. |
| value | [ValueType](arkts-arkdata-valuetype-t.md) | Yes | Value to match with the predicate. If this parameter is set to **undefined** or **null**, the predicate used is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notEqualTo("NAME", "Rose");
```

## notIn

```TypeScript
notIn(field: string, value: Array<ValueType>): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that is not in the specified value.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-notIn(field: string, value: Array<ValueType>): DataSharePredicates--><!--Device-DataSharePredicates-notIn(field: string, value: Array<ValueType>): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this API call is invalid. When **field** is the string **'null'** or **'undefined'**, the key-value database and relational database APIs may return unexpected matching results or throw an exception when using this predicate. |
| value | Array&lt;[ValueType](arkts-arkdata-valuetype-t.md)&gt; | Yes | Value to match, specified as an array of the ValueType type. If **value** is **undefined** or **null**, the predicate configured by this API call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.notIn("NAME", ["Lisa", "Rose"]);
```

## or

```TypeScript
or(): DataSharePredicates
```

Creates a **DataSharePredicates** object to add the OR condition.

Currently, both the RDB store and KV store support this predicate.

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

<!--Device-DataSharePredicates-or(): DataSharePredicates--><!--Device-DataSharePredicates-or(): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object with the OR operator. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "lisi")
    .or()
    .equalTo("NAME", "Rose");
```

## orderByAsc

```TypeScript
orderByAsc(field: string): DataSharePredicates
```

Creates a **DataSharePredicates** object that sorts records in ascending order.

Currently, both the RDB store and KV store support this predicate.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataSharePredicates-orderByAsc(field: string): DataSharePredicates--><!--Device-DataSharePredicates-orderByAsc(field: string): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this interface call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByAsc("AGE");
```

## orderByDesc

```TypeScript
orderByDesc(field: string): DataSharePredicates
```

Creates a **DataSharePredicates** object that sorts data in descending order.

Currently, both the RDB store and KV store support this predicate.

**Since:** 10

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 20.

<!--Device-DataSharePredicates-orderByDesc(field: string): DataSharePredicates--><!--Device-DataSharePredicates-orderByDesc(field: string): DataSharePredicates-End-->

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. If **field** is **undefined** or **null**, the predicate configured by this interface call is invalid. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.orderByDesc("AGE");
```
