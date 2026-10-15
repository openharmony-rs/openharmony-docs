# DeviceKVStore

```TypeScript
interface DeviceKVStore extends KVStore
```

Provides APIs to query and synchronize data in a device KV store. This class inherits from [KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md). Data is distinguished by device in a device KV store. Each device can only write and modify its own data. Data of other devices is read-only and cannot be modified. For example, a device KV store can be used to implement image sharing between devices. The images of other devices can be viewed, but not be modified or deleted. Before calling any method in **DeviceKVStore**, you must use getKVStore to obtain a **DeviceKVStore** object.

**Inheritance/Implementation:** DeviceKVStore extends [KVStore](arkts-arkdata-distributeddata-kvstore-i.md)

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [DeviceKVStore](arkts-arkdata-distributedkvstore-devicekvstore-i.md)

<!--Device-distributedData-interface DeviceKVStore extends KVStore--><!--Device-distributedData-interface DeviceKVStore extends KVStore-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## Modules to Import

```TypeScript
```

<a id="closeresultset1"></a>

## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void
```

Closes the **KvStoreResultSet** object obtained by DeviceKVStore.getResultSet. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** closeResultSet

<!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void--><!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | Yes | **KvStoreResultSet** object to close. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
try {
    console.info('CloseResultSet success');
    let resultSet = null;
    kvStore.closeResultSet(resultSet, function (err, data) {
        if (err == undefined) {
            console.info('closeResultSet success');
        } else {
            console.error('closeResultSet fail');
        }
    });
}catch(e) {
    console.error('CloseResultSet e ' + e);
}
```

<a id="closeresultset2"></a>

## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet): Promise<void>
```

Closes the **KvStoreResultSet** object obtained by DeviceKVStore.getResultSet. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** closeResultSet

<!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet): Promise<void>--><!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | Yes | **KvStoreResultSet** object to close. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
try {
    console.info('CloseResultSet success');
    let resultSet = null;
    kvStore.closeResultSet(resultSet).then(() => {
        console.info('closeResultSet success');
    }).catch((err) => {
        console.error('closeResultSet fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('CloseResultSet e ' + e);
}
```

<a id="get1"></a>

## get

```TypeScript
get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void
```

Obtains a string value that matches the specified device ID and key. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [get](arkts-arkdata-distributedkvstore-devicekvstore-i.md#get)

<!--Device-DeviceKVStore-get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void--><!--Device-DeviceKVStore-get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| key | string | Yes | Key to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean &#124; string &#124; number &#124; Uint8Array&gt; | Yes | Callback used to return the value obtained. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try{
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async function (err,data) {
        console.info('put success');
        kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT, function (err,data) {
            console.info('get success');
        });
    })
}catch(e) {
    console.error('get e' + e);
}
```

<a id="get2"></a>

## get

```TypeScript
get(deviceId: string, key: string): Promise<boolean | string | number | Uint8Array>
```

Obtains a string value that matches the specified device ID and key. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [get](arkts-arkdata-distributedkvstore-devicekvstore-i.md#get)

<!--Device-DeviceKVStore-get(deviceId: string, key: string): Promise<boolean | string | number | Uint8Array>--><!--Device-DeviceKVStore-get(deviceId: string, key: string): Promise<boolean | string | number | Uint8Array>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| key | string | Yes | Key to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean &#124; string &#124; number &#124; Uint8Array&gt; | Promise used to return the string value that matches the given condition. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(async (data) => {
        console.info(' put success');
        kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT).then((data) => {
            console.info('get success');
        }).catch((err) => {
            console.error('get fail ' + JSON.stringify(err));
        });
    }).catch((error) => {
        console.error('put error' + error);
    });
} catch (e) {
    console.error('Get e ' + e);
}
```

<a id="getentries1"></a>

## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

Obtains all KV pairs that match the specified device ID and key prefix. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getEntries](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getentries)

<!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| keyPrefix | string | Yes | Key prefix to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Yes | Callback used to return the KV pairs obtained. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    console.info('entries: ' + entries);
    kvStore.putBatch(entries, async function (err,data) {
        console.info('putBatch success');
        kvStore.getEntries('localDeviceId', 'batch_test_string_key', function (err,entries) {
            console.info('getEntries success');
            console.info('entries.length: ' + entries.length);
            console.info('entries[0]: ' + JSON.stringify(entries[0]));
        });
    });
}catch(e) {
    console.error('PutBatch e ' + e);
}
```

<a id="getentries2"></a>

## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>
```

Obtains all KV pairs that match the specified device ID and key prefix. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getEntries](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getentries)

