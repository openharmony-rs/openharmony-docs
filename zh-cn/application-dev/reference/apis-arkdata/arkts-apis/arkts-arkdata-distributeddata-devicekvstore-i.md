# DeviceKVStore

设备协同数据库，继承自KVStore，提供查询数据和同步数据的方法。设备协同数据库，以设备维度对数据进行区分，每台设备仅能写入和修改本设备的数据，其它设备的数据对其是只读的，无法修改其它设备的数据。比如，可以使用设备协同数据库实现设备间的图片分享，可以查看其他设备的图片，但无法修改和删除其他设备的图片。在调用DeviceKVStore的方法前，需要先通过[getKVStore](arkts-arkdata-distributeddata-kvmanager-i.md#getkvstore-2)构建一个DeviceKVStore实例。

**继承/实现关系：** DeviceKVStore extends [KVStore](arkts-arkdata-distributeddata-kvstore-i.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** DeviceKVStore

<!--Device-distributedData-interface DeviceKVStore extends KVStore--><!--Device-distributedData-interface DeviceKVStore extends KVStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void
```

关闭由[DeviceKVStore.getResultSet](../../../../reference/apis-arkdata/js-apis-distributed-data.md#getresultset8-4)返回的KvStoreResultSet对象，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeResultSet

<!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void--><!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | 是 | 指示要关闭的KvStoreResultSet对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
try {
    console.log('CloseResultSet success');
    let resultSet = null;
    kvStore.closeResultSet(resultSet, function (err, data) {
        if (err == undefined) {
            console.log('closeResultSet success');
        } else {
            console.log('closeResultSet fail');
        }
    });
}catch(e) {
    console.log('CloseResultSet e ' + e);
}

```

## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet): Promise<void>
```

关闭由[DeviceKVStore.getResultSet](../../../../reference/apis-arkdata/js-apis-distributed-data.md#getresultset8-4)返回的KvStoreResultSet对象，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeResultSet

<!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet): Promise<void>--><!--Device-DeviceKVStore-closeResultSet(resultSet: KvStoreResultSet): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | 是 | 指示要关闭的KvStoreResultSet对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    console.log('CloseResultSet success');
    let resultSet = null;
    kvStore.closeResultSet(resultSet).then(() => {
        console.log('closeResultSet success');
    }).catch((err) => {
        console.log('closeResultSet fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('CloseResultSet e ' + e);
}

```

## get

```TypeScript
get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void
```

获取与指定设备ID和key匹配的string值，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** get

<!--Device-DeviceKVStore-get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void--><!--Device-DeviceKVStore-get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| key | string | 是 | 表示要查询key值的键。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<boolean \| string \| number \| Uint8Array> | 是 | 回调函数，返回匹配给定条件的字符串值。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try{
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async function (err,data) {
        console.log('put success');
        kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT, function (err,data) {
            console.log('get success');
        });
    })
}catch(e) {
    console.log('get e' + e);
}

```

## get

```TypeScript
get(deviceId: string, key: string): Promise<boolean | string | number | Uint8Array>
```

获取与指定设备ID和key匹配的string值，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** get

<!--Device-DeviceKVStore-get(deviceId: string, key: string): Promise<boolean | string | number | Uint8Array>--><!--Device-DeviceKVStore-get(deviceId: string, key: string): Promise<boolean | string | number | Uint8Array>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| key | string | 是 | 表示要查询key值的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<boolean \| string \| number \| Uint8Array> | Promise对象。返回匹配给定条件的字符串值。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then(async (data) => {
        console.log(' put success');
        kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT).then((data) => {
            console.log('get success');
        }).catch((err) => {
            console.log('get fail ' + JSON.stringify(err));
        });
    }).catch((error) => {
        console.log('put error' + error);
    });
} catch (e) {
    console.log('Get e ' + e);
}

```

## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

获取与指定设备ID和key前缀匹配的所有键值对，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Entry[]> | 是 | 回调函数，返回满足给定条件的所有键值对的列表。 |

**示例：**

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
    console.log('entries: ' + entries);
    kvStore.putBatch(entries, async function (err,data) {
        console.log('putBatch success');
        kvStore.getEntries('localDeviceId', 'batch_test_string_key', function (err,entries) {
            console.log('getEntries success');
            console.log('entries.length: ' + entries.length);
            console.log('entries[0]: ' + JSON.stringify(entries[0]));
        });
    });
}catch(e) {
    console.log('PutBatch e ' + e);
}

