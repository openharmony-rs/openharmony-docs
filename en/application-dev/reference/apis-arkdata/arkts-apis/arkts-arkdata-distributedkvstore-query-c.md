# Query

Provides methods to create a **Query** object, which defines different data query criteria. A **Query** object supports a maximum of 256 predicates.

**Since:** 9

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## Modules to Import

```TypeScript
import { distributedKVStore } from '@kit.ArkData';
```

## and

```TypeScript
and(): Query
```

Creates a **Query** object with the AND condition.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value1');
      query.and();
      query.notEqualTo('field', 'value2');
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## beginGroup

```TypeScript
beginGroup(): Query
```

Creates a **Query** object for a query condition group with a left parenthesis.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.beginGroup();
      query.isNotNull('field');
      query.endGroup();
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## constructor

```TypeScript
constructor()
```

Defines a constructor used to create a **Query** instance.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

## deviceId

```TypeScript
deviceId(deviceId: string): Query
```

Creates a **Query** object with the device ID as the key prefix.

> **NOTE:** 
> 
> **deviceId** can be obtained by
> [deviceManager.getAvailableDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-distributeddevicemanager-devicemanager-i.md#getavailabledevicelistsync)
> .
> 
> For details about how to obtain **deviceId**, see [sync()](arkts-arkdata-distributedkvstore-syncmode-e.md).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the device to be queried. This parameter cannot be left empty. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.deviceId('deviceId');
      console.info(`query is ${query.getSqlLike()}`);
    }
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## endGroup

```TypeScript
endGroup(): Query
```

Creates a **Query** object for a query condition group with a right parenthesis.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.beginGroup();
      query.isNotNull('field');
      query.endGroup();
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## equalTo

```TypeScript
equalTo(field: string, value: number | number | string | boolean): Query
```

Creates a **Query** object to match the specified field whose value is equal to the given value.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value | number &#124; number &#124; string &#124; boolean | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.equalTo('field', 'value');
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## getSqlLike

```TypeScript
getSqlLike(): string
```

Obtains the query statement of the **Query** object.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the query statement obtained. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      let sql1 = query.getSqlLike();
      console.info(`GetSqlLike sql= ${sql1}`);
    }
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## greaterThan

```TypeScript
greaterThan(field: string, value: number | number | string | boolean): Query
```

Creates a **Query** object to match the specified field whose value is greater than the specified value.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Indicates the field, which cannot contain ^. |
| value | number &#124; number &#124; string &#124; boolean | Yes | Indicates the value to be compared. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.greaterThan('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## greaterThanOrEqualTo

```TypeScript
greaterThanOrEqualTo(field: string, value: number | number | string): Query
```

Creates a **Query** object to match the specified field whose value is greater than or equal to the specified value.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value | number &#124; number &#124; string | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.greaterThanOrEqualTo('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## inNumber

```TypeScript
inNumber(field: string, valueList: number[] | number[]): Query
```

Creates a **Query** object to match the specified field whose value is within the specified list of numbers.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| valueList | number[] &#124; number[] | Yes | List of numbers. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.inNumber('field', [0, 1]);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## inString

```TypeScript
inString(field: string, valueList: string[]): Query
```

Creates a **Query** object to match the specified field whose value is within the specified list of strings.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| valueList | string[] | Yes | List of strings. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.inString('field', ['test1', 'test2']);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## isNotNull

```TypeScript
isNotNull(field: string): Query
```

Creates a **Query** object to match the specified field whose value is not **null**.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.isNotNull('field');
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## isNull

```TypeScript
isNull(field: string): Query
```

Creates a **Query** object to match the specified field whose value is **null**.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.isNull('field');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## lessThan

```TypeScript
lessThan(field: string, value: number | number | string): Query
```

Creates a **Query** object to match the specified field whose value is less than the specified value.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value | number &#124; number &#124; string | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.lessThan('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## lessThanOrEqualTo

```TypeScript
lessThanOrEqualTo(field: string, value: number | number | string): Query
```

Creates a **Query** object to match the specified field whose value is less than or equal to the specified value.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value | number &#124; number &#124; string | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.lessThanOrEqualTo('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## like

```TypeScript
like(field: string, value: string): Query
```