<!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| keyPrefix | string | Yes | Key prefix to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Promise used to return all the KV pairs that match the given condition. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    console.info('entries: ' + entries);
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
        kvStore.getEntries('localDeviceId', 'batch_test_string_key').then((entries) => {
            console.info('getEntries success');
            console.info('entries.length: ' + entries.length);
            console.info('entries[0]: ' + JSON.stringify(entries[0]));
            console.info('entries[0].value: ' + JSON.stringify(entries[0].value));
            console.info('entries[0].value.value: ' + entries[0].value.value);
        }).catch((err) => {
            console.error('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error('putBatch fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('PutBatch e ' + e);
}
```

<a id="getentries3"></a>

## getEntries

```TypeScript
getEntries(query: Query, callback: AsyncCallback<Entry[]>): void
```

Obtains the KV pairs that match the specified **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getEntries](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getentries)

<!--Device-DeviceKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Yes | Callback used to return the KV pairs obtained. |

**Examples**

```TypeScript
let kvStore;
try {
    var arr = new Uint8Array([21,31]);
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_bool_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.BYTE_ARRAY,
                value : arr
            }
        }
        entries.push(entry);
    }
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.info('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        query.deviceId('localDeviceId');
        kvStore.getEntries(query, function (err,entries) {
            console.info('getEntries success');
            console.info('entries.length: ' + entries.length);
            console.info('entries[0]: ' + JSON.stringify(entries[0]));
        });
    });
    console.info('GetEntries success');
}catch(e) {
    console.error('GetEntries e ' + e);
}
```

<a id="getentries4"></a>

## getEntries

```TypeScript
getEntries(query: Query): Promise<Entry[]>
```

Obtains the KV pairs that match the specified **Query** object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getEntries](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getentries)

<!--Device-DeviceKVStore-getEntries(query: Query): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(query: Query): Promise<Entry[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Promise used to return the KV pairs that match the specified **Query** object. |

**Examples**

```TypeScript
let kvStore;
try {
    var arr = new Uint8Array([21,31]);
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_bool_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.BYTE_ARRAY,
                value : arr
            }
        }
        entries.push(entry);
    }
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        kvStore.getEntries(query).then((entries) => {
            console.info('getEntries success');
        }).catch((err) => {
            console.error('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error('GetEntries putBatch fail ' + JSON.stringify(err))
    });
    console.info('GetEntries success');
}catch(e) {
    console.error('GetEntries e ' + e);
}
```

<a id="getentries5"></a>

## getEntries

```TypeScript
getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void
```

Obtains the KV pairs that match the specified device ID and **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getEntries](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getentries)

<!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Yes | Callback used to return the KV pairs that match the specified device ID and **Query** object. |

**Examples**

```TypeScript
let kvStore;
try {
    var arr = new Uint8Array([21,31]);
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_bool_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.BYTE_ARRAY,
                value : arr
            }
        }
        entries.push(entry);
    }
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.info('putBatch success');
        var query = new distributedData.Query();
        query.deviceId('localDeviceId');
        query.prefixKey("batch_test");
        kvStore.getEntries('localDeviceId', query, function (err,entries) {
            console.info('getEntries success');
            console.info('entries.length: ' + entries.length);
            console.info('entries[0]: ' + JSON.stringify(entries[0]));
        })
    });
    console.info('GetEntries success');
}catch(e) {
    console.error('GetEntries e ' + e);
}
```

<a id="getentries6"></a>

## getEntries

```TypeScript
getEntries(deviceId: string, query: Query): Promise<Entry[]>
```

Obtains the KV pairs that match the specified device ID and **Query** object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getEntries](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getentries)

<!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query): Promise<Entry[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Promise used to return the KV pairs that match the specified device ID and **Query** object. |

**Examples**

```TypeScript
let kvStore;
try {
    var arr = new Uint8Array([21,31]);
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_bool_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.BYTE_ARRAY,
                value : arr
            }
        }
        entries.push(entry);
    }
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
        var query = new distributedData.Query();
        query.deviceId('localDeviceId');
        query.prefixKey("batch_test");
        kvStore.getEntries('localDeviceId', query).then((entries) => {
            console.info('getEntries success');
        }).catch((err) => {
            console.error('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error('putBatch fail ' + JSON.stringify(err));
    });
    console.info('GetEntries success');
}catch(e) {
    console.error('GetEntries e ' + e);
}
```

<a id="getresultset1"></a>

## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void
```

Obtains a **KvStoreResultSet** object that matches the specified device ID and key prefix. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSet](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultset)

<!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| keyPrefix | string | Yes | Key prefix to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Yes | Callback used to return the **KvStoreResultSet** object that matches the specified device ID and key prefix. |

