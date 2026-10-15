# KVManager

```TypeScript
interface KVManager
```

Creates a **KVManager** object to obtain KV store information. Before calling any method in **KVManager**, you must use [createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md#createkvmanager1) to create a **KVManager** object.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [KVManager](arkts-arkdata-distributedkvstore-kvmanager-i.md)

<!--Device-distributedData-interface KVManager--><!--Device-distributedData-interface KVManager-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core @version 1

## Modules to Import

```TypeScript
```

<a id="closekvstore1"></a>

## closeKVStore

```TypeScript
closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback<void>): void
```

Closes a KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [closeKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#closekvstore)

<!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback<void>): void--><!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | Bundle name of the app that invokes the KV store. |
| storeId | string | Yes | Unique identifier of the KV store to close. The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| kvStore | [KVStore](arkts-arkdata-distributeddata-kvstore-i.md) | Yes | KV store to close. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvStore;
let kvManager;
const options = {
    createIfMissing: true,
    encrypt: false,
    backup: false,
    autoSync: false,
    kvStoreType: distributedData.KVStoreType.SINGLE_VERSION,
    schema: undefined,
    securityLevel: distributedData.SecurityLevel.S3,
}
try {
    kvManager.getKVStore('storeId', options, async function (err, store) {
        console.info('getKVStore success');
        kvStore = store;
        kvManager.closeKVStore('appId', 'storeId', kvStore, function (err, data) {
            console.info('closeKVStore success');
        });
    });
} catch (e) {
    console.error('closeKVStore e ' + e);
}
```

<a id="closekvstore2"></a>

## closeKVStore

```TypeScript
closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise<void>
```

Closes a KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [closeKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#closekvstore)

<!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise<void>--><!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | Bundle name of the app that invokes the KV store. |
| storeId | string | Yes | Unique identifier of the KV store to close. The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| kvStore | [KVStore](arkts-arkdata-distributeddata-kvstore-i.md) | Yes | KV store to close. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvManager;
let kvStore;
const options = {
    createIfMissing: true,
    encrypt: false,
    backup: false,
    autoSync: false,
    kvStoreType: distributedData.KVStoreType.SINGLE_VERSION,
    schema: undefined,
    securityLevel: distributedData.SecurityLevel.S3,
}
try {
    kvManager.getKVStore('storeId', options).then(async (store) => {
        console.info('getKVStore success');
        kvStore = store;
        kvManager.closeKVStore('appId', 'storeId', kvStore).then(() => {
            console.info('closeKVStore success');
        }).catch((err) => {
            console.error('closeKVStore err ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error('CloseKVStore getKVStore err ' + JSON.stringify(err));
    });
} catch (e) {
    console.error('closeKVStore e ' + e);
}
```

<a id="deletekvstore1"></a>

## deleteKVStore

```TypeScript
deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void
```

Deletes a KV store. This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#deletekvstore)

<!--Device-KVManager-deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void--><!--Device-KVManager-deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | Bundle name of the app that invokes the KV store. |
| storeId | string | Yes | Unique identifier of the KV store to delete. The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvManager;
let kvStore;
const options = {
    createIfMissing : true,
    encrypt : false,
    backup : false,
    autoSync : true,
    kvStoreType : distributedData.KVStoreType.SINGLE_VERSION,
    schema : undefined,
    securityLevel : distributedData.SecurityLevel.S3,
}
try {
    kvManager.getKVStore('store', options, async function (err, store) {
        console.info('getKVStore success');
        kvStore = store;
        kvManager.deleteKVStore('appId', 'storeId', function (err, data) {
            console.info('deleteKVStore success');
        });
    });
} catch (e) {
    console.error('DeleteKVStore e ' + e);
}
```

<a id="deletekvstore2"></a>

## deleteKVStore

```TypeScript
deleteKVStore(appId: string, storeId: string): Promise<void>
```

Deletes a KV store. This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [deleteKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#deletekvstore)

<!--Device-KVManager-deleteKVStore(appId: string, storeId: string): Promise<void>--><!--Device-KVManager-deleteKVStore(appId: string, storeId: string): Promise<void>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | Bundle name of the app that invokes the KV store. |
| storeId | string | Yes | Unique identifier of the KV store to delete. The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Examples**

```TypeScript
let kvManager;
let kvStore;
const options = {
    createIfMissing : true,
    encrypt : false,
    backup : false,
    autoSync : true,
    kvStoreType : distributedData.KVStoreType.SINGLE_VERSION,
    schema : undefined,
    securityLevel : distributedData.SecurityLevel.S3,
}
try {
    kvManager.getKVStore('storeId', options).then(async (store) => {
        console.info('getKVStore success');
        kvStore = store;
        kvManager.deleteKVStore('appId', 'storeId').then(() => {
            console.info('deleteKVStore success');
        }).catch((err) => {
            console.error('deleteKVStore err ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.error('getKVStore err ' + JSON.stringify(err));
    });
} catch (e) {
    console.error('deleteKVStore e ' + e);
}
```

<a id="getallkvstoreid1"></a>

## getAllKVStoreId

```TypeScript
getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void
```

Obtains the IDs of all KV stores that are created by getKVStore() and have not been deleted by [deleteKVStore()](#deletekvstore1). This API uses an asynchronous callback to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAllKVStoreId](arkts-arkdata-distributedkvstore-kvmanager-i.md#getallkvstoreid)

<!--Device-KVManager-getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void--><!--Device-KVManager-getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | Bundle name of the app that invokes the KV store. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string[]&gt; | Yes | Callback used to return the IDs of all created KV stores. |

**Examples**

```TypeScript
let kvManager;
try {
    kvManager.getAllKVStoreId('appId', function (err, data) {
        console.info('GetAllKVStoreId success');
        console.info('GetAllKVStoreId size = ' + data.length);
    });
} catch (e) {
    console.error('GetAllKVStoreId e ' + e);
}
```

<a id="getallkvstoreid2"></a>

## getAllKVStoreId

```TypeScript
getAllKVStoreId(appId: string): Promise<string[]>
```

Obtains the IDs of all KV stores that are created by getKVStore() and have not been deleted by [deleteKVStore()](#deletekvstore1). This API uses a promise to return the result.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [getAllKVStoreId](arkts-arkdata-distributedkvstore-kvmanager-i.md#getallkvstoreid)

<!--Device-KVManager-getAllKVStoreId(appId: string): Promise<string[]>--><!--Device-KVManager-getAllKVStoreId(appId: string): Promise<string[]>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | Bundle name of the app that invokes the KV store. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string[]&gt; | Promise used to return the IDs of all created KV stores. |

**Examples**

```TypeScript
let kvManager;
try {
    console.info('GetAllKVStoreId');
    kvManager.getAllKVStoreId('appId').then((data) => {
        console.info('getAllKVStoreId success');
        console.info('size = ' + data.length);
    }).catch((err) => {
        console.error('getAllKVStoreId err ' + JSON.stringify(err));
    });
} catch(e) {
    console.error('getAllKVStoreId e ' + e);
}
```

<a id="getkvstore1"></a>

## getKVStore

```TypeScript
getKVStore<T extends KVStore>(storeId: string, options: Options): Promise<T>
```

Creates and obtains a KV store. This API uses a promise to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)

<!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options): Promise<T>--><!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options): Promise<T>-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| storeId | string | Yes | Unique identifier of the KV store. The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| options | [Options](arkts-arkdata-distributeddata-options-i.md) | Yes | Configuration of the KV store. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;T&gt;, &lt;T extends KVStore&gt; | Promise used to return the KV store instance created. |

**Examples**

```TypeScript
let kvStore;
let kvManager;
try {
    const options = {
        createIfMissing : true,
        encrypt : false,
        backup : false,
        autoSync : true,
        kvStoreType : distributedData.KVStoreType.SINGLE_VERSION,
        securityLevel : distributedData.SecurityLevel.S3,
    };
    kvManager.getKVStore('storeId', options).then((store) => {
        console.info("getKVStore success");
        kvStore = store;
    }).catch((err) => {
        console.error("getKVStore err: "  + JSON.stringify(err));
    });
} catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

<a id="getkvstore2"></a>

## getKVStore

```TypeScript
getKVStore<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback<T>): void
```

Creates and obtains a KV store. This API uses an asynchronous callback to return the result.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)

<!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback<T>): void--><!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback<T>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| storeId | string | Yes | Unique identifier of the KV store. The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md). |
| options | [Options](arkts-arkdata-distributeddata-options-i.md) | Yes | Configuration of the KV store. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | Yes | Callback used to return the KV store instance created. |

**Examples**

```TypeScript
let kvStore;
let kvManager;
try {
    const options = {
        createIfMissing : true,
        encrypt : false,
        backup : false,
        autoSync : true,
        kvStoreType : distributedData.KVStoreType.SINGLE_VERSION,
        securityLevel : distributedData.SecurityLevel.S3,
    };
    kvManager.getKVStore('storeId', options, function (err, store) {
        if (err) {
            console.error("getKVStore err: "  + JSON.stringify(err));
            return;
        }
        console.info("getKVStore success");
        kvStore = store;
    });
} catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

## off

```TypeScript
off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void
```

Unsubscribes from service status changes.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [off](arkts-arkdata-distributedkvstore-kvmanager-i.md#off)

<!--Device-KVManager-off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void--><!--Device-KVManager-off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'distributedDataServiceDie' | Yes | Event type. The value is **distributedDataServiceDie**, which indicates service status changes. |
| deathCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks for service status changes will be unregistered. |

**Examples**

```TypeScript
let kvManager;
try {
    console.info('KVManagerOff');
    const deathCallback = function () {
        console.info('death callback call');
    }
    kvManager.off('distributedDataServiceDie', deathCallback);
} catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```

## on

```TypeScript
on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void
```

Subscribes to service status changes.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [on](arkts-arkdata-distributedkvstore-kvmanager-i.md#on)

<!--Device-KVManager-on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void--><!--Device-KVManager-on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void-End-->

**System capability:** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| event | 'distributedDataServiceDie' | Yes | Event type. The value is **distributedDataServiceDie**, which indicates service status changes. |
| deathCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Examples**

```TypeScript
let kvManager;
try {
    console.info('KVManagerOn');
    const deathCallback = function () {
        console.info('death callback call');
    }
    kvManager.on('distributedDataServiceDie', deathCallback);
} catch (e) {
    console.error("An unexpected error occurred. Error:" + e);
}
```
