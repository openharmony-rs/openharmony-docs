# KVStore

KVStore数据库实例，提供增加数据、删除数据和订阅数据变更、订阅数据同步完成的方法。
在调用KVStore的方法前，需要先通过
[getKVStore](arkts-arkdata-kvmanager-i.md#getkvstore-2)
构建一个KVStore实例。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** SingleKVStore

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

## commit

```TypeScript
commit(callback: AsyncCallback<void>): void
```

提交KVStore数据库中的事务，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** commit

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.commit(function (err,data) {
        if (err == undefined) {
            console.log('commit success');
        } else {
            console.log('commit fail');
        }
    });
}catch(e) {
    console.log('Commit e ' + e);
}

```

## commit

```TypeScript
commit(): Promise<void>
```

提交KVStore数据库中的事务，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** commit

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.commit().then(async (err) => {
        console.log('commit success');
    }).catch((err) => {
        console.log('commit fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('Commit e ' + e);
}

```

## delete

```TypeScript
delete(key: string, callback: AsyncCallback<void>): void
```

从数据库中删除指定键值的数据，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** delete

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要删除数据的key，不能为空且长度不大于[MAX_KEY_LENGTH](arkts-arkdata-constants-n.md#constants)。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

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
        kvStore.delete(KEY_TEST_STRING_ELEMENT, function (err,data) {
            if (err != undefined) {
                console.log("delete err: " + JSON.stringify(err));
                return;
            }
            console.log("delete success");
        });
    });
}catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

## delete

```TypeScript
delete(key: string): Promise<void>
```

从数据库中删除指定键值的数据，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** delete

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要删除数据的key，不能为空且长度不大于[MAX_KEY_LENGTH](arkts-arkdata-constants-n.md#constants)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((data) => {
        console.log("put success: " + JSON.stringify(data));
        kvStore.delete(KEY_TEST_STRING_ELEMENT).then((data) => {
            console.log("delete success");
        }).catch((err) => {
            console.log("delete err: " + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log("put err: " + JSON.stringify(err));
    });
}catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

## deleteBatch

```TypeScript
deleteBatch(keys: string[], callback: AsyncCallback<void>): void
```

批量删除KVStore数据库中的键值对，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteBatch

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | string[] | 是 | 表示要批量删除的键值对。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.log('putBatch success');
        kvStore.deleteBatch(keys, async function (err,data) {
            console.log('deleteBatch success');
        });
    });
}catch(e) {
    console.log('DeleteBatch e ' + e);
}

```

## deleteBatch

```TypeScript
deleteBatch(keys: string[]): Promise<void>
```

批量删除KVStore数据库中的键值对，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** deleteBatch

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| keys | string[] | 是 | 表示要批量删除的键值对。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.log('putBatch success');
        kvStore.deleteBatch(keys).then((err) => {
            console.log('deleteBatch success');
        }).catch((err) => {
            console.log('deleteBatch fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log('putBatch fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('DeleteBatch e ' + e);
}

```

## enableSync

```TypeScript
enableSync(enabled: boolean, callback: AsyncCallback<void>): void
```

设定是否开启同步，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** enableSync

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设定是否开启同步，true表示开启同步，false表示不启用同步。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.enableSync(true, function (err,data) {
        if (err == undefined) {
            console.log('enableSync success');
        } else {
            console.log('enableSync fail');
        }
    });
}catch(e) {
    console.log('EnableSync e ' + e);
}

```

## enableSync

```TypeScript
enableSync(enabled: boolean): Promise<void>
```

设定是否开启同步，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** enableSync

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| enabled | boolean | 是 | 设定是否开启同步，true表示开启同步，false表示不启用同步。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.enableSync(true).then((err) => {
        console.log('enableSync success');
    }).catch((err) => {
        console.log('enableSync fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('EnableSync e ' + e);
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
| listener | Callback&lt;ChangeNotification&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

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

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 取消订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | Callback&lt;Array&lt;[string, number]&gt;&gt; | 否 | 取消订阅的函数。如不设置callback，则取消所有订阅的函数。 |

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

**起始版本：** 7

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'dataChange' | 是 | 订阅的事件名，固定为'dataChange'，表示数据变更事件。 |
| type | SubscribeType | 是 | 表示订阅的类型。 |
| listener | Callback&lt;ChangeNotification&gt; | 是 | 回调函数。 |

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

**起始版本：** 7

**废弃版本：** 9

**替代接口：** on

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| event | 'syncComplete' | 是 | 订阅的事件名，固定为'syncComplete'，表示同步完成事件。 |
| syncCallback | Callback&lt;Array&lt;[string, number]&gt;&gt; | 是 | 回调函数。用于向调用方发送同步结果的回调。 |

**示例：**

```TypeScript
let kvStore;
kvStore.on('syncComplete', function (data) {
    console.log("callback call data: " + data);
});

