# @ohos.data.distributedKVStore (Distributed KV Store) (System API)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @ding_dong_dong-->
<!--Designer: @ding_dong_dong-->
<!--Tester: @logic42-->
<!--Adviser: @ge-yafang-->
<!-- md-trans-meta sourceCommit=315af7fbe1ff3251dfebf4c4e58304dd13ed2f09 translatedAt=2026-09-15T14:13:00.113Z pushedAt=2026-09-16T07:50:15.760Z -->

The **distributedKVStore** module implements collaboration between databases for different devices that form a Super Device. You can use the APIs provided by this module to save application data to a distributed key-value (KV) store and perform operations, such as adding, deleting, modifying, querying, and synchronizing data in distributed KV stores.

The **distributedKVStore** module provides the following functionalities:

- [KVManager](js-apis-distributedKVStore.md#kvmanager): provides a **KVManager** instance to obtain KV store information.
- [KVStoreResultSet](js-apis-distributedKVStore.md#kvstoreresultset): provides APIs for accessing the results obtained from a KV store.
- [Query](js-apis-distributedKVStore.md#query): provides APIs for setting predicates for data query.
- [SingleKVStore](#singlekvstore): provides APIs for querying and synchronizing data in single KV stores. The single KV stores manage data without distinguishing devices.
- [DeviceKVStore](#devicekvstore): provides APIs for querying and synchronizing data in device KV stores. This class inherits from [SingleKVStore](#singlekvstore). The device KV stores manage data by device.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.data.distributedKVStore](js-apis-distributedKVStore.md).

## Modules to Import

```ts
import { distributedKVStore } from '@kit.ArkData';
```

## SingleKVStore

Provides APIs for data management in a single KV store, such as adding data, deleting data, and subscribing to data changes or data sync completion events.

Before calling **SingleKVStore** APIs, you need to use [getKVStore](js-apis-distributedKVStore.md#getkvstore) to create a **SingleKVStore** instance.

### putBatch

putBatch(value: Array&lt;ValuesBucket&gt;, callback: AsyncCallback&lt;void&gt;): void

Writes key-value pairs in batches. Each **ValuesBucket** object contains a key and a value. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name  | Type                                                    | Mandatory| Description              |
| -------- | ------------------------------------------------------------ | ---- | ------------------ |
| value    | Array&lt;[ValuesBucket](js-apis-data-valuesBucket.md#valuesbucket)&gt; | Yes  | Data to write.|
| callback | AsyncCallback&lt;void&gt;                                     | Yes   | Callback function. If the operation succeeds, err is undefined; otherwise, err is an error object.         |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit. <br> Applicable versions: 10+ |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ValuesBucket } from '@kit.ArkData';

try {
  let bucket1: ValuesBucket = {key: 'name', value: 'LiSi'};
  let bucket2: ValuesBucket = {key: 'age', value: 20};
  let bucket3: ValuesBucket = {key: 'deposits', value: 12.34};
  let people: Array<ValuesBucket> = new Array(bucket1, bucket2, bucket3);
  kvStore.putBatch(people, (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put batch. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting batch');
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to do putBatch error. Code: ${error.code}, message: ${error.message}`);
}
```

### putBatch

putBatch(value: Array&lt;ValuesBucket&gt;): Promise&lt;void&gt;

Writes key-value pairs in batches. Each **ValuesBucket** object contains a key and a value. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.KVStore.Core

**Parameters**

| Name| Type                                                    | Mandatory| Description              |
| ------ | ------------------------------------------------------------ | ---- | ------------------ |
| value  | Array&lt;[ValuesBucket](js-apis-data-valuesBucket.md#valuesbucket)&gt; | Yes  | Data to write.|

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types.|
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit. <br> Applicable versions: 10+ |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';
import { ValuesBucket } from '@kit.ArkData';

try {
  let bucket1: ValuesBucket = {key: 'name', value: 'LiSi'};
  let bucket2: ValuesBucket = {key: 'age', value: 20};
  let bucket3: ValuesBucket = {key: 'deposits', value: 12.34};
  let people: Array<ValuesBucket> = new Array(bucket1, bucket2, bucket3);
  kvStore.putBatch(people).then(() => {
    console.info(`Succeeded in putting batch`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to do putBatch error. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`Failed to do putBatch error. Code: ${error.code}, message: ${error.message}`);
}
```

### delete

delete(predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback&lt;void&gt;): void

Deletes KV pairs from this KV store. This API uses an asynchronous callback to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                    | Mandatory| Description                                           |
| ---------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes   | Filter indicator. Not allowed to be null. |
| callback   | AsyncCallback&lt;void&gt;                                    | Yes   | Callback function. If the operation succeeds, **err** is **undefined**; otherwise, **err** is an error object.                                      |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100003     | Database corrupted.                    |
| 15100005    | Database or result set already closed. |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit. <br> Applicable versions: 10+ |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let predicates = new dataSharePredicates.DataSharePredicates();
  let arr = ['name'];
  predicates.inKeys(arr);
  kvStore.put('name', 'bob', (err: BusinessError) => {
    if (err) {
      console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in putting');
    if (kvStore != null) {
      kvStore.delete(predicates, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
        } else {
          console.info('Succeeded in deleting');
        }
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### delete

delete(predicates: dataSharePredicates.DataSharePredicates): Promise&lt;void&gt;

Deletes KV pairs from this KV store. This API uses a promise to return the result.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                    | Mandatory| Description                                           |
| ---------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes | Indicates the filter condition. It cannot be null. |

**Return value**

| Type               | Description                     |
| ------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                            |
| ------------ | ---------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100003     | Database corrupted.                      |
| 15100005     | Database or result set already closed.   |

For details about the error codes, see [RDB Error Codes](errorcode-data-rdb.md).

| ID| **Error Message**                                |
| ------------ | -------------------------------------------- |
| 14800047     | The WAL file size exceeds the default limit. <br> Applicable versions: 10+ |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let predicates = new dataSharePredicates.DataSharePredicates();
  let arr = ['name'];
  predicates.inKeys(arr);
  kvStore.put('name', 'bob').then(() => {
    console.info(`Succeeded in putting data`);
    if (kvStore != null) {
      kvStore.delete(predicates).then(() => {
        console.info('Succeeded in deleting');
      }).catch((err: BusinessError) => {
        console.error(`Failed to delete. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to put. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains the **KVStoreResultSet** object that matches the specified **Predicates** object. This API uses an asynchronous callback to return the result. After the result set is obtained, call [closeResultSet](js-apis-distributedKVStore.md#closeresultset) in a timely manner to close the result set and release resources.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                    | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes | Filter indicator. Not allowed to be null. |
| callback   | AsyncCallback&lt;[KVStoreResultSet](js-apis-distributedKVStore.md#kvstoreresultset)&gt;   | Yes  | Callback used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100001     | Over max limits. <br> Applicable versions: 10+ |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let predicates = new dataSharePredicates.DataSharePredicates();
  predicates.prefixKey('batch_test_string_key');
  kvStore.getResultSet(predicates, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
    if (err) {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing result set');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(predicates: dataSharePredicates.DataSharePredicates): Promise&lt;KVStoreResultSet&gt;

Obtains the **KVStoreResultSet** object that matches the specified **Predicates** object. This API uses a promise to return the result. After the result set is obtained, call [closeResultSet](js-apis-distributedKVStore.md#closeresultset) in a timely manner to close the result set and release resources.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                    | Mandatory| Description                                           |
| ---------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes | Filter indicator. Not allowed to be null. |

**Return value**

| Type                                                | Description                     |
| ---------------------------------------------------- | ------------------------- |
| Promise&lt;[KVStoreResultSet](js-apis-distributedKVStore.md#kvstoreresultset)&gt; | Promise used to return a **KVStoreResultSet** object. |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100001     | Over max limits. <br> Applicable versions: 10+ |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let predicates = new dataSharePredicates.DataSharePredicates();
  predicates.prefixKey('batch_test_string_key');
  kvStore.getResultSet(predicates).then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet).then(() => {
        console.info('Succeeded in closing result set');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });

} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

## DeviceKVStore

Provides APIs for querying and synchronizing data in a device KV store. This class inherits from **SingleKVStore**.

Data is distinguished by device in a device KV store. Each device can only write and modify its own data. Data of other devices is read-only and cannot be modified.

For example, a device KV store can be used to implement image sharing between devices. The images of other devices can be viewed, but not be modified or deleted.

Before calling **DeviceKVStore** APIs, you need to use [getKVStore](js-apis-distributedKVStore.md#getkvstore) to create a **DeviceKVStore** instance.

### getResultSet

getResultSet(predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains the **KVStoreResultSet** object on this device that matches the specified **Predicates** object. This API uses an asynchronous callback to return the result. After the result set is obtained, call [closeResultSet](js-apis-distributedKVStore.md#closeresultset) in a timely manner to close the result set and release resources.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes   | Filter condition. Not allowed to be null.              |
| callback   | AsyncCallback&lt;[KVStoreResultSet](js-apis-distributedKVStore.md#kvstoreresultset)&gt;   | Yes  | Callback used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100001     | Over max limits. <br> Applicable versions: 10+ |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let predicates = new dataSharePredicates.DataSharePredicates();
  predicates.prefixKey('batch_test_string_key');
  kvStore.getResultSet(predicates, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
    if (err) {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing result set');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(predicates: dataSharePredicates.DataSharePredicates): Promise&lt;KVStoreResultSet&gt;

Obtains the **KVStoreResultSet** object on this device that matches the specified **Predicates** object. This API uses a promise to return the result. After the result set is obtained, call [closeResultSet](js-apis-distributedKVStore.md#closeresultset) in a timely manner to close the result set and release resources.

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                        | Mandatory| Description                                           |
| ---------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes | Filter condition, not allowed to be null. |

**Return value**

| Type                                                | Description                     |
| ---------------------------------------------------- | ------------------------- |
| Promise&lt;[KVStoreResultSet](js-apis-distributedKVStore.md#kvstoreresultset)&gt; | Promise used to return the **KVStoreResultSet** object. |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100001     | Over max limits. <br> Applicable versions: 10+ |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let predicates = new dataSharePredicates.DataSharePredicates();
  predicates.prefixKey('batch_test_string_key');
  kvStore.getResultSet(predicates).then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet).then(() => {
        console.info('Succeeded in closing result set');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates, callback: AsyncCallback&lt;KVStoreResultSet&gt;): void

Obtains the **KVStoreResultSet** object on the specified device that matches the specified **Predicates** object. This API uses an asynchronous callback to return the result. After the result set is obtained, call [closeResultSet](js-apis-distributedKVStore.md#closeresultset) in a timely manner to close the result set and release resources.
> **NOTE**
>
> The **deviceId** is obtained by calling [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync API example](js-apis-distributedKVStore.md#sync).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                    | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------------ | ---- | ------------------------------------------------------------ |
| deviceId  | string                                                       | Required   | Network ID of the device whose data is to be queried. This parameter cannot be left empty.                                     |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Required   | Filter indicator. It is not allowed to be null.              |
| callback   | AsyncCallback&lt;[KVStoreResultSet](js-apis-distributedKVStore.md#kvstoreresultset)&gt;   | Yes  | Callback used to return the **KVStoreResultSet** object obtained.|

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100001     | Over max limits. <br> Applicable versions: 10+ |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let predicates = new dataSharePredicates.DataSharePredicates();
  predicates.prefixKey('batch_test_string_key');
  kvStore.getResultSet('localDeviceId', predicates, async (err: BusinessError, result: distributedKVStore.KVStoreResultSet) => {
    if (err) {
      console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
      return;
    }
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet, (err: BusinessError) => {
        if (err) {
          console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
          return;
        }
        console.info('Succeeded in closing result set');
      });
    }
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```

### getResultSet

getResultSet(deviceId: string, predicates: dataSharePredicates.DataSharePredicates): Promise&lt;KVStoreResultSet&gt;

Obtains the **KVStoreResultSet** object on the specified device that matches the specified **Predicates** object. This API uses a promise to return the result. After the result set is obtained, call [closeResultSet](js-apis-distributedKVStore.md#closeresultset) in a timely manner to close the result set and release resources.
> **NOTE**
>
> The **deviceId** is obtained by calling [deviceManager.getAvailableDeviceListSync](../apis-distributedservice-kit/js-apis-distributedDeviceManager.md#getavailabledevicelistsync).
> For details about how to obtain **deviceId**, see [sync API example](js-apis-distributedKVStore.md#sync).

**Model restriction**: This API can be used only in the stage model.

**System API**: This is a system API.

**System capability**: SystemCapability.DistributedDataManager.DataShare.Provider

**Parameters**

| Name    | Type                                                    | Mandatory| Description                                           |
| ---------- | ------------------------------------------------------------ | ---- | ----------------------------------------------- |
| deviceId  | string                                                       | Yes   | Network ID of the device whose data is to be queried. This parameter cannot be left empty.                                     |
| predicates | [dataSharePredicates.DataSharePredicates](js-apis-data-dataSharePredicates.md#datasharepredicates) | Yes   | Filter condition. It cannot be null. |

**Return value**

| Type                                                | Description                     |
| ---------------------------------------------------- | ------------------------- |
| Promise&lt;[KVStoreResultSet](js-apis-distributedKVStore.md#kvstoreresultset)&gt; | Promise used to return the **KVStoreResultSet** object. |

**Error codes**

For details about the error codes, see [Distributed KV Store Error Codes](errorcode-distributedKVStore.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| **Error Message**                          |
| ------------ | -------------------------------------- |
| 401          | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameters types. |
| 202          | Permission verification failed, application which is not a system application uses system API.|
| 15100001     | Over max limits. <br> Applicable versions: 10+ |
| 15100003     | Database corrupted.                    |
| 15100005     | Database or result set already closed. |

**Example**

```ts
import { dataSharePredicates } from '@kit.ArkData';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let resultSet: distributedKVStore.KVStoreResultSet;
  let predicates = new dataSharePredicates.DataSharePredicates();
  predicates.prefixKey('batch_test_string_key');
  kvStore.getResultSet('localDeviceId', predicates).then((result: distributedKVStore.KVStoreResultSet) => {
    console.info('Succeeded in getting result set');
    resultSet = result;
    if (kvStore != null) {
      kvStore.closeResultSet(resultSet).then(() => {
        console.info('Succeeded in closing result set');
      }).catch((err: BusinessError) => {
        console.error(`Failed to close resultset. Code: ${err.code}, message: ${err.message}`);
      });
    }
  }).catch((err: BusinessError) => {
    console.error(`Failed to get resultset. Code: ${err.code}, message: ${err.message}`);
  });
} catch (err) {
  let error = err as BusinessError;
  console.error(`An unexpected error occurred. Code: ${error.code}, message: ${error.message}`);
}
```