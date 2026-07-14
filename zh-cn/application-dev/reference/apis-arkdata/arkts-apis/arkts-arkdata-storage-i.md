# Storage

提供获取和修改存储数据的接口。

下列接口都需先使用[data_storage.getStorage](arkts-arkdata-getstorage-f.md#getstorage-1)或
[data_storage.getStorageSync](arkts-arkdata-getstoragesync-f.md#getstoragesync-1)获取到Storage实例，再通过此实例调用对应接口。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** preferences

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

## clear

```TypeScript
clear(callback: AsyncCallback<void>): void
```

清除此存储对象中的所有存储。使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** clear

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
storage.clear(function (err) {
    if (err) {
        console.info("Failed to clear the storage with err: " + err);
        return;
    }
    console.info("Succeeded in clearing the storage.");
})

```

## clear

```TypeScript
clear(): Promise<void>
```

清除此存储对象中的所有存储。使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** clear

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```TypeScript
let promiseclear = storage.clear();
promiseclear.then(() => {
    console.info("Succeeded in clearing the storage.");
}).catch((err) => {
    console.info("Failed to clear the storage with err: " + err);
})

```

## clearSync

```TypeScript
clearSync(): void
```

清除此存储对象中的所有存储。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** clear

**示例：**

```TypeScript
storage.clearSync();

```

## delete

```TypeScript
delete(key: string, callback: AsyncCallback<void>): void
```

从存储对象中删除名为给定key的存储。使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** delete

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称，不能为空。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
storage.delete('startup', function (err) {
    if (err) {
        console.info("Failed to delete startup key failed err: " + err);
        return;
    }
    console.info("Succeeded in deleting startup key.");
})

```

## delete

```TypeScript
delete(key: string): Promise<void>
```

从存储对象删除名为给定key的存储。使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** delete

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```TypeScript
let promisedel = storage.delete('startup')
promisedel.then(() => {
    console.info("Succeeded in deleting startup key.");
}).catch((err) => {
    console.info("Failed to delete startup key failed err: " + err);
})

```

## deleteSync

```TypeScript
deleteSync(key: string): void
```

从存储对象中删除名为给定key的存储。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** delete

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称。它不能为空。 |

**示例：**

```TypeScript
 storage.deleteSync('startup');

```

## flush

```TypeScript
flush(callback: AsyncCallback<void>): void
```

将当前storage对象中的修改保存到当前的storage，并异步存储到文件中。使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** flush

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
storage.flush(function (err) {
    if (err) {
        console.info("Failed to flush to file with err: " + err);
        return;
    }
    console.info("Succeeded in flushing to file.");
})

```

## flush

```TypeScript
flush(): Promise<void>
```

将当前storage对象中的修改保存到当前的storage，并异步存储到文件中。使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** flush

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```TypeScript
let promiseflush = storage.flush();
promiseflush.then(() => {
    console.info("Succeeded in flushing to file.");
}).catch((err) => {
    console.info("Failed to flush to file with err: " + err);
})

```

## flushSync

```TypeScript
flushSync(): void
```

将当前storage对象中的修改保存到当前的storage，并同步存储到文件中。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** flush

**示例：**

```TypeScript
storage.flushSync();

```

## get

```TypeScript
get(key: string, defValue: ValueType, callback: AsyncCallback<ValueType>): void
```

获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue。使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称，不能为空。 |
| defValue | ValueType | 是 | 默认返回值。支持number、string、boolean。 |
| callback | AsyncCallback&lt;ValueType&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
storage.get('startup', 'default', function(err, value) {
    if (err) {
        console.info("Failed to get the value of startup with err: " + err);
        return;
      }
    console.info("The value of startup is " + value);
})

```

## get

```TypeScript
get(key: string, defValue: ValueType): Promise<ValueType>
```

获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue。使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称，不能为空。 |
| defValue | ValueType | 是 | 默认返回值。支持number、string、boolean。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;ValueType&gt; | Promise实例，用于异步获取结果。 |

**示例：**

```TypeScript
let promiseget = storage.get('startup', 'default');
promiseget.then((value) => {
    console.info("The value of startup is " + value)
}).catch((err) => {
    console.info("Failed to get the value of startup with err: " + err);
})

```

## getSync

```TypeScript
getSync(key: string, defValue: ValueType): ValueType
```

获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** get

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称，不能为空。 |
| defValue | ValueType | 是 | 给定key的存储不存在，则要返回的默认值。支持number、string、boolean。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ValueType | 键对应的值，如果值为null或者非默认值类型，返回默认数据。 |

**示例：**

```TypeScript
let value = storage.getSync('startup', 'default');
console.info("The value of startup is " + value);

```

## has

```TypeScript
has(key: string, callback: AsyncCallback<boolean>): boolean
```

检查存储对象是否包含名为给定key的存储。使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** has

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称，不能为空。 |
| callback | AsyncCallback&lt;boolean&gt; | 是 | 回调函数。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true表示存在，false表示不存在。 |

**示例：**

```TypeScript
storage.has('startup', function (err, isExist) {
    if (err) {
        console.info("Failed to check the key of startup with err: " + err);
        return;
    }
    if (isExist) {
        console.info("The key of startup is contained.");
    }
})

```

## has

```TypeScript
has(key: string): Promise<boolean>
```

检查存储对象是否包含名为给定key的存储。使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** has

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称，不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise实例，用于异步处理。 |

**示例：**

```TypeScript
let promisehas = storage.has('startup')
promisehas.then((isExist) => {
    if (isExist) {
        console.info("The key of startup is contained.");
    }
}).catch((err) => {
    console.info("Failed to check the key of startup with err: " + err);
})

```

## hasSync

```TypeScript
hasSync(key: string): boolean
```

检查存储对象是否包含名为给定key的存储。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** has

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要获取的存储key名称，不能为空。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true 表示存在，false表示不存在。 |

**示例：**

```TypeScript
let isExist = storage.hasSync('startup');
if (isExist) {
    console.info("The key of startup is contained.");
}

```

## off('change')

```TypeScript
off(type: 'change', callback: Callback<StorageObserver>): void
```

当不再进行订阅数据变更时，使用此接口取消订阅。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** off

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件类型，固定值'change'，表示数据变更。 |
| callback | Callback&lt;StorageObserver&gt; | 是 | 需要取消的回调对象实例。 |

**示例：**

```TypeScript
let observer = function (key) {
    console.info("The key of " + key + " changed.");
}
storage.off('change', observer);

```

## on('change')

```TypeScript
on(type: 'change', callback: Callback<StorageObserver>): void
```

订阅数据变更者类需要实现StorageObserver接口，订阅的key的值发生变更后，在执行flush/flushSync方法后，callback方法会被回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** on

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| type | 'change' | 是 | 事件类型，固定值'change'，表示数据变更。 |
| callback | Callback&lt;StorageObserver&gt; | 是 | 回调对象实例。 |

**示例：**

```TypeScript
let observer = function (key) {
    console.info("The key of " + key + " changed.");
}
storage.on('change', observer);
storage.putSync('startup', 'auto');
storage.flushSync();  // observer will be called.

```

## put

```TypeScript
put(key: string, value: ValueType, callback: AsyncCallback<void>): void
```

首先获取指定文件对应的Storage实例，然后借助Storage API将数据写入Storage实例，通过flush或者flushSync将Storage实例持久化。使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** put

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要修改的存储的key，不能为空。 |
| value | ValueType | 是 | 存储的新值。支持number、string、boolean。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 回调函数。 |

**示例：**

```TypeScript
storage.put('startup', 'auto', function (err) {
    if (err) {
        console.info("Failed to put the value of startup with err: " + err);
        return;
    }
    console.info("Succeeded in putting the value of startup.");
})

```

## put

```TypeScript
put(key: string, value: ValueType): Promise<void>
```

首先获取指定文件对应的Storage实例，然后借助Storage API将数据写入Storage实例，通过flush或者flushSync将Storage实例持久化。使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** put

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要修改的存储的key，不能为空。 |
| value | ValueType | 是 | 存储的新值。支持number、string、boolean。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```TypeScript
let promiseput = storage.put('startup', 'auto');
promiseput.then(() => {
    console.info("Succeeded in putting the value of startup.");
}).catch((err) => {
    console.info("Failed to put the value of startup with err: " + err);
})

```

## putSync

```TypeScript
putSync(key: string, value: ValueType): void
```

首先获取指定文件对应的Storage实例，然后借助Storage API将数据写入Storage实例，通过flush或者flushSync将Storage实例持久化。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** put

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| key | string | 是 | 要修改的存储的key，不能为空。 |
| value | ValueType | 是 | 存储的新值。支持number、string、boolean。 |

**示例：**

```TypeScript
storage.putSync('startup', 'auto');

```