Creates a **Query** object to match the specified field whose value is similar to the specified string.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value | string | Yes | String specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.like('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## limit

```TypeScript
limit(total: number, offset: number): Query
```

Creates a **Query** object to specify the number of records of the query result and where to start. This API must be called after the invocation of the **orderByAsc()**, **orderByDesc()**, and the query APIs of the **Query** object.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| total | number | Yes | Maximum number of results to query. The value must be a non-negative integer.<br>If the value is a negative number, the entire result set is queried. |
| offset | number | Yes | Start position of the query result. The value must be a non-negative integer.<br>If the value is a negative number, the entire result set is queried.<br>If **offset** exceeds the end of the result set, the query result is empty. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let total = 10;
let offset = 1;
try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.notEqualTo('field', 'value');
    query.limit(total, offset);
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## notEqualTo

```TypeScript
notEqualTo(field: string, value: number | number | string | boolean): Query
```

Creates a **Query** object to match the specified field whose value is not equal to the specified value.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value | number &#124; number &#124; string &#124; boolean | Yes | Value specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.notEqualTo('field', 'value');
    console.info(`query is ${query.getSqlLike()}`);
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## notInNumber

```TypeScript
notInNumber(field: string, valueList: number[] | number[]): Query
```

Creates a **Query** object to match the specified field whose value is not within the specified list of numbers.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| valueList | number[] &#124; number[] | Yes | List of numbers. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notInNumber('field', [0, 1]);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## notInString

```TypeScript
notInString(field: string, valueList: string[]): Query
```

Creates a **Query** object to match the specified field whose value is not within the specified list of strings.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| valueList | string[] | Yes | List of strings. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notInString('field', ['test1', 'test2']);
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## or

```TypeScript
or(): Query
```

Creates a **Query** object with the OR condition.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value1');
      query.or();
      query.notEqualTo('field', 'value2');
      console.info('query is ' + query.getSqlLike());
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## orderByAsc

```TypeScript
orderByAsc(field: string): Query
```

Creates a **Query** object to sort the query results in ascending order.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value');
      query.orderByAsc('field');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## orderByDesc

```TypeScript
orderByDesc(field: string): Query
```

Creates a **Query** object to sort the query results in descending order.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.notEqualTo('field', 'value');
      query.orderByDesc('field');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## prefixKey

```TypeScript
prefixKey(prefix: string): Query
```

Creates a **Query** object with a specified key prefix.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| prefix | string | Yes | Key prefix, which cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.prefixKey('$.name');
      query.prefixKey('0');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## reset

```TypeScript
reset(): Query
```

Resets the **Query** object.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object reset. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let query: distributedKVStore.Query | null = new distributedKVStore.Query();
  if (query != null) {
    query.equalTo('key', 'value');
    console.info('query is ' + query.getSqlLike());
    query.reset();
    console.info('query is ' + query.getSqlLike());
  }
  query = null;
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## setSuggestIndex

```TypeScript
setSuggestIndex(index: string): Query
```

Creates a **Query** object with an index preferentially used for query.

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| index | string | Yes | Index to set, which cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.setSuggestIndex('$.name');
      query.setSuggestIndex('0');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## unlike

```TypeScript
unlike(field: string, value: string): Query
```

Creates a **Query** object to match the specified field whose value is not similar to the specified string.

> **NOTE:** 
> 
> This API should be used together with [Schema](arkts-arkdata-distributedkvstore-schema-c.md).
> 
> For details about how to use **Schema** to create a database, see the example of creating and obtaining a KV
> store using the **getKVStore()** method in
> [Persisting KV Store Data](../../../database/data-persistence-by-kv-store.md#how-to-develop).

**Since:** 9

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| field | string | Yes | Field to match. It cannot contain '^'. If the value contains '^', the predicate becomes invalid and all data in the KV store will be returned. |
| value | string | Yes | String specified. |

**Return value:**

| Type | Description |
| --- | --- |
| [Query](arkts-arkdata-distributedkvstore-query-c.md) | **Query** object created. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error.Possible causes:1.Mandatory parameters are left unspecified;<br>2.Incorrect parameters types; <br>3.Parameter verification failed. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

try {
    let query: distributedKVStore.Query | null = new distributedKVStore.Query();
    if (query != null) {
      query.unlike('field', 'value');
      console.info(`query is ${query.getSqlLike()}`);
    }
    query = null;
} catch (err) {
    let error = err as BusinessError;
    console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```
