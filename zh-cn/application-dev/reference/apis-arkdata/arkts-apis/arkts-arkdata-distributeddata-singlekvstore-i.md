# SingleKVStore

单版本数据库，继承自[KVStore](arkts-arkdata-distributeddata-kvstoretype-e.md)数据库，提供查询数据和同步数据的方法。单版本数据库，不对数据所属设备进行区分，不同设备使用相同键写入数据会互相覆盖。比如，可以使用单版本数据库实现个人日历、联系人数据在不同设备间的数据同步。在调用SingleKVStore的方法前，需要先通过[getKVStore](distributedData.KVManager.getKVStore<T extends KVStore>(storeId: string, options: Options, callback: AsyncCallback<T>))构建一个SingleKVStore实例。

**继承/实现关系：** SingleKVStore extends [KVStore](arkts-arkdata-distributeddata-kvstore-i.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** SingleKVStore

<!--Device-distributedData-interface SingleKVStore extends KVStore--><!--Device-distributedData-interface SingleKVStore extends KVStore-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

<a id="closeresultset"></a>
## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void
```

关闭由[SingleKVStore.getResultSet](arkts-arkdata-distributeddata-singlekvstore-i.md#getresultset-1)返回的KvStoreResultSet对象，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeResultSet

<!--Device-SingleKVStore-closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-closeResultSet(resultSet: KvStoreResultSet, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | 是 | 表示要关闭的KvStoreResultSet对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
try {
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

<a id="closeresultset-1"></a>
## closeResultSet

```TypeScript
closeResultSet(resultSet: KvStoreResultSet): Promise<void>
```

关闭由[SingleKVStore.getResultSet](arkts-arkdata-distributeddata-singlekvstore-i.md#getresultset-1)返回的KvStoreResultSet对象，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** closeResultSet

<!--Device-SingleKVStore-closeResultSet(resultSet: KvStoreResultSet): Promise<void>--><!--Device-SingleKVStore-closeResultSet(resultSet: KvStoreResultSet): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| resultSet | [KvStoreResultSet](arkts-arkdata-distributeddata-kvstoreresultset-i.md) | 是 | 表示要关闭的KvStoreResultSet对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
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

<a id="get"></a>
## get

```TypeScript
get(key: string, callback: AsyncCallback<Uint8Array | string | boolean | number>): void
```

获取指定键的值，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** get

<!--Device-SingleKVStore-get(key: string, callback: AsyncCallback<Uint8Array | string | boolean | number>): void--><!--Device-SingleKVStore-get(key: string, callback: AsyncCallback<Uint8Array | string | boolean | number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要查询数据的key，不能为空且长度不大于[MAX_KEY_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants)。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Uint8Array \| string \| boolean \| number&gt; | 是 | 回调函数。返回获取查询的值。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, function (err,data) {
        if (err != undefined) {
            console.log("put err: " + JSON.stringify(err));
            return;
        }
        console.log("put success");
        kvStore.get(KEY_TEST_STRING_ELEMENT, function (err,data) {
            console.log("get success data: " + data);
        });
    });
}catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

<a id="get-1"></a>
## get

```TypeScript
get(key: string): Promise<Uint8Array | string | boolean | number>
```

获取指定键的值，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** get

<!--Device-SingleKVStore-get(key: string): Promise<Uint8Array | string | boolean | number>--><!--Device-SingleKVStore-get(key: string): Promise<Uint8Array | string | boolean | number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要查询数据的key，不能为空且长度不大于[MAX_KEY_LENGTH](arkts-arkdata-distributeddata-constants-n.md#constants)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Uint8Array \| string \| boolean \| number&gt; | Promise对象。返回获取查询的值。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((data) => {
        console.log("put success: " + JSON.stringify(data));
        kvStore.get(KEY_TEST_STRING_ELEMENT).then((data) => {
            console.log("get success data: " + data);
        }).catch((err) => {
            console.log("get err: " + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log("put err: " + JSON.stringify(err));
    });
}catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

<a id="getentries"></a>
## getEntries

```TypeScript
getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void
```

获取匹配指定键前缀的所有键值对，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-SingleKVStore-getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void--><!--Device-SingleKVStore-getEntries(keyPrefix: string, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Entry[]&gt; | 是 | 回调函数。返回匹配指定前缀的键值对列表。 |

**示例：**

```TypeScript
let kvStore;
try {
    let entries = [];
    for (var i = 0; i < 10; i++) {
        var key = 'batch_test_number_key';
        var entry = {
            key : key + i,
            value : {
                type : distributedData.ValueType.INTEGER,
                value : 222
            }
        }
        entries.push(entry);
    }
    kvStore.putBatch(entries, async function (err,data) {
        console.log('putBatch success');
        kvStore.getEntries('batch_test_number_key', function (err,entries) {
            console.log('getEntries success');
            console.log('entries.length: ' + entries.length);
            console.log('entries[0]: ' + JSON.stringify(entries[0]));
        });
    });
}catch(e) {
    console.log('PutBatch e ' + e);
}

```

<a id="getentries-1"></a>
## getEntries

```TypeScript
getEntries(keyPrefix: string): Promise<Entry[]>
```

获取匹配指定键前缀的所有键值对，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-SingleKVStore-getEntries(keyPrefix: string): Promise<Entry[]>--><!--Device-SingleKVStore-getEntries(keyPrefix: string): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回匹配指定前缀的键值对列表。 |

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
        kvStore.getEntries('batch_test_string_key').then((entries) => {
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

<a id="getentries-2"></a>
## getEntries

```TypeScript
getEntries(query: Query, callback: AsyncCallback<Entry[]>): void
```

获取与指定Query对象匹配的键值对列表，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-SingleKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void--><!--Device-SingleKVStore-getEntries(query: Query, callback: AsyncCallback<Entry[]>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示要匹配的键前缀。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Entry[]&gt; | 是 | 回调函数。返回与指定Query对象匹配的键值对列表。 |

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

<a id="getentries-3"></a>
## getEntries

```TypeScript
getEntries(query: Query): Promise<Entry[]>
```

获取与指定Query对象匹配的键值对列表，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getEntries

<!--Device-SingleKVStore-getEntries(query: Query): Promise<Entry[]>--><!--Device-SingleKVStore-getEntries(query: Query): Promise<Entry[]>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Entry[]&gt; | Promise对象。返回与指定Query对象匹配的键值对列表。 |

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

<a id="getresultset"></a>
## getResultSet

```TypeScript
getResultSet(keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void
```

从KvStore数据库中获取具有指定前缀的结果集，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-SingleKVStore-getResultSet(keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-SingleKVStore-getResultSet(keyPrefix: string, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;KvStoreResultSet&gt; | 是 | 回调函数。返回具有指定前缀的结果集。 |

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
        console.log('GetResultSet putBatch success');
        kvStore.getResultSet('batch_test_string_key', async function (err, result) {
            console.log('GetResultSet getResultSet succeed.');
            resultSet = result;
            kvStore.closeResultSet(resultSet, function (err, data) {
                console.log('GetResultSet closeResultSet success');
            })
        });
    });
}catch(e) {
    console.log('GetResultSet e ' + e);
}

```

<a id="getresultset-1"></a>
## getResultSet

```TypeScript
getResultSet(keyPrefix: string): Promise<KvStoreResultSet>
```

从KVStore数据库中获取具有指定前缀的结果集，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSet

<!--Device-SingleKVStore-getResultSet(keyPrefix: string): Promise<KvStoreResultSet>--><!--Device-SingleKVStore-getResultSet(keyPrefix: string): Promise<KvStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keyPrefix | string | 是 | 表示要匹配的键前缀。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KvStoreResultSet&gt; | Promise对象。返回具有指定前缀的结果集。 |

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
        console.log('PutBatch putBatch fail ' + JSON.stringify(err));
    });
    kvStore.getResultSet('batch_test_string_key').then((result) => {
        console.log('GetResult getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.log('getResultSet failed: ' + JSON.stringify(err));
    });
    kvStore.closeResultSet(resultSet).then((err) => {
        console.log('GetResult closeResultSet success');
    }).catch((err) => {
        console.log('closeResultSet fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetResult e ' + e);
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

<!--Device-SingleKVStore-getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void--><!--Device-SingleKVStore-getResultSet(query: Query, callback: AsyncCallback<KvStoreResultSet>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;KvStoreResultSet&gt; | 是 | 回调函数，获取与指定Query对象匹配的KvStoreResultSet对象。 |

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
        kvStore.getResultSet(query, async function (err, result) {
            console.log('getResultSet succeed.');
            resultSet = result;
        });
    });
} catch(e) {
    console.log('GetResultSet e ' + e);
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

<!--Device-SingleKVStore-getResultSet(query: Query): Promise<KvStoreResultSet>--><!--Device-SingleKVStore-getResultSet(query: Query): Promise<KvStoreResultSet>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;KvStoreResultSet&gt; | Promise对象。获取与指定Query对象匹配的KvStoreResultSet对象。 |

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
        console.log('putBatch fail ' + JSON.stringify(err));
    });
    const query = new distributedData.Query();
    query.prefixKey("batch_test");
    kvStore.getResultSet(query).then((result) => {
        console.log(' getResultSet succeed.');
        resultSet = result;
    }).catch((err) => {
        console.log('getResultSet failed: ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetResultSet e ' + e);
}

```

<a id="getresultsize"></a>
## getResultSize

```TypeScript
getResultSize(query: Query, callback: AsyncCallback<number>): void
```

获取与指定Query对象匹配的结果数，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getResultSize

<!--Device-SingleKVStore-getResultSize(query: Query, callback: AsyncCallback<number>): void--><!--Device-SingleKVStore-getResultSize(query: Query, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。返回与指定Query对象匹配的结果数。 |

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
        kvStore.getResultSize(query, async function (err, resultSize) {
            console.log('getResultSet succeed.');
        });
    });
} catch(e) {
    console.log('GetResultSize e ' + e);
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

<!--Device-SingleKVStore-getResultSize(query: Query): Promise<number>--><!--Device-SingleKVStore-getResultSize(query: Query): Promise<number>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| query | [Query](arkts-arkdata-distributeddata-query-c.md) | 是 | 表示查询对象。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。获取与指定Query对象匹配的结果数。 |

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
    kvStore.getResultSize(query).then((resultSize) => {
        console.log('getResultSet succeed.');
    }).catch((err) => {
        console.log('getResultSet failed: ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetResultSize e ' + e);
}

```

<a id="getsecuritylevel"></a>
## getSecurityLevel

```TypeScript
getSecurityLevel(callback: AsyncCallback<SecurityLevel>): void
```

获取数据库的安全级别，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getSecurityLevel

<!--Device-SingleKVStore-getSecurityLevel(callback: AsyncCallback<SecurityLevel>): void--><!--Device-SingleKVStore-getSecurityLevel(callback: AsyncCallback<SecurityLevel>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;SecurityLevel&gt; | 是 | 回调函数。返回数据库的安全级别。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.getSecurityLevel(function (err,data) {
        console.log('getSecurityLevel success');
    });
}catch(e) {
    console.log('GetSecurityLevel e ' + e);
}

```

<a id="getsecuritylevel-1"></a>
## getSecurityLevel

```TypeScript
getSecurityLevel(): Promise<SecurityLevel>
```

获取数据库的安全级别，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** getSecurityLevel

<!--Device-SingleKVStore-getSecurityLevel(): Promise<SecurityLevel>--><!--Device-SingleKVStore-getSecurityLevel(): Promise<SecurityLevel>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;SecurityLevel&gt; | Promise对象。返回数据库的安全级别。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.getSecurityLevel().then((data) => {
        console.log(' getSecurityLevel success');
    }).catch((err) => {
        console.log('getSecurityLevel fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('GetSecurityLevel e ' + e);
}

```

<a id="off"></a>
## off

```TypeScript
off(event: 'dataChange', listener?: Callback<ChangeNotification>): void
```

取消订阅数据变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

<!--Device-SingleKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void--><!--Device-SingleKVStore-off(event: 'dataChange', listener?: Callback<ChangeNotification>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 取消订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| listener | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ChangeNotification&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

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

<a id="off-1"></a>
## off

```TypeScript
off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void
```

取消订阅同步完成事件回调通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** off

<!--Device-SingleKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void--><!--Device-SingleKVStore-off(event: 'syncComplete', syncCallback?: Callback<Array<[string, number]>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 取消订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

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

<a id="on"></a>
## on

```TypeScript
on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void
```

订阅指定类型的数据变更通知。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** on

<!--Device-SingleKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void--><!--Device-SingleKVStore-on(event: 'dataChange', type: SubscribeType, listener: Callback<ChangeNotification>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| type | [SubscribeType](../../apis-notification-kit/arkts-apis/arkts-notification-notificationextensionsubscription-subscribetype-e.md) | 是 | 表示订阅的类型。 |
| listener | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;ChangeNotification&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
kvStore.on('dataChange', distributedData.SubscribeType.SUBSCRIBE_TYPE_LOCAL, function (data) {
    console.log("dataChange callback call data: " + JSON.stringify(data));
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

<!--Device-SingleKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void--><!--Device-SingleKVStore-on(event: 'syncComplete', syncCallback: Callback<Array<[string, number]>>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | [Callback](../../apis-arkui/arkts-components/arkts-arkui-callback-i.md)&lt;Array&lt;[string, number]&gt;&gt; | 是 | 回调函数。用于向调用方发送同步结果的回调。 |

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

<a id="removedevicedata"></a>
## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void
```

删除指定设备的数据，使用callback异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeDeviceData

<!--Device-SingleKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-removeDeviceData(deviceId: string, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示要删除设备的名称。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-002';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT, async function (err,data) {
        console.log('put success');
        const deviceid = 'no_exist_device_id';
        kvStore.removeDeviceData(deviceid, async function (err,data) {
            if (err == undefined) {
                console.log('removeDeviceData success');
            } else {
                console.log('removeDeviceData fail');
                kvStore.get(KEY_TEST_STRING_ELEMENT, async function (err,data) {
                    console.log('RemoveDeviceData get success');
                });
            }
        });
    });
}catch(e) {
    console.log('RemoveDeviceData e ' + e);
}

```

<a id="removedevicedata-1"></a>
## removeDeviceData

```TypeScript
removeDeviceData(deviceId: string): Promise<void>
```

删除指定设备的数据，使用Promise异步回调。

> **说明：**  
>  
> 其中deviceId通过调用<!--RP1-->  
> [deviceManager.getTrustedDeviceListSync](../../apis-distributed-service-kit/arkts-apis/arkts-distributedservice-devicemanager-devicemanager-i-sys.md#gettrusteddevicelistsync-1)  
> 方法得到。<!--RP1End-->deviceManager模块的接口均为系统接口，仅系统应用可用。  
> > deviceId具体获取方式请参考[sync接口示例](arkts-arkdata-distributeddata-singlekvstore-i.md#sync-1)。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** removeDeviceData

<!--Device-SingleKVStore-removeDeviceData(deviceId: string): Promise<void>--><!--Device-SingleKVStore-removeDeviceData(deviceId: string): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceId | string | 是 | 表示要删除设备的名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string_2';
const VALUE_TEST_STRING_ELEMENT = 'value-string-001';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((err) => {
        console.log('removeDeviceData put success');
    }).catch((err) => {
        console.log('put fail ' + JSON.stringify(err));
    });
    const deviceid = 'no_exist_device_id';
    kvStore.removeDeviceData(deviceid).then((err) => {
        console.log('removeDeviceData success');
    }).catch((err) => {
        console.log('removeDeviceData fail ' + JSON.stringify(err));
    });
    kvStore.get(KEY_TEST_STRING_ELEMENT).then((data) => {
        console.log('get success data:' + data);
    }).catch((err) => {
        console.log('RemoveDeviceData get fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('RemoveDeviceData e ' + e);
}

```

<a id="setsyncparam"></a>
## setSyncParam

```TypeScript
setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback<void>): void
```

设置数据库同步允许的默认延迟，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSyncParam

<!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback<void>): void--><!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: number, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultAllowedDelayMs | number | 是 | 表示数据库同步允许的默认延迟，以毫秒为单位。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
try {
    const defaultAllowedDelayMs = 500;
    kvStore.setSyncParam(defaultAllowedDelayMs, function (err,data) {
        console.log('SetSyncParam put success');
    });
}catch(e) {
    console.log('testSingleKvStoreSetSyncParam e ' + e);
}

```

<a id="setsyncparam-1"></a>
## setSyncParam

```TypeScript
setSyncParam(defaultAllowedDelayMs: number): Promise<void>
```

设置数据库同步允许的默认延迟，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSyncParam

<!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: number): Promise<void>--><!--Device-SingleKVStore-setSyncParam(defaultAllowedDelayMs: number): Promise<void>-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| defaultAllowedDelayMs | number | 是 | 表示数据库同步允许的默认延迟，以毫秒为单位。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    const defaultAllowedDelayMs = 500;
    kvStore.setSyncParam(defaultAllowedDelayMs).then((err) => {
        console.log('SetSyncParam put success');
    }).catch((err) => {
        console.log('SetSyncParam put fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('SetSyncParam e ' + e);
}

```

<a id="sync"></a>
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

**起始版本：** 7

**废弃版本：** 9

**替代接口：** sync

**需要权限：** ohos.permission.DISTRIBUTED_DATASYNC

<!--Device-SingleKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void--><!--Device-SingleKVStore-sync(deviceIds: string[], mode: SyncMode, delayMs?: number): void-End-->

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| deviceIds | string[] | 是 | 同一组网环境下，需要同步的设备的networkId列表。 |
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