```

## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>
```

获取与指定设备ID和key前缀匹配的所有键值对，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Entry[]> | Promise对象。返回匹配给定条件的所有键值对的列表。 |

**示例：**

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
    console.log('entries: ' + entries);
    kvStore.putBatch(entries).then(async (err) => {
        console.log('putBatch success');
        kvStore.getEntries('localDeviceId', 'batch_test_string_key').then((entries) => {
            console.log('getEntries success');
            console.log('entries.length: ' + entries.length);
            console.log('entries[0]: ' + JSON.stringify(entries[0]));
            console.log('entries[0].value: ' + JSON.stringify(entries[0].value));
            console.log('entries[0].value.value: ' + entries[0].value.value);
        }).catch((err) => {
            console.log('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log('putBatch fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('PutBatch e ' + e);
}

```

## getEntries

```TypeScript
getEntries(query: Query, callback: AsyncCallback<Entry[]>): void
```

获取与指定Query对象匹配的键值对列表，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-DeviceKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Entry[]> | 是 | 回调函数，返回与指定Query对象匹配的键值对列表。 |

**示例：**

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.log('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        query.deviceId('localDeviceId');
        kvStore.getEntries(query, function (err,entries) {
            console.log('getEntries success');
            console.log('entries.length: ' + entries.length);
            console.log('entries[0]: ' + JSON.stringify(entries[0]));
        });
    });
    console.log('GetEntries success');
}catch(e) {
    console.log('GetEntries e ' + e);
}

```

## getEntries

```TypeScript
getEntries(query: Query): Promise<Entry[]>
```

获取与指定Query对象匹配的键值对列表，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-DeviceKVStore-getEntries(query: Query): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(query: Query): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Entry[]> | Promise对象。返回与指定Query对象匹配的键值对列表。 |

**示例：**

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.log('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        kvStore.getEntries(query).then((entries) => {
            console.log('getEntries success');
        }).catch((err) => {
            console.log('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log('GetEntries putBatch fail ' + JSON.stringify(err))
    });
    console.log('GetEntries success');
}catch(e) {
    console.log('GetEntries e ' + e);
}

```

## getEntries

```TypeScript
getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void
```

获取与指定设备ID和Query对象匹配的键值对列表，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 键值对所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<Entry[]> | 是 | 回调函数。返回与指定设备ID和Query对象匹配的键值对列表。 |

**示例：**

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.log('putBatch success');
        var query = new distributedData.Query();
        query.deviceId('localDeviceId');
        query.prefixKey("batch_test");
        kvStore.getEntries('localDeviceId', query, function (err,entries) {
            console.log('getEntries success');
            console.log('entries.length: ' + entries.length);
            console.log('entries[0]: ' + JSON.stringify(entries[0]));
        })
    });
    console.log('GetEntries success');
}catch(e) {
    console.log('GetEntries e ' + e);
}

```

## getEntries

```TypeScript
getEntries(deviceId: string, query: Query): Promise<Entry[]>
```

获取与指定设备ID和Query对象匹配的键值对列表，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query): Promise<Entry[]>--><!--Device-DeviceKVStore-getEntries(deviceId: string, query: Query): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 键值对所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<Entry[]> | Promise对象。返回与指定设备ID和Query对象匹配的键值对列表。 |

**示例：**

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.log('putBatch success');
        var query = new distributedData.Query();
        query.deviceId('localDeviceId');
        query.prefixKey("batch_test");
        kvStore.getEntries('localDeviceId', query).then((entries) => {
            console.log('getEntries success');
        }).catch((err) => {
            console.log('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log('putBatch fail ' + JSON.stringify(err));
    });
    console.log('GetEntries success');
}catch(e) {
    console.log('GetEntries e ' + e);
}

```

## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void
```

获取与指定设备ID和key前缀匹配的KvStoreResultSet对象，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<KvStoreResultSet> | 是 | 回调函数。返回与指定设备ID和key前缀匹配的KvStoreResultSet对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('localDeviceId', 'batch_test_string_key', async function (err, result) {
        console.log('getResultSet succeed.');
        resultSet = result;
        kvStore.closeResultSet(resultSet, function (err, data) {
            console.log('closeResultSet success');
        })
    });
}catch(e) {
    console.log('GetResultSet e ' + e);
}

```

## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string): Promise<KvStoreResultSet>
```

获取与指定设备ID和key前缀匹配的KvStoreResultSet对象，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string): Promise<KvStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(deviceId: string, keyPrefix: string): Promise<KvStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<KvStoreResultSet> | Promise对象。返回与指定设备ID和key前缀匹配的KvStoreResultSet对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    let resultSet;
    kvStore.getResultSet('localDeviceId', 'batch_test_string_key').then((result) => {
        console.log('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.log('getResultSet failed: ' + JSON.stringify(err));
    });
    kvStore.closeResultSet(resultSet).then((err) => {
        console.log('closeResultSet success');
    }).catch((err) => {
        console.log('closeResultSet fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetResultSet e ' + e);
}

```

## getResultSet

```TypeScript
getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void
```

获取与指定Query对象匹配的KvStoreResultSet对象，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-DeviceKVStore-getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<KvStoreResultSet> | 是 | 回调函数，返回与指定Query对象匹配的KvStoreResultSet对象。 |

**示例：**

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
        console.log('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        query.deviceId('localDeviceId');
        kvStore.getResultSet(query, async function (err, result) {
            console.log('getResultSet succeed.');
            resultSet = result;
            kvStore.closeResultSet(resultSet, function (err, data) {
                console.log('closeResultSet success');
            })
        });
    });
} catch(e) {
    console.log('GetResultSet e ' + e);
}

```

## getResultSet

```TypeScript
getResultSet(query: Query): Promise<KvStoreResultSet>
```

获取与指定Query对象匹配的KvStoreResultSet对象，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-DeviceKVStore-getResultSet(query: Query): Promise<KvStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(query: Query): Promise<KvStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<KvStoreResultSet> | Promise对象。返回与指定Query对象匹配的KvStoreResultSet对象。 |

**示例：**

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
        console.log('putBatch success');
    }).catch((err) => {
        console.log('putBatch fail ' + err);
    });
    const query = new distributedData.Query();
    query.deviceId('localDeviceId');
    query.prefixKey("batch_test");
    console.log("GetResultSet " + query.getSqlLike());
    kvStore.getResultSet(query).then((result) => {
        console.log('getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.log('getResultSet failed: ' + JSON.stringify(err));
    });
    kvStore.closeResultSet(resultSet).then((err) => {
        console.log('closeResultSet success');
    }).catch((err) => {
        console.log('closeResultSet fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetResultSet e ' + e);
}

```

## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KvStoreResultSet>): void
```

获取与指定设备ID和Query对象匹配的KvStoreResultSet对象，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<KvStoreResultSet> | 是 | 回调函数。返回与指定设备ID和Query对象匹配的KvStoreResultSet对象。 |

**示例：**

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
        console.log('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        kvStore.getResultSet('localDeviceId', query, async function (err, result) {
            console.log('getResultSet succeed.');
            resultSet = result;
            kvStore.closeResultSet(resultSet, function (err, data) {
                console.log('closeResultSet success');
            })
        });
    });
} catch(e) {
    console.log('GetResultSet e ' + e);
}