**Examples**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('localDeviceId', 'batch_test_string_key', async function (err, result) {
        console.info('getResultSet succeed.');
        resultSet = result;
        kvStore.closeResultSet(resultSet, function (err, data) {
            console.info('closeResultSet success');
        })
    });
}catch(e) {
    console.error('GetResultSet e ' + e);
}
```

<a id="getresultset2"></a>

## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string): Promise<KvStoreResultSet>
```

Obtains a **KvStoreResultSet** object that matches the specified device ID and key prefix. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSet](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultset)

<!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string): Promise<KvStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string): Promise<KvStoreResultSet>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| keyPrefix | string | Yes | Key prefix to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Promise used to return the **KvStoreResultSet** object that matches the specified device ID and key prefix. |

**Examples**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('localDeviceId', 'batch_test_string_key').then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + JSON.stringify(err));
    });
    kvStore.closeResultSet(resultSet).then((err) => {
        console.info('closeResultSet success');
    }).catch((err) => {
        console.error('closeResultSet fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('GetResultSet e ' + e);
}
```

<a id="getresultset3"></a>

## getResultSet

```TypeScript
getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void
```

Obtains a **KvStoreResultSet** object that matches the specified **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSet](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultset)

<!--Device-DeviceKVStore-getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Yes | Callback used to return the **KvStoreResultSet** object obtained. |

**Examples**

```TypeScript
let kvStore;
try {
    let resultSet;
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries, async function (err, data) {
        console.info('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        query.deviceId('localDeviceId');
        kvStore.getResultSet(query, async function (err, result) {
            console.info('getResultSet succeed.');
            resultSet = result;
            kvStore.closeResultSet(resultSet, function (err, data) {
                console.info('closeResultSet success');
            })
        });
    });
} catch(e) {
    console.error('GetResultSet e ' + e);
}
```

<a id="getresultset4"></a>

## getResultSet

```TypeScript
getResultSet(query: Query): Promise<KvStoreResultSet>
```

Obtains a **KvStoreResultSet** object that matches the specified **Query** object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSet](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultset)

<!--Device-DeviceKVStore-getResultSet(query: Query): Promise<KvStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(query: Query): Promise<KvStoreResultSet>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Promise used to return the **KvStoreResultSet** object that matches the specified **Query** object. |

**Examples**

```TypeScript
let kvStore;
try {
    let resultSet;
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
    }).catch((err) => {
        console.error('putBatch fail ' + err);
    });
    const query = new distributedData.Query();
    query.deviceId('localDeviceId');
    query.prefixKey("batch_test");
    console.info("GetResultSet " + query.getSqlLike());
    kvStore.getResultSet(query).then((result) => {
        console.info('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('getResultSet failed: ' + JSON.stringify(err));
    });
    kvStore.closeResultSet(resultSet).then((err) => {
        console.info('closeResultSet success');
    }).catch((err) => {
        console.error('closeResultSet fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('GetResultSet e ' + e);
}
```

<a id="getresultset5"></a>

## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KvStoreResultSet>): void
```

Obtains a **KvStoreResultSet** object that matches the specified device ID and **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSet](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultset)

<!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Yes | Callback used to return the **KvStoreResultSet** object that matches the specified device ID and **Query** object. |

**Examples**

```TypeScript
let kvStore;
try {
    let resultSet;
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries, async function (err, data) {
        console.info('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        kvStore.getResultSet('localDeviceId', query, async function (err, result) {
            console.info('getResultSet succeed.');
            resultSet = result;
            kvStore.closeResultSet(resultSet, function (err, data) {
                console.info('closeResultSet success');
            })
        });
    });
} catch(e) {
    console.error('GetResultSet e ' + e);
}
```

<a id="getresultset6"></a>

## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query): Promise<KvStoreResultSet>
```

Obtains a **KvStoreResultSet** object that matches the specified device ID and **Query** object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSet](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultset)

<!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query): Promise<KvStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query): Promise<KvStoreResultSet>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Promise used to return the **KvStoreResultSet** object that matches the specified device ID and **Query** object. |

**Examples**

```TypeScript
let kvStore;
try {
    let resultSet;
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries).then(async (err) => {
        console.info('GetResultSet putBatch success');
    }).catch((err) => {
        console.error('PutBatch putBatch fail ' + JSON.stringify(err));
    });
    const query = new distributedData.Query();
    query.prefixKey("batch_test");
    kvStore.getResultSet('localDeviceId', query).then((result) => {
        console.info('GetResultSet getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.error('GetResultSet getResultSet failed: ' + JSON.stringify(err));
    });
    query.deviceId('localDeviceId');
    console.info("GetResultSet " + query.getSqlLike());
    kvStore.closeResultSet(resultSet).then((err) => {
        console.info('GetResultSet closeResultSet success');
    }).catch((err) => {
        console.error('GetResultSet closeResultSet fail ' + JSON.stringify(err));
    });

}catch(e) {
    console.error('GetResultSet e ' + e);
}
```

<a id="getresultsize1"></a>

## getResultSize

```TypeScript
getResultSize(query: Query, callback: AsyncCallback<number>): void
```

Obtains the number of results that match the specified **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSize](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultsize)

<!--Device-DeviceKVStore-getResultSize(query: Query, callback: AsyncCallback<number>): void--><!--Device-DeviceKVStore-getResultSize(query: Query, callback: AsyncCallback<number>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the number of results obtained. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries, async function (err, data) {
        console.info('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        query.deviceId('localDeviceId');
        kvStore.getResultSize(query, async function (err, resultSize) {
            console.info('getResultSet succeed.');
        });
    });
} catch(e) {
    console.error('GetResultSize e ' + e);
}
```

<a id="getresultsize2"></a>

## getResultSize

```TypeScript
getResultSize(query: Query): Promise<number>
```

Obtains the number of results that match the specified **Query** object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSize](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultsize)

<!--Device-DeviceKVStore-getResultSize(query: Query): Promise<number>--><!--Device-DeviceKVStore-getResultSize(query: Query): Promise<number>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of results obtained. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
    }).catch((err) => {
        console.error('putBatch fail ' + JSON.stringify(err));
    });
    const query = new distributedData.Query();
    query.prefixKey("batch_test");
    query.deviceId('localDeviceId');
    kvStore.getResultSize(query).then((resultSize) => {
        console.info('getResultSet succeed.');
    }).catch((err) => {
        console.error('getResultSet failed: ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('GetResultSize e ' + e);
}
```

<a id="getresultsize3"></a>

## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void
```

Obtains the number of results that match the specified device ID and **Query** object. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSize](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultsize)

<!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void--><!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | Callback used to return the number of results obtained. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries, async function (err, data) {
        console.info('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        kvStore.getResultSize('localDeviceId', query, async function (err, resultSize) {
            console.info('getResultSet succeed.');
        });
    });
} catch(e) {
    console.error('GetResultSize e ' + e);
}
```

<a id="getresultsize4"></a>

## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query): Promise<number>
```

