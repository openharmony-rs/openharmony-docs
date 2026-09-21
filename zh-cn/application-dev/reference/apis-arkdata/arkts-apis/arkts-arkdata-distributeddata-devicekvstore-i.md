# DeviceKVStore

```TypeScript
interface DeviceKVStore extends KVStore
```

设备协同数据库，继承自KVStore，提供查询数据和同步数据的方法。设备协同数据库，以设备维度对数据进行区分，每台设备仅能写入和修改本设备的数据，其它设备的数据对其是只读的，无法修改其它设备的数据。比如，可以使用设备协同数据库实现设备间的图片分享，可以查看其他设备的图片，但无法修改和删除其他设备的图片。在调用DeviceKVStore的方法前，需要先通过getKVStore构建一个DeviceKVStore实例。

**继承/实现关系：** DeviceKVStore extends [KVStore](arkts-arkdata-distributeddata-kvstore-i.md)

**起始版本：** 8

**废弃版本：** 9

**替代接口：** DeviceKVStore

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

## 导入模块

```TypeScript
```

## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void
```

关闭由[DeviceKVStore.getResultSet](../../../reference/apis-arkdata/js-apis-distributed-data.md#getresultset8-4)返回的KvStoreResultSet对象，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | 是 | 指示要关闭的KvStoreResultSet对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

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

<a id="closeresultset-1"></a>

## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet): Promise<void>
```

关闭由[DeviceKVStore.getResultSet](../../../reference/apis-arkdata/js-apis-distributed-data.md#getresultset8-4)返回的KvStoreResultSet对象，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | 是 | 指示要关闭的KvStoreResultSet对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

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

## get

```TypeScript
get(deviceId: string, key: string, callback: AsyncCallback<boolean | string | number | Uint8Array>): void
```

获取与指定设备ID和key匹配的string值，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** get

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| key | string | 是 | 表示要查询key值的键。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean &#124; string &#124; number &#124; Uint8Array&gt; | 是 | 回调函数，返回匹配给定条件的字符串值。 |

**示例**

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

<a id="get-1"></a>

## get

```TypeScript
get(deviceId: string, key: string): Promise<boolean | string | number | Uint8Array>
```

获取与指定设备ID和key匹配的string值，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** get

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| key | string | 是 | 表示要查询key值的键。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean &#124; string &#124; number &#124; Uint8Array&gt; | Promise对象。返回匹配给定条件的字符串值。 |

**示例**

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

## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

获取与指定设备ID和key前缀匹配的所有键值对，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | 是 | 回调函数，返回满足给定条件的所有键值对的列表。 |

**示例**

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

<a id="getentries-1"></a>

## getEntries

```TypeScript
getEntries(deviceId: string, keyPrefix: string): Promise<Entry[]>
```

获取与指定设备ID和key前缀匹配的所有键值对，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Promise对象。返回匹配给定条件的所有键值对的列表。 |

**示例**

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

<a id="getentries-2"></a>

## getEntries

```TypeScript
getEntries(query: Query, callback: AsyncCallback<Entry[]>): void
```

获取与指定Query对象匹配的键值对列表，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | 是 | 回调函数，返回与指定Query对象匹配的键值对列表。 |

**示例**

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

<a id="getentries-3"></a>

## getEntries

```TypeScript
getEntries(query: Query): Promise<Entry[]>
```

获取与指定Query对象匹配的键值对列表，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Promise对象。返回与指定Query对象匹配的键值对列表。 |

**示例**

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

<a id="getentries-4"></a>

## getEntries

```TypeScript
getEntries(deviceId: string, query: Query, callback: AsyncCallback<Entry[]>): void
```

获取与指定设备ID和Query对象匹配的键值对列表，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 键值对所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | 是 | 回调函数。返回与指定设备ID和Query对象匹配的键值对列表。 |

**示例**

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

<a id="getentries-5"></a>

## getEntries

```TypeScript
getEntries(deviceId: string, query: Query): Promise<Entry[]>
```

获取与指定设备ID和Query对象匹配的键值对列表，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 键值对所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[Entry](arkts-arkdata-distributeddata-entry-i.md)[]&gt; | Promise对象。返回与指定设备ID和Query对象匹配的键值对列表。 |

**示例**

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

## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void
```

获取与指定设备ID和key前缀匹配的KvStoreResultSet对象，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | 是 | 回调函数。返回与指定设备ID和key前缀匹配的KvStoreResultSet对象。 |

**示例**

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

<a id="getresultset-1"></a>

## getResultSet

```TypeScript
getResultSet(deviceId: string, keyPrefix: string): Promise<KvStoreResultSet>
```

获取与指定设备ID和key前缀匹配的KvStoreResultSet对象，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要查询其数据的设备。 |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Promise对象。返回与指定设备ID和key前缀匹配的KvStoreResultSet对象。 |

**示例**

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

<a id="getresultset-2"></a>

## getResultSet

```TypeScript
getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void
```

获取与指定Query对象匹配的KvStoreResultSet对象，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | 是 | 回调函数，返回与指定Query对象匹配的KvStoreResultSet对象。 |

**示例**

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

<a id="getresultset-3"></a>

## getResultSet

```TypeScript
getResultSet(query: Query): Promise<KvStoreResultSet>
```

获取与指定Query对象匹配的KvStoreResultSet对象，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Promise对象。返回与指定Query对象匹配的KvStoreResultSet对象。 |

**示例**

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

<a id="getresultset-4"></a>

## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query, callback: AsyncCallback<KvStoreResultSet>): void
```

获取与指定设备ID和Query对象匹配的KvStoreResultSet对象，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | 是 | 回调函数。返回与指定设备ID和Query对象匹配的KvStoreResultSet对象。 |

**示例**

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

<a id="getresultset-5"></a>

## getResultSet

```TypeScript
getResultSet(deviceId: string, query: Query): Promise<KvStoreResultSet>
```

获取与指定设备ID和Query对象匹配的KvStoreResultSet对象，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md)&gt; | Promise对象。返回与指定设备ID和Query对象匹配的KvStoreResultSet对象。 |

