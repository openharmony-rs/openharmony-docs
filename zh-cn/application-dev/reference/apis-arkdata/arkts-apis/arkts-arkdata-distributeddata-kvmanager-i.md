# KVManager

数据管理实例，用于获取KVStore的相关信息。在调用KVManager的方法前，需要先通过[createKVManager](arkts-arkdata-distributeddata-createkvmanager-f.md#createkvmanager)构建一个KVManager实例。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** KVManager

<!--Device-distributedData-interface KVManager--><!--Device-distributedData-interface KVManager-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## closeKVStore

```TypeScript
closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback<void>): void
```

通过storeId的值关闭指定的KVStore数据库，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeKVStore

<!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback<void>): void--><!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 所调用数据库方的包名。 |
| storeId | string | 是 | Unique identifier of the 要关闭的KVStore数据库。 The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants). |
| kvStore | [KVStore](arkts-arkdata-distributeddata-kvstore-i.md) | 是 | 要关闭的KVStore数据库。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例：**

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
        console.log('getKVStore success');
        kvStore = store;
        kvManager.closeKVStore('appId', 'storeId', kvStore, function (err, data) {
            console.log('closeKVStore success');
        });
    });
} catch (e) {
    console.log('closeKVStore e ' + e);
}

```

## closeKVStore

```TypeScript
closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise<void>
```

通过storeId的值关闭指定的KVStore数据库，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeKVStore

<!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise<void>--><!--Device-KVManager-closeKVStore(appId: string, storeId: string, kvStore: KVStore): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 所调用数据库方的包名。 |
| storeId | string | 是 | Unique identifier of the 要关闭的KVStore数据库。 The length cannot exceed [MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants). |
| kvStore | [KVStore](arkts-arkdata-distributeddata-kvstore-i.md) | 是 | 要关闭的KVStore数据库。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

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
        console.log('getKVStore success');
        kvStore = store;
        kvManager.closeKVStore('appId', 'storeId', kvStore).then(() => {
            console.log('closeKVStore success');
        }).catch((err) => {
            console.log('closeKVStore err ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log('CloseKVStore getKVStore err ' + JSON.stringify(err));
    });
} catch (e) {
    console.log('closeKVStore e ' + e);
}

```

## deleteKVStore

```TypeScript
deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void
```

通过storeId的值删除指定的KVStore数据库，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteKVStore

<!--Device-KVManager-deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void--><!--Device-KVManager-deleteKVStore(appId: string, storeId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 所调用数据库方的包名。 |
| storeId | string | 是 | 要删除的数据库唯一标识符，长度不大于[MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例：**

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
        console.log('getKVStore success');
        kvStore = store;
        kvManager.deleteKVStore('appId', 'storeId', function (err, data) {
            console.log('deleteKVStore success');
        });
    });
} catch (e) {
    console.log('DeleteKVStore e ' + e);
}

```

## deleteKVStore

```TypeScript
deleteKVStore(appId: string, storeId: string): Promise<void>
```

通过storeId的值删除指定的KVStore数据库，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteKVStore

<!--Device-KVManager-deleteKVStore(appId: string, storeId: string): Promise<void>--><!--Device-KVManager-deleteKVStore(appId: string, storeId: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 所调用数据库方的包名。 |
| storeId | string | 是 | 要删除的数据库唯一标识符，长度不大于[MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

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
        console.log('getKVStore success');
        kvStore = store;
        kvManager.deleteKVStore('appId', 'storeId').then(() => {
            console.log('deleteKVStore success');
        }).catch((err) => {
            console.log('deleteKVStore err ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log('getKVStore err ' + JSON.stringify(err));
    });
} catch (e) {
    console.log('deleteKVStore e ' + e);
}

```

## getAllKVStoreId

```TypeScript
getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void
```

