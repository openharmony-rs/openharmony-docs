# KVStore

```TypeScript
interface KVStore
```

Provides APIs to manage data in a KV store, for example, adding or deleting data and subscribing to data changes or completion of data sync. Before calling any method in **KVStore**, you must use getKVStore to obtain a **KVStore** object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** SingleKVStore

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core @version 1

## Modules to Import

```TypeScript
```

## commit

```TypeScript
commit(callback: AsyncCallback<void>): void
```

Commits the transaction in this KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** commit

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
try {
    kvStore.commit(function (err,data) {
        if (err == undefined) {
            console.info('commit success');
        } else {
            console.error('commit fail');
        }
    });
}catch(e) {
    console.error('Commit e ' + e);
}
```

<a id="commit-1"></a>

## commit

```TypeScript
commit(): Promise<void>
```

Commits the transaction in this KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** commit

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
try {
    kvStore.commit().then(async (err) => {
        console.info('commit success');
    }).catch((err) => {
        console.error('commit fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('Commit e ' + e);
}
```

## delete

```TypeScript
delete(key: string, callback: AsyncCallback<void>): void
```

Deletes a KV pair from this KV store. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** delete

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the KV pair to delete. It cannot be empty, and the length cannot exceed [MAX_KEY_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, function (err,data) {
        if (err != undefined) {
            console.error("put err: " + JSON.stringify(err));
            return;
        }
        console.info("put success");
        kvStore.delete(KEY_TEST_STRING_ELEMENT, function (err,data) {
            if (err != undefined) {
                console.error("delete err: " + JSON.stringify(err));
                return;
            }
            console.info("delete success");
        });
    });
}catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

<a id="delete-1"></a>

## delete

```TypeScript
delete(key: string): Promise<void>
```

Deletes a KV pair from this KV store. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** delete

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the KV pair to delete. It cannot be empty, and the length cannot exceed [MAX_KEY_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((data) => {
        console.info("put success: " + JSON.stringify(data));
        kvStore.delete(KEY_TEST_STRING_ELEMENT).then((data) => {
            console.info("delete success");
        }).catch((err) => {
            console.error("delete err: " + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error("put err: " + JSON.stringify(err));
    });
}catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

## deleteBatch

```TypeScript
deleteBatch(keys: string[], callback: AsyncCallback<void>): void
```

Deletes KV pairs in batches from this KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** deleteBatch

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | string[] | Yes | KV pairs to delete in batches. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    let keys = [];
    for (var i = 0; i < 5; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
        keys.push(key + i);
    }
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.info('putBatch success');
        kvStore.deleteBatch(keys, async function (err,data) {
            console.info('deleteBatch success');
        });
    });
}catch(e) {
    console.error('DeleteBatch e ' + e);
}
```

<a id="deletebatch-1"></a>

## deleteBatch

```TypeScript
deleteBatch(keys: string[]): Promise<void>
```

Deletes KV pairs in batches from this KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** deleteBatch

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| keys | string[] | Yes | KV pairs to delete in batches. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
try {
    let entries = [];
    let keys = [];
    for (var i = 0; i < 5; i++) {
        var key = 'batch_test_string_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
        keys.push(key + i);
    }
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
        kvStore.deleteBatch(keys).then((err) => {
            console.info('deleteBatch success');
        }).catch((err) => {
            console.error('deleteBatch fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error('putBatch fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('DeleteBatch e ' + e);
}
```

## enableSync

```TypeScript
enableSync(enabled: boolean, callback: AsyncCallback<void>): void
```

Sets data sync, which can be enabled or disabled. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** enableSync

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable data sync. The value **true** means to enable data sync, and **false** means the opposite. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
try {
    kvStore.enableSync(true, function (err,data) {
        if (err == undefined) {
            console.info('enableSync success');
        } else {
            console.error('enableSync fail');
        }
    });
}catch(e) {
    console.error('EnableSync e ' + e);
}
```

<a id="enablesync-1"></a>

## enableSync

```TypeScript
enableSync(enabled: boolean): Promise<void>
```

Sets data sync, which can be enabled or disabled. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** enableSync

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| enabled | boolean | Yes | Whether to enable data sync. The value **true** means to enable data sync, and **false** means the opposite. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
try {
    kvStore.enableSync(true).then((err) => {
        console.info('enableSync success');
    }).catch((err) => {
        console.error('enableSync fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('EnableSync e ' + e);
}
```

## off

```TypeScript
off(event: 'dataChange', listener?: Callback<ChangeNotification>): void
```

Unsubscribes from data changes.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** off

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

<a id="off-1"></a>

## off

```TypeScript
off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void
```

Unsubscribes from sync completion events.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** off

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

## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void
```

Subscribes to data changes of the specified type.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** on

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

<a id="on-1"></a>

## on

```TypeScript
on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void
```

Subscribes to sync completion events.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** on

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'syncComplete' | Yes | Event type. The value is **syncComplete**, which indicates a sync completion event. |
| syncCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | Yes | Callback used to return a sync completion event. |

**Examples**

```TypeScript
let kvStore;
kvStore.on('syncComplete', function (data) {
    console.info("callback call data: " + data);
});
```

## put

```TypeScript
put(key: string, value: Uint8Array | string | number | boolean, callback: AsyncCallback<void>): void
```

Adds a KV pair of the specified type to this KV store. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** put

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the KV pair to add. It cannot be empty, and the length cannot exceed [MAX_KEY_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| value | Uint8Array &#124; string &#124; number &#124; boolean | Yes | Value of the KV pair to add. The value type can be Uint8Array, number, string, or boolean. A value of the Uint8Array or string type cannot exceed [MAX_VALUE_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, function (err,data) {
        if (err != undefined) {
            console.error("put err: " + JSON.stringify(err));
            return;
        }
        console.info("put success");
    });
}catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

<a id="put-1"></a>

## put

```TypeScript
put(key: string, value: Uint8Array | string | number | boolean): Promise<void>
```

Adds a KV pair of the specified type to this KV store. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** put

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | Key of the KV pair to add. It cannot be empty, and the length cannot exceed [MAX_KEY_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| value | Uint8Array &#124; string &#124; number &#124; boolean | Yes | Value of the KV pair to add. The value type can be Uint8Array, number, string, or boolean. A value of the Uint8Array or string type cannot exceed [MAX_VALUE_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((data) => {
        console.info("put success: " + JSON.stringify(data));
    }).catch((err) => {
        console.error("put err: " + JSON.stringify(err));
    });
}catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

## putBatch

```TypeScript
putBatch(entries: Entry[], callback: AsyncCallback<void>): void
```

Inserts KV pairs in batches to this KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** putBatch

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| entries | [Entry](arkts-arkdata-distributeddata-entry-i.md)[] | Yes | KV pairs to insert in batches. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

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
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.info('putBatch success');
        kvStore.getEntries('batch_test_string_key', function (err,entries) {
            console.info('getEntries success');
            console.info('entries.length: ' + entries.length);
            console.info('entries[0]: ' + JSON.stringify(entries[0]));
        });
    });
}catch(e) {
    console.info('PutBatch e ' + JSON.stringify(e));
}
```

<a id="putbatch-1"></a>

## putBatch

```TypeScript
putBatch(entries: Entry[]): Promise<void>
```

Inserts KV pairs in batches to this KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** putBatch

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| entries | [Entry](arkts-arkdata-distributeddata-entry-i.md)[] | Yes | KV pairs to insert in batches. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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
    console.info('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.info('putBatch success');
        kvStore.getEntries('batch_test_string_key').then((entries) => {
            console.info('getEntries success');
            console.info('PutBatch ' + JSON.stringify(entries));
        }).catch((err) => {
            console.error('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error('putBatch fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.info('PutBatch e ' + JSON.stringify(e));
}
```

## rollback

```TypeScript
rollback(callback: AsyncCallback<void>): void
```

Rolls back the transaction in this KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** rollback

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
try {
    kvStore.rollback(function (err,data) {
        if (err == undefined) {
            console.info('commit success');
        } else {
            console.error('commit fail');
        }
    });
}catch(e) {
    console.error('Rollback e ' + e);
}
```

<a id="rollback-1"></a>

## rollback

```TypeScript
rollback(): Promise<void>
```

Rolls back the transaction in this KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** rollback

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
try {
    kvStore.rollback().then(async (err) => {
        console.info('rollback success');
    }).catch((err) => {
        console.error('rollback fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('Rollback e ' + e);
}
```

## setSyncRange

```TypeScript
setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback<void>): void
```

Sets the data sync range. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** setSyncRange

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localLabels | string[] | Yes | Sync labels set for the local device. |
| remoteSupportLabels | string[] | Yes | Sync labels set for remote devices. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
try {
    const localLabels = ['A', 'B'];
    const remoteSupportLabels = ['C', 'D'];
    kvStore.setSyncRange(localLabels, remoteSupportLabels, function (err,data) {
        console.info('SetSyncRange put success');
    });
}catch(e) {
    console.error('SetSyncRange e ' + e);
}
```

<a id="setsyncrange-1"></a>

## setSyncRange

```TypeScript
setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise<void>
```

Sets the data sync range. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** setSyncRange

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| localLabels | string[] | Yes | Sync labels set for the local device. |
| remoteSupportLabels | string[] | Yes | Sync labels set for remote devices. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
try {
    const localLabels = ['A', 'B'];
    const remoteSupportLabels = ['C', 'D'];
    kvStore.setSyncRange(localLabels, remoteSupportLabels).then((err) => {
        console.info('setSyncRange success');
    }).catch((err) => {
        console.error('delete fail ' + err);
    });
}catch(e) {
    console.error('SetSyncRange e ' + e);
}
```

## startTransaction

```TypeScript
startTransaction(callback: AsyncCallback<void>): void
```

Starts the transaction in this KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** startTransaction

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
function putBatchString(len, prefix) {
    let entries = [];
    for (var i = 0; i < len; i++) {
        var entry = {
            key : prefix + i,
            value : {
                type : distributedData.ValueType.STRING,
                value : 'batch_test_string_value'
            }
        }
        entries.push(entry);
    }
    return entries;
}
try {
    var count = 0;
    kvStore.on('dataChange', 0, function (data) {
        console.info('startTransaction 0' + data)
        count++;
    });
    kvStore.startTransaction(async function (err,data) {
        console.info('startTransaction success');
        let entries = putBatchString(10, 'batch_test_string_key');
        console.info('entries: ' + JSON.stringify(entries));
        kvStore.putBatch(entries, async function (err,data) {
            console.info('putBatch success');
        });
    });
}catch(e) {
    console.error('startTransaction e ' + e);
}
```

<a id="starttransaction-1"></a>

## startTransaction

```TypeScript
startTransaction(): Promise<void>
```

Starts the transaction in this KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** startTransaction

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvStore;
try {
    var count = 0;
    kvStore.on('dataChange', distributedData.SubscribeType.SUBSCRIBE_TYPE_ALL, function (data) {
        console.info('startTransaction ' + JSON.stringify(data));
        count++;
    });
    kvStore.startTransaction().then(async (err) => {
        console.info('startTransaction success');
    }).catch((err) => {
        console.error('startTransaction fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.error('startTransaction e ' + e);
}
```
