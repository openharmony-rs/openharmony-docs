# DataSharePredicates

```TypeScript
class DataSharePredicates
```

Provides APIs for setting different **DataSharePredicates** objects. This type is not multi-thread safe. If a **DataSharePredicates** instance is operated by multiple threads at the same time in an application, use a lock for it.

**Since:** 10

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

## Modules to Import

```TypeScript
import { dataSharePredicates } from '@kit.ArkData';
```

## beginsWith

```TypeScript
beginsWith(field: string, value: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that begins with the specified value.

Currently, only RDB store supports this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. |
| value | string | Yes | Start value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.beginsWith("NAME", "os");
```

## contains

```TypeScript
contains(field: string, value: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that contains the specified value.

Currently, only RDB store supports this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. |
| value | string | Yes | Value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.contains("NAME", "os");
```

## distinct

```TypeScript
distinct(): DataSharePredicates
```

Creates a **DataSharePredicates** object to filter out duplicate data records.

Currently, only RDB store supports this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.equalTo("NAME", "Rose").distinct();
```

## endsWith

```TypeScript
endsWith(field: string, value: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that ends with the specified value.

Currently, only RDB store supports this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. |
| value | string | Yes | End value to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.endsWith("NAME", "os");
```

## glob

```TypeScript
glob(field: string, value: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that matches the specified wildcard expression.

Currently, only RDB store supports this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. |
| value | string | Yes | Wildcard expression to match.In the expression, '*' represents zero, one, or more digits or characters, and '?' represents a single digit or character. It is case sensitive. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.glob("NAME", "?h*g");
```

## groupBy

```TypeScript
groupBy(fields: Array<string>): DataSharePredicates
```

Creates a **DataSharePredicates** object group the records according to the specified fields.

Currently, only RDB store supports this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fields | Array&lt;string&gt; | Yes | Names of the columns by which the records are grouped. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.groupBy(["AGE", "NAME"]);
```

## indexedBy

```TypeScript
indexedBy(field: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to list data by the specified index. Before using this API, ensure that the index column exists.

Currently, only RDB store supports this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Name of the index column. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.indexedBy("SALARY_INDEX");
```

## inKeys

```TypeScript
inKeys(keys: Array<string>): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data whose keys are within the given range.

Currently, only the KVDB supports this **DataSharePredicates** object.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | Array&lt;string&gt; | Yes | Array of the keys to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.inKeys(["Lisa", "Rose"]);
```

## isNotNull

```TypeScript
isNotNull(field: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data whose value is not null.

Currently, both the RDB store and KV store support this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNotNull("NAME");
```

## isNull

```TypeScript
isNull(field: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data whose value is null.

Currently, both the RDB store and KV store support this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.isNull("NAME");
```

## prefixKey

```TypeScript
prefixKey(prefix: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data with the specified key prefix.

Currently, only the KVDB supports this **DataSharePredicates** object.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| prefix | string | Yes | Key prefix to match. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.prefixKey("NAME");
```

## unlike

```TypeScript
unlike(field: string, value: string): DataSharePredicates
```

Creates a **DataSharePredicates** object to match the data that does not match the specified wildcard expression.

Currently, both the RDB store and KV store support this predicate.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.DataShare.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Column name in the database table. |
| value | string | Yes | Wildcard expression to match.In the expression, '%' represents zero, one, or more digits or characters, and '_' represents a single digit or character. It is case insensitive. |

**Return value:**

| Type | Description |
| --- | --- |
| [DataSharePredicates](arkts-arkdata-datasharepredicates-datasharepredicates-c.md) | **DataSharePredicates** object created. |

**Examples**

```TypeScript
let predicates = new dataSharePredicates.DataSharePredicates();
predicates.unlike("NAME", "%os%");
```