```

## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query): Promise<KvStoreResultSet>
```

获取与指定设备ID和Query对象匹配的KvStoreResultSet对象，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query): Promise<KvStoreResultSet>--><!--Device-DeviceKVStore-getResultSet(deviceId: string, query: Query): Promise<KvStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<KvStoreResultSet> | Promise对象。返回与指定设备ID和Query对象匹配的KvStoreResultSet对象。 |

**示例：**

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
        console.log('GetResultSet putBatch success');
    }).catch((err) => {
        console.log('PutBatch putBatch fail ' + JSON.stringify(err));
    });
    const query = new distributedData.Query();
    query.prefixKey("batch_test");
    kvStore.getResultSet('localDeviceId', query).then((result) => {
        console.log('GetResultSet getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.log('GetResultSet getResultSet failed: ' + JSON.stringify(err));
    });
    query.deviceId('localDeviceId');
    console.log("GetResultSet " + query.getSqlLike());
    kvStore.closeResultSet(resultSet).then((err) => {
        console.log('GetResultSet closeResultSet success');
    }).catch((err) => {
        console.log('GetResultSet closeResultSet fail ' + JSON.stringify(err));
    });

}catch(e) {
    console.log('GetResultSet e ' + e);
}

```

## getResultSize

```TypeScript
getResultSize(query: Query, callback: AsyncCallback<number>): void
```

获取与指定Query对象匹配的结果数，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

<!--Device-DeviceKVStore-getResultSize(query: Query, callback: AsyncCallback<number>): void--><!--Device-DeviceKVStore-getResultSize(query: Query, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数，返回与指定Query对象匹配的结果数。 |

**示例：**

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
        console.log('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        query.deviceId('localDeviceId');
        kvStore.getResultSize(query, async function (err, resultSize) {
            console.log('getResultSet succeed.');
        });
    });
} catch(e) {
    console.log('GetResultSize e ' + e);
}

```