```

## put

```TypeScript
put(key: string, value: Uint8Array | string | number | boolean, callback: AsyncCallback<void>): void
```

添加指定类型键值对到数据库，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** put

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要添加数据的key，不能为空且长度不大于[MAX_KEY_LENGTH](arkts-arkdata-constants-n.md#constants)。 |
| value | Uint8Array \| string \| number \| boolean | 是 | 要添加数据的value，支持Uint8Array、number 、 string 、boolean，Uint8Array、string 的长度不大于[MAX_VALUE_LENGTH](arkts-arkdata-constants-n.md#constants)。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

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
    });
}catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

## put

```TypeScript
put(key: string, value: Uint8Array | string | number | boolean): Promise<void>
```

添加指定类型键值对到数据库，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** put

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要添加数据的key，不能为空且长度不大于[MAX_KEY_LENGTH](arkts-arkdata-constants-n.md#constants)。 |
| value | Uint8Array \| string \| number \| boolean | 是 | 要添加数据的value，支持Uint8Array、number 、 string 、boolean，Uint8Array、string 的长度不大于[MAX_VALUE_LENGTH](arkts-arkdata-constants-n.md#constants)。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
const KEY_TEST_STRING_ELEMENT = 'key_test_string';
const VALUE_TEST_STRING_ELEMENT = 'value-test-string';
try {
    kvStore.put(KEY_TEST_STRING_ELEMENT, VALUE_TEST_STRING_ELEMENT).then((data) => {
        console.log("put success: " + JSON.stringify(data));
    }).catch((err) => {
        console.log("put err: " + JSON.stringify(err));
    });
}catch (e) {
    console.log("An unexpected error occurred. Error:" + e);
}

```

## putBatch

```TypeScript
putBatch(entries: Entry[], callback: AsyncCallback<void>): void
```

批量插入键值对到KVStore数据库中，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** putBatch

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entries | Entry[] | 是 | 表示要批量插入的键值对。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries, async function (err,data) {
        console.log('putBatch success');
        kvStore.getEntries('batch_test_string_key', function (err,entries) {
            console.log('getEntries success');
            console.log('entries.length: ' + entries.length);
            console.log('entries[0]: ' + JSON.stringify(entries[0]));
        });
    });
}catch(e) {
    console.log('PutBatch e ' + JSON.stringify(e));
}

```

## putBatch

```TypeScript
putBatch(entries: Entry[]): Promise<void>
```

批量插入键值对到KVStore数据库中，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** putBatch

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| entries | Entry[] | 是 | 表示要批量插入的键值对。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

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
    console.log('entries: ' + JSON.stringify(entries));
    kvStore.putBatch(entries).then(async (err) => {
        console.log('putBatch success');
        kvStore.getEntries('batch_test_string_key').then((entries) => {
            console.log('getEntries success');
            console.log('PutBatch ' + JSON.stringify(entries));
        }).catch((err) => {
            console.log('getEntries fail ' + JSON.stringify(err));
        });
    }).catch((err) => {
        console.log('putBatch fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('PutBatch e ' + JSON.stringify(e));
}

```

## rollback

```TypeScript
rollback(callback: AsyncCallback<void>): void
```

在KVStore数据库中回滚事务，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** rollback

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.rollback(function (err,data) {
        if (err == undefined) {
            console.log('commit success');
        } else {
            console.log('commit fail');
        }
    });
}catch(e) {
    console.log('Rollback e ' + e);
}

```

## rollback

```TypeScript
rollback(): Promise<void>
```

在KVStore数据库中回滚事务，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** rollback

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    kvStore.rollback().then(async (err) => {
        console.log('rollback success');
    }).catch((err) => {
        console.log('rollback fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('Rollback e ' + e);
}

```

## setSyncRange

```TypeScript
setSyncRange(localLabels: string[], remoteSupportLabels: string[], callback: AsyncCallback<void>): void
```

设置同步范围标签，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSyncRange

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localLabels | string[] | 是 | 表示本地设备的同步标签。 |
| remoteSupportLabels | string[] | 是 | 表示要同步数据的设备的同步标签。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
let kvStore;
try {
    const localLabels = ['A', 'B'];
    const remoteSupportLabels = ['C', 'D'];
    kvStore.setSyncRange(localLabels, remoteSupportLabels, function (err,data) {
        console.log('SetSyncRange put success');
    });
}catch(e) {
    console.log('SetSyncRange e ' + e);
}

```

## setSyncRange

```TypeScript
setSyncRange(localLabels: string[], remoteSupportLabels: string[]): Promise<void>
```

设置同步范围标签，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** setSyncRange

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| localLabels | string[] | 是 | 表示本地设备的同步标签。 |
| remoteSupportLabels | string[] | 是 | 表示要同步数据的设备的同步标签。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    const localLabels = ['A', 'B'];
    const remoteSupportLabels = ['C', 'D'];
    kvStore.setSyncRange(localLabels, remoteSupportLabels).then((err) => {
        console.log('setSyncRange success');
    }).catch((err) => {
        console.log('delete fail ' + err);
    });
}catch(e) {
    console.log('SetSyncRange e ' + e);
}

```

## startTransaction

```TypeScript
startTransaction(callback: AsyncCallback<void>): void
```

启动KVStore数据库中的事务，使用callback异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** startTransaction

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

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
        console.log('startTransaction 0' + data)
        count++;
    });
    kvStore.startTransaction(async function (err,data) {
        console.log('startTransaction success');
        let entries = putBatchString(10, 'batch_test_string_key');
        console.log('entries: ' + JSON.stringify(entries));
        kvStore.putBatch(entries, async function (err,data) {
            console.log('putBatch success');
        });
    });
}catch(e) {
    console.log('startTransaction e ' + e);
}

```

## startTransaction

```TypeScript
startTransaction(): Promise<void>
```

启动KVStore数据库中的事务，使用Promise异步回调。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** startTransaction

**系统能力：** SystemCapability.DistributedDataManager.KVStore.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**示例：**

```TypeScript
let kvStore;
try {
    var count = 0;
    kvStore.on('dataChange', distributedData.SubscribeType.SUBSCRIBE_TYPE_ALL, function (data) {
        console.log('startTransaction ' + JSON.stringify(data));
        count++;
    });
    kvStore.startTransaction().then(async (err) => {
        console.log('startTransaction success');
    }).catch((err) => {
        console.log('startTransaction fail ' + JSON.stringify(err));
    });
}catch(e) {
    console.log('startTransaction e ' + e);
}

```