Obtains the number of results that match the specified device ID and **Query** object. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getResultSize](arkts-arkdata-distributedkvstore-devicekvstore-i.md#getresultsize)

<!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query): Promise<number>--><!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query): Promise<number>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | Yes | **Query** object to match. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Promise used to return the number of results obtained. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
    }).catch((err) => {
        console.error('putBatch fail ' + JSON.stringify(err));
    });
    var query = new distributedData.Query();
    query.prefixKey("batch_test");
    kvStore.getResultSize('localDeviceId', query).then((resultSize) => {
        console.info('getResultSet succeed.');
    }).catch((err) => {
        console.error('getResultSet failed: ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('GetResultSize e ' + e);
}
```

<a id="off1"></a>

## off

```TypeScript
off(event: 'dataChange', listener?: Callback<ChangeNotification>): void
```

Unsubscribes from data changes.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** off

<!--Device-DeviceKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void--><!--Device-DeviceKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event type. The value is **dataChange**, which indicates data changes. |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeNotification](arkts-arkdata-distributeddata-changenotification-i.md)&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks for data changes will be unregistered. |

**Examples**

```TypeScript
let kvStore;
class KvstoreModel {
    call(data) {
        console.info("dataChange: " + data);
    }
    subscribeDataChange() {
        if (kvStore != null) {
            kvStore.on('dataChange', distributedData.SubscribeType.SUBSCRIBE_TYPE_REMOTE, this.call);
        }
    }
    unsubscribeDataChange() {
        if (kvStore != null) {
            kvStore.off('dataChange', this.call);
        }
    }
}
```

<a id="off2"></a>

## off

```TypeScript
off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void
```

Unsubscribes from sync completion events.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** off

<!--Device-DeviceKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void--><!--Device-DeviceKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'syncComplete' | Yes | Event type. The value is **syncComplete**, which indicates a sync completion event. |
| syncCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks for data changes will be unregistered. |

**Examples**

```TypeScript
let kvStore;
class KvstoreModel {
    call(data) {
        console.info("syncComplete: " + data);
    }
    subscribeSyncComplete() {
        if (kvStore != null) {
            kvStore.on('syncComplete', this.call);
        }
    }
    unsubscribeSyncComplete() {
        if (kvStore != null) {
            kvStore.off('syncComplete', this.call);
        }
    }
}
```

<a id="on1"></a>

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void
```

Subscribes to data changes of the specified type.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** on

<!--Device-DeviceKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void--><!--Device-DeviceKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'dataChange' | Yes | Event type. The value is **dataChange**, which indicates data changes. |
| type | [SubscribeType](arkts-arkdata-distributeddata-subscribetype-e.md) | Yes | Type of data change. |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeNotification](arkts-arkdata-distributeddata-changenotification-i.md)&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
kvStore.on('dataChange', distributedData.SubscribeType.SUBSCRIBE_TYPE_LOCAL, function (data) {
    console.info("dataChange callback call data: " + JSON.stringify(data));
});
```

<a id="on2"></a>

## on

```TypeScript
on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void
```

Subscribes to sync completion events.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** on

<!--Device-DeviceKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void--><!--Device-DeviceKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'syncComplete' | Yes | Event type. The value is **syncComplete**, which indicates a sync completion event. |
| syncCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | Yes | Callback used to return a sync completion event. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_FLOAT_ELEMENT = 'key_test_float';
const VALUE_TEST_FLOAT_ELEMENT = 321.12;
try {
    kvStore.on('syncComplete', function (data) {
        console.info('syncComplete ' + data)
    });
    kvStore.put(KEY_TEST_FLOAT_ELEMENT, VALUE_TEST_FLOAT_ELEMENT).then((data) => {
        console.info('syncComplete put success');
    }).catch((error) => {
        console.error('syncComplete put fail ' + error);
    });
}catch(e) {
    console.error('syncComplete put e ' + e);
}
```

<a id="removedevicedata1"></a>

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void
```

Deletes data of the specified device from this KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** removeDeviceData

<!--Device-DeviceKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void--><!--Device-DeviceKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-string-001';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async function (err,data) {
        console.info('RemoveDeviceData  put success');
        const deviceid = 'no_exist_device_id';
        kvStore.removeDeviceData(deviceid, async function (err,data) {
            if (err == undefined) {
                console.info('removeDeviceData success');
            } else {
                console.error('removeDeviceData fail');
                kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT, async function (err,data) {
                    console.info('RemoveDeviceData get success');
                });
            }
        });
    });
}catch(e) {
    console.error('RemoveDeviceData e ' + e);
}
```

<a id="removedevicedata2"></a>

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string): Promise<void>
```

Deletes data of the specified device from this KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** removeDeviceData

<!--Device-DeviceKVStore-removeDeviceData(deviceId: string): Promise<void>--><!--Device-DeviceKVStore-removeDeviceData(deviceId: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceId | string | Yes | ID of the target device. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-string-001';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((err) => {
        console.info('RemoveDeviceData put success');
    }).catch((err) => {
        console.error('RemoveDeviceData put fail ' + JSON.stringify(err));
    });
    const deviceid = 'no_exist_device_id';
    kvStore.removeDeviceData(deviceid).then((err) => {
        console.info('removeDeviceData success');
    }).catch((err) => {
        console.error('removeDeviceData fail ' + JSON.stringify(err));
    });
    kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT).then((data) => {
        console.info('RemoveDeviceData get success data:' + data);
    }).catch((err) => {
        console.error('RemoveDeviceData get fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('RemoveDeviceData e ' + e);
}
```

## sync

```TypeScript
sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void
```

Synchronizes the KV store manually.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** sync

**Required permissions:** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void--><!--Device-DeviceKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceIds | string[] | Yes | **networkId**s of the devices to be synchronized. |
| mode | [SyncMode](arkts-arkdata-distributeddata-syncmode-e.md) | Yes | Sync mode. |
| delayMs | number | No | Delay time allowed, in milliseconds. The default value is **0**. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';
const deviceIds = ['networkId1', 'networkId2'];
try {
  kvStore.on('syncComplete', function (data) {
    console.info('Sync dataChange');
  });
  kvStore.put(KEY_TEST_SYNC_ELEMENT + 'testSync101', VALUE_TEST_SYNC_ELEMENT, function (err, data) {
    if (err != undefined) {
      console.error("put err: " + JSON.stringify(err));
      return;
    }
    console.info('Succeeded in putting data');
    const mode = distributedData.SyncMode.PULL_ONLY;
    kvStore.sync(deviceIds, mode, 1000);
  });
} catch (e) {
  console.error('Sync e' + e);
}
```