## getResultSize

```TypeScript
getResultSize(query: Query): Promise<number>
```

获取与指定Query对象匹配的结果数，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

<!--Device-DeviceKVStore-getResultSize(query: Query): Promise<number>--><!--Device-DeviceKVStore-getResultSize(query: Query): Promise<number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回与指定Query对象匹配的结果数。 |

**示例：**

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
        console.log('putBatch success');
    }).catch((err) => {
        console.log('putBatch fail ' + JSON.stringify(err));
    });
    const query = new distributedData.Query();
    query.prefixKey("batch_test");
    query.deviceId('localDeviceId');
    kvStore.getResultSize(query).then((resultSize) => {
        console.log('getResultSet succeed.');
    }).catch((err) => {
        console.log('getResultSet failed: ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetResultSize e ' + e);
}

```

## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void
```

获取与指定设备ID和Query对象匹配的结果数，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

<!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void--><!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<number> | 是 | 回调函数。返回与指定设备ID和Query对象匹配的结果数。 |

**示例：**

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
        console.log('putBatch success');
        const query = new distributedData.Query();
        query.prefixKey("batch_test");
        kvStore.getResultSize('localDeviceId', query, async function (err, resultSize) {
            console.log('getResultSet succeed.');
        });
    });
} catch(e) {
    console.log('GetResultSize e ' + e);
}

```

## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query): Promise<number>
```

获取与指定设备ID和Query对象匹配的结果数，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

<!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query): Promise<number>--><!--Device-DeviceKVStore-getResultSize(deviceId: string, query: Query): Promise<number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<number> | Promise对象。返回与指定设备ID和Query对象匹配的结果数。 |

**示例：**

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
        console.log('putBatch success');
    }).catch((err) => {
        console.log('putBatch fail ' + JSON.stringify(err));
    });
    var query = new distributedData.Query();
    query.prefixKey("batch_test");
    kvStore.getResultSize('localDeviceId', query).then((resultSize) => {
        console.log('getResultSet succeed.');
    }).catch((err) => {
        console.log('getResultSet failed: ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetResultSize e ' + e);
}

```

## off

```TypeScript
off(event: 'dataChange', listener?: Callback<ChangeNotification>): void
```

取消订阅数据变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

<!--Device-DeviceKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void--><!--Device-DeviceKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取消订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| listener | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ChangeNotification> | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

**示例：**

```TypeScript
let kvStore;
class KvstoreModel {
    call(data) {
        console.log("dataChange: " + data);
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

## off

```TypeScript
off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void
```

取消订阅同步完成事件回调通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

<!--Device-DeviceKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void--><!--Device-DeviceKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 取消订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Array<[string, number]>> | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

**示例：**

```TypeScript
let kvStore;
class KvstoreModel {
    call(data) {
        console.log("syncComplete: " + data);
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

订阅指定类型的数据变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

<!--Device-DeviceKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void--><!--Device-DeviceKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| type | [SubscribeType](../../apis-notification-kit/arkts-apis/arkts-notification-notificationextensionsubscription-subscribetype-e.md) | 是 | 表示订阅的类型。 |
| listener | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<ChangeNotification> | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
kvStore.on('dataChange', distributedData.SubscribeType.SUBSCRIBE_TYPE_LOCAL, function (data) {
    console.log("dataChange callback call data: " + JSON.stringify(data));
});

```

## on

```TypeScript
on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void
```

订阅同步完成事件回调通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

<!--Device-DeviceKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void--><!--Device-DeviceKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-common-callback-i.md)<Array<[string, number]>> | 是 | 回调函数。用于向调用方发送同步结果的回调。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_FLOAT_ELEMENT = 'key_test_float';
const VALUE_TEST_FLOAT_ELEMENT = 321.12;
try {
    kvStore.on('syncComplete', function (data) {
        console.log('syncComplete ' + data)
    });
    kvStore.put(KEY_TEST_FLOAT_ELEMENT, VALUE_TEST_FLOAT_ELEMENT).then((data) => {
        console.log('syncComplete put success');
    }).catch((error) => {
        console.log('syncComplete put fail ' + error);
    });
}catch(e) {
    console.log('syncComplete put e ' + e);
}

```

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void
```

从当前数据库中删除指定设备的数据，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeDeviceData

<!--Device-DeviceKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void--><!--Device-DeviceKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要删除其数据的设备。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)<void> | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-string-001';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async function (err,data) {
        console.log('RemoveDeviceData  put success');
        const deviceid = 'no_exist_device_id';
        kvStore.removeDeviceData(deviceid, async function (err,data) {
            if (err == undefined) {
                console.log('removeDeviceData success');
            } else {
                console.log('removeDeviceData fail');
                kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT, async function (err,data) {
                    console.log('RemoveDeviceData get success');
                });
            }
        });
    });
}catch(e) {
    console.log('RemoveDeviceData e ' + e);
}