**示例**

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

## getResultSize

```TypeScript
getResultSize(query: Query, callback: AsyncCallback<number>): void
```

获取与指定Query对象匹配的结果数，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数，返回与指定Query对象匹配的结果数。 |

**示例**

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

<a id="getresultsize-1"></a>

## getResultSize

```TypeScript
getResultSize(query: Query): Promise<number>
```

获取与指定Query对象匹配的结果数，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回与指定Query对象匹配的结果数。 |

**示例**

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

<a id="getresultsize-2"></a>

## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query, callback: AsyncCallback<number>): void
```

获取与指定设备ID和Query对象匹配的结果数，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。返回与指定设备ID和Query对象匹配的结果数。 |

**示例**

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

<a id="getresultsize-3"></a>

## getResultSize

```TypeScript
getResultSize(deviceId: string, query: Query): Promise<number>
```

获取与指定设备ID和Query对象匹配的结果数，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | KvStoreResultSet对象所属的设备ID。 |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回与指定设备ID和Query对象匹配的结果数。 |

**示例**

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

## off

```TypeScript
off(event: 'dataChange', listener?: Callback<ChangeNotification>): void
```

取消订阅数据变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取消订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeNotification](arkts-arkdata-distributeddata-changenotification-i.md)&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

**示例**

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

取消订阅同步完成事件回调通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 取消订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

**示例**

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

订阅指定类型的数据变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| type | [SubscribeType](arkts-arkdata-distributeddata-subscribetype-e.md) | 是 | 表示订阅的类型。 |
| listener | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[ChangeNotification](arkts-arkdata-distributeddata-changenotification-i.md)&gt; | 是 | 回调函数。 |

**示例**

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

订阅同步完成事件回调通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | 是 | 回调函数。用于向调用方发送同步结果的回调。 |

**示例**

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

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void
```

从当前数据库中删除指定设备的数据，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeDeviceData

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要删除其数据的设备。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例**

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

<a id="removedevicedata-1"></a>

## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string): Promise<void>
```

从当前数据库中删除指定设备的数据，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeDeviceData

**系统能力：** SystemCapability.DistributedDataManager.KVStore.DistributedKVStore

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 标识要删除其数据的设备。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例**

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

在手动同步方式下，触发数据库同步。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** sync

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceIds | string[] | 是 | 需要同步DeviceKVStore数据库的设备networkId列表。 |
| mode | [SyncMode](arkts-arkdata-distributeddata-syncmode-e.md) | 是 | 同步模式。 |
| delayMs | number | 否 | 可选参数，允许延时时间，单位：ms（毫秒），默认为0。 |

**示例**

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