获取所有通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)方法创建的且没有调用[deleteKVStore](arkts-arkdata-distributeddata-kvmanager-i.md#deletekvstore)方法删除的KVStore数据库的storeId，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAllKVStoreId

<!--Device-KVManager-getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void--><!--Device-KVManager-getAllKVStoreId(appId: string, callback: AsyncCallback<string[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 所调用数据库方的包名。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string[]&gt; | 是 | 回调函数。返回所有创建的KvStore数据库的storeId。 |

**示例：**

```TypeScript
let kvManager;
try {
    kvManager.getAllKVStoreId('appId', function (err, data) {
        console.log('GetAllKVStoreId success');
        console.log('GetAllKVStoreId size = ' + data.length);
    });
} catch (e) {
    console.log('GetAllKVStoreId e ' + e);
}

```

## getAllKVStoreId

```TypeScript
getAllKVStoreId(appId: string): Promise<string[]>
```

获取所有通过[getKVStore](arkts-arkdata-distributedkvstore-kvmanager-i.md#getkvstore)方法创建的且没有调用[deleteKVStore](arkts-arkdata-distributeddata-kvmanager-i.md#deletekvstore)方法删除的KVStore数据库的storeId，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getAllKVStoreId

<!--Device-KVManager-getAllKVStoreId(appId: string): Promise<string[]>--><!--Device-KVManager-getAllKVStoreId(appId: string): Promise<string[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| appId | string | 是 | 所调用数据库方的包名。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;string[]&gt; | Promise对象。返回所有创建的KvStore数据库的storeId。 |

**示例：**

```TypeScript
let kvManager;
try {
    console.log('GetAllKVStoreId');
    kvManager.getAllKVStoreId('appId').then((data) => {
        console.log('getAllKVStoreId success');
        console.log('size = ' + data.length);
    }).catch((err) => {
        console.log('getAllKVStoreId err ' + JSON.stringify(err));
    });
} catch(e) {
    console.log('getAllKVStoreId e ' + e);
}

```

## getKVStore

```TypeScript
getKVStore<T extends KVStore>(storeId: string, options: Options): Promise<T>
```

通过指定Options和storeId，创建并获取KVStore数据库，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getKVStore

<!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options): Promise<T>--><!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options): Promise<T>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| storeId | string | 是 | 数据库唯一标识符，长度不大于[MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants)。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 创建KVStore实例的配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;T&gt; | Promise对象。返回创建的KVStore数据库实例。 |

**示例：**

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
        console.log("getKVStore success");
        kvStore = store;
    }).catch((err) => {
        console.log("getKVStore err: "  + JSON.stringify(err));
    });
} catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

## getKVStore

```TypeScript
getKVStore<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback<T>): void
```

通过指定Options和storeId，创建并获取KVStore数据库，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getKVStore

<!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback<T>): void--><!--Device-KVManager-getKVStore<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback<T>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| storeId | string | 是 | 数据库唯一标识符，长度不大于[MAX_STORE_ID_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants)。 |
| options | [Options](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-zlib-options-i.md) | 是 | 创建KVStore实例的配置信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;T&gt; | 是 | 回调函数。返回创建的KVStore数据库实例。 |

**示例：**

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
            console.log("getKVStore err: "  + JSON.stringify(err));
            return;
        }
        console.log("getKVStore success");
        kvStore = store;
    });
} catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

## off

```TypeScript
off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void
```

取消订阅服务状态变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

<!--Device-KVManager-off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void--><!--Device-KVManager-off(event: 'distributedDataServiceDie', deathCallback?: Callback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'distributedDataServiceDie' | 是 | 取消订阅的事件名，固定为'distributedDataServiceDie'，即服务状态变更事件。 |
| deathCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有已订阅的函数。 |

**示例：**

```TypeScript
let kvManager;
try {
    console.log('KVManagerOff');
    const deathCallback = function () {
        console.log('death callback call');
    }
    kvManager.off('distributedDataServiceDie', deathCallback);
} catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}
    

```

## on

```TypeScript
on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void
```

订阅服务状态变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

<!--Device-KVManager-on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void--><!--Device-KVManager-on(event: 'distributedDataServiceDie', deathCallback: Callback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'distributedDataServiceDie' | 是 | 订阅的事件名，固定为'distributedDataServiceDie'，即服务状态变更事件。 |
| deathCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvManager;
try {
    console.log('KVManagerOn');
    const deathCallback = function () {
        console.log('death callback call');
    }
    kvManager.on('distributedDataServiceDie', deathCallback);
} catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