```

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string): Promise<void>
```

从当前数据库中删除指定设备的数据，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeDeviceData

<!--Device-DeviceKVStore-removeDeviceData(deviceId: string): Promise<void>--><!--Device-DeviceKVStore-removeDeviceData(deviceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要删除其数据的设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise<void> | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-string-001';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((err) => {
        console.log('RemoveDeviceData put success');
    }).catch((err) => {
        console.log('RemoveDeviceData put fail ' + JSON.stringify(err));
    });
    const deviceid = 'no_exist_device_id';
    kvStore.removeDeviceData(deviceid).then((err) => {
        console.log('removeDeviceData success');
    }).catch((err) => {
        console.log('removeDeviceData fail ' + JSON.stringify(err));
    });
    kvStore.get('localDeviceId', KEY_TEST_STRING_ELEMENT).then((data) => {
        console.log('RemoveDeviceData get success data:' + data);
    }).catch((err) => {
        console.log('RemoveDeviceData get fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('RemoveDeviceData e ' + e);
}

```

## sync

```TypeScript
sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void
```

在手动同步方式下，触发数据库同步。

> **说明：**  
>  
> 其中deviceIds为<!--RP2-->[DeviceInfo](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-deviceinfo-i-sys.md)中的  
> networkId, 通过调用  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP2End-->deviceManager模块的接口均为系统接口，仅系统应用可用。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** sync

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-DeviceKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void--><!--Device-DeviceKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceIds | string[] | 是 | 需要同步DeviceKVStore数据库的设备networkId列表。 |
| mode | [SyncMode](arkts-arkdata-distributeddata-syncmode-e.md) | 是 | 同步模式。 |
| delayMs | number | 否 | 可选参数，允许延时时间，单位：ms（毫秒），默认为0。 |

**示例：**

```TypeScript
import deviceManager from '@ohos.distributedHardware.deviceManager';

let devManager;
let kvStore;
const KEY_TEST_SYNC_ELEMENT = 'key_test_sync';
const VALUE_TEST_SYNC_ELEMENT = 'value-string-001';
// create deviceManager
deviceManager.createDeviceManager('bundleName', (err, value) => {
  if (!err) {
    devManager = value;
    let deviceIds = [];
    if (devManager != null) {
      var devices = devManager.getTrustedDeviceListSync();
      for (var i = 0; i < devices.length; i++) {
        deviceIds[i] = devices[i].networkId;
      }
    }
    try {
      kvStore.on('syncComplete', function (data) {
        console.log('Sync dataChange');
      });
      kvStore.put(KEY_TEST_SYNC_ELEMENT + 'testSync101', VALUE_TEST_SYNC_ELEMENT, function (err, data) {
        if (err != undefined) {
          console.log("put err: " + JSON.stringify(err));
          return;
        }
        console.log('Succeeded in putting data');
        const mode = distributedData.SyncMode.PULL_ONLY;
        kvStore.sync(deviceIds, mode, 1000);
      });
    } catch (e) {
      console.log('Sync e' + e);
    }
  }
});

```

