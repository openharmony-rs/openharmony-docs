# @ohos.data.storage (轻量级存储)
<!--Kit: ArkData-->
<!--Subsystem: DistributedDataManager-->
<!--Owner: @yanhuii-->
<!--Designer: @houpengtao1-->
<!--Tester: @yippo; @logic42-->
<!--Adviser: @ge-yafang-->

轻量级存储为应用提供key-value键值型的文件数据处理能力，支持应用对数据进行轻量级存储及查询。数据存储形式为键值对，键的类型为字符串型，值的存储数据类型包括数字型、字符型、布尔型。

> **说明：**
>
> -  本模块首批接口从API version 6开始支持。后续版本的新增接口，采用上角标单独标记接口的起始版本。
>
> -  从API version 9开始，该接口不再维护，推荐使用新接口[`@ohos.data.preferences`](js-apis-data-preferences.md)。


## 导入模块

```js
import data_storage from '@ohos.data.storage';
```

## 常量

**系统能力：** 以下各项对应的系统能力均为SystemCapability.DistributedDataManager.Preferences.Core

| 名称             | 类型 | 可读 | 可写 | 说明                                  |
| ---------------- | -------- | ---- | ---- | ------------------------------------- |
| MAX_KEY_LENGTH   | number   | 是   | 否   | key的最大长度限制为80字节。     |
| MAX_VALUE_LENGTH | number   | 是   | 否   | value的最大长度限制为8192字节。 |


## data_storage.getStorageSync

getStorageSync(path: string): Storage

读取指定文件，将数据加载到Storage实例，用于数据操作。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| path   | string | 是   | 应用程序内部数据存储路径。 |

**返回值：**

| 类型                | 说明                                              |
| ------------------- | ------------------------------------------------- |
| [Storage](#storage) | 获取到要操作的Storage实例，用于进行数据存储操作。 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
  path = filePath;
  console.info("======================>getFilesDirPromise====================>");

  let storage = data_storage.getStorageSync(path + '/mystore');
  storage.putSync('startup', 'auto');
  storage.flushSync();
});
```


## data_storage.getStorage

getStorage(path: string, callback: AsyncCallback&lt;Storage&gt;): void

读取指定文件，将数据加载到Storage实例，用于数据操作，使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                                     | 必填 | 说明                       |
| -------- | ---------------------------------------- | ---- | -------------------------- |
| path     | string                                   | 是   | 应用程序内部数据存储路径。 |
| callback | AsyncCallback&lt;[Storage](#storage)&gt; | 是   | 回调函数。                 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
  path = filePath;
  console.info("======================>getFilesDirPromise====================>");

  data_storage.getStorage(path + '/mystore', function (err, storage) {
    if (err) {
      console.info("Failed to get the storage. path: " + path + '/mystore');
      return;
    }
    storage.putSync('startup', 'auto');
    storage.flushSync();
  })
});
```


## data_storage.getStorage

getStorage(path: string): Promise&lt;Storage&gt;

读取指定文件，将数据加载到Storage实例，用于数据操作，使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| path   | string | 是   | 应用程序内部数据存储路径。 |

**返回值：**

| 类型                               | 说明                            |
| ---------------------------------- | ------------------------------- |
| Promise&lt;[Storage](#storage)&gt; | Promise实例，用于异步获取结果。 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
  path = filePath;
  console.info("======================>getFilesDirPromise====================>");

  let getPromise = data_storage.getStorage(path + '/mystore');
  getPromise.then((storage) => {
    storage.putSync('startup', 'auto');
    storage.flushSync();
  }).catch((err) => {
    console.info("Failed to get the storage. path: " + path + '/mystore');
  })
});
```


## data_storage.deleteStorageSync

deleteStorageSync(path: string): void

从内存中移除指定文件对应的Storage单实例，并删除指定文件及其备份文件、损坏文件。删除指定文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| path   | string | 是   | 应用程序内部数据存储路径。 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
    path = filePath;
    console.info("======================>getFilesDirPromise====================>");

    data_storage.deleteStorageSync(path + '/mystore');
});
```

## data_storage.deleteStorage

deleteStorage(path: string, callback: AsyncCallback&lt;void&gt;): void

从内存中移除指定文件对应的Storage单实例，并删除指定文件及其备份文件、损坏文件。删除指定文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题，使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                      | 必填 | 说明                       |
| -------- | ------------------------- | ---- | -------------------------- |
| path     | string                    | 是   | 应用程序内部数据存储路径。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。                 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
  path = filePath;
  console.info("======================>getFilesDirPromise====================>");

  data_storage.deleteStorage(path + '/mystore', function (err) {
    if (err) {
      console.info("Failed to delete the storage with err: " + err);
      return;
    }
    console.info("Succeeded in deleting the storage.");
  })
});
```


## data_storage.deleteStorage

deleteStorage(path: string): Promise&lt;void&gt;

从内存中移除指定文件对应的Storage单实例，并删除指定文件及其备份文件、损坏文件。删除指定文件时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题，使用promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| path   | string | 是   | 应用程序内部数据存储路径。 |

**返回值：**

| 类型                | 说明                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise实例，用于异步获取结果。 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
  path = filePath;
  console.info("======================>getFilesDirPromise====================>");

  let promisedelSt = data_storage.deleteStorage(path + '/mystore');
  promisedelSt.then(() => {
    console.info("Succeeded in deleting the storage.");
  }).catch((err) => {
    console.info("Failed to delete the storage with err: " + err);
  })
});
```


## data_storage.removeStorageFromCacheSync

removeStorageFromCacheSync(path: string): void

从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**
| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| path   | string | 是   | 应用程序内部数据存储路径。 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
    path = filePath;
    console.info("======================>getFilesDirPromise====================>");

    data_storage.removeStorageFromCacheSync(path + '/mystore');
});
```


## data_storage.removeStorageFromCache

removeStorageFromCache(path: string, callback: AsyncCallback&lt;void&gt;): void

从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                      | 必填 | 说明                       |
| -------- | ------------------------- | ---- | -------------------------- |
| path     | string                    | 是   | 应用程序内部数据存储路径。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。                 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
  path = filePath;
  console.info("======================>getFilesDirPromise====================>");

  data_storage.removeStorageFromCache(path + '/mystore', function (err) {
    if (err) {
      console.info("Failed to remove storage from cache with err: " + err);
      return;
    }
    console.info("Succeeded in removing storage from cache.");
  })
});
```


## data_storage.removeStorageFromCache

removeStorageFromCache(path: string): Promise&lt;void&gt;

从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                       |
| ------ | ------ | ---- | -------------------------- |
| path   | string | 是   | 应用程序内部数据存储路径。 |

**返回值：**

| 类型                | 说明                            |
| ------------------- | ------------------------------- |
| Promise&lt;void&gt; | Promise实例，用于异步获取结果。 |

**示例：**

```js
import featureAbility from '@ohos.ability.featureAbility';

let path;
let context = featureAbility.getContext();
context.getFilesDir().then((filePath) => {
  path = filePath;
  console.info("======================>getFilesDirPromise====================>");

  let promiserevSt = data_storage.removeStorageFromCache(path + '/mystore')
  promiserevSt.then(() => {
    console.info("Succeeded in removing storage from cache.");
  }).catch((err) => {
    console.info("Failed to remove storage from cache with err: " + err);
  })
});
```

## Storage

提供获取和修改存储数据的接口。

下列接口都需先使用[data_storage.getStorage](#data_storagegetstorage)或[data_storage.getStorageSync](#data_storagegetstoragesync)获取到Storage实例，再通过此实例调用对应接口。

### getSync

getSync(key: string, defValue: ValueType): ValueType

获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                                         |
| -------- | ----------------------- | ---- | ------------------------------------------------------------ |
| key      | string                  | 是   | 要获取的存储key名称，不能为空。                              |
| defValue | [ValueType](#valuetype) | 是   | 给定key的存储不存在，则要返回的默认值。支持number、string、boolean。 |

**返回值：**

| 类型      | 说明                                                     |
| --------- | -------------------------------------------------------- |
| ValueType | 键对应的值，如果值为null或者非默认值类型，返回默认数据。 |

**示例：**

```js
let value = storage.getSync('startup', 'default');
console.info("The value of startup is " + value);
```


### get

get(key: string, defValue: ValueType, callback: AsyncCallback&lt;ValueType&gt;): void

获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue。使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                           | 必填 | 说明                                      |
| -------- | ------------------------------ | ---- | ----------------------------------------- |
| key      | string                         | 是   | 要获取的存储key名称，不能为空。           |
| defValue | [ValueType](#valuetype)        | 是   | 默认返回值。支持number、string、boolean。 |
| callback | AsyncCallback&lt;ValueType&gt; | 是   | 回调函数。                                |

**示例：**

```js
storage.get('startup', 'default', function(err, value) {
    if (err) {
        console.info("Failed to get the value of startup with err: " + err);
        return;
      }
    console.info("The value of startup is " + value);
})
```


### get

get(key: string, defValue: ValueType): Promise&lt;ValueType&gt;

获取键对应的值，如果值为null或者非默认值类型，返回默认数据defValue。使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                    | 必填 | 说明                                      |
| -------- | ----------------------- | ---- | ----------------------------------------- |
| key      | string                  | 是   | 要获取的存储key名称，不能为空。           |
| defValue | [ValueType](#valuetype) | 是   | 默认返回值。支持number、string、boolean。 |

**返回值：**

| 类型                     | 说明                            |
| ------------------------ | ------------------------------- |
| Promise&lt;ValueType&gt; | Promise实例，用于异步获取结果。 |

**示例：**

```js
let promiseget = storage.get('startup', 'default');
promiseget.then((value) => {
    console.info("The value of startup is " + value)
}).catch((err) => {
    console.info("Failed to get the value of startup with err: " + err);
})
```


### putSync

putSync(key: string, value: ValueType): void

首先获取指定文件对应的Storage实例，然后借助Storage API将数据写入Storage实例，通过flush或者flushSync将Storage实例持久化。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型                    | 必填 | 说明                                      |
| ------ | ----------------------- | ---- | ----------------------------------------- |
| key    | string                  | 是   | 要修改的存储的key，不能为空。             |
| value  | [ValueType](#valuetype) | 是   | 存储的新值。支持number、string、boolean。 |

**示例：**

```js
storage.putSync('startup', 'auto');
```


### put

put(key: string, value: ValueType, callback: AsyncCallback&lt;void&gt;): void

首先获取指定文件对应的Storage实例，然后借助Storage API将数据写入Storage实例，通过flush或者flushSync将Storage实例持久化。使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                      | 必填 | 说明                                      |
| -------- | ------------------------- | ---- | ----------------------------------------- |
| key      | string                    | 是   | 要修改的存储的key，不能为空。             |
| value    | [ValueType](#valuetype)   | 是   | 存储的新值。支持number、string、boolean。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。                                |

**示例：**

```js
storage.put('startup', 'auto', function (err) {
    if (err) {
        console.info("Failed to put the value of startup with err: " + err);
        return;
    }
    console.info("Succeeded in putting the value of startup.");
})
```


### put

put(key: string, value: ValueType): Promise&lt;void&gt;

首先获取指定文件对应的Storage实例，然后借助Storage API将数据写入Storage实例，通过flush或者flushSync将Storage实例持久化。使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型                    | 必填 | 说明                                      |
| ------ | ----------------------- | ---- | ----------------------------------------- |
| key    | string                  | 是   | 要修改的存储的key，不能为空。             |
| value  | [ValueType](#valuetype) | 是   | 存储的新值。支持number、string、boolean。 |

**返回值：**

| 类型                | 说明                        |
| ------------------- | --------------------------- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```js
let promiseput = storage.put('startup', 'auto');
promiseput.then(() => {
    console.info("Succeeded in putting the value of startup.");
}).catch((err) => {
    console.info("Failed to put the value of startup with err: " + err);
})
```


### hasSync

hasSync(key: string): boolean

检查存储对象是否包含名为给定key的存储。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                            |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | 是   | 要获取的存储key名称，不能为空。 |

**返回值：**

| 类型    | 说明                                  |
| ------- | ------------------------------------- |
| boolean | true&nbsp;表示存在，false表示不存在。 |

**示例：**

```js
let isExist = storage.hasSync('startup');
if (isExist) {
    console.info("The key of startup is contained.");
}
```


### has

has(key: string, callback: AsyncCallback&lt;boolean&gt;): boolean

检查存储对象是否包含名为给定key的存储。使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                         | 必填 | 说明                            |
| -------- | ---------------------------- | ---- | ------------------------------- |
| key      | string                       | 是   | 要获取的存储key名称，不能为空。 |
| callback | AsyncCallback&lt;boolean&gt; | 是   | 回调函数。                      |

**返回值：**

| 类型    | 说明                            |
| ------- | ------------------------------- |
| boolean | true表示存在，false表示不存在。 |

**示例：**

```js
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


### has

has(key: string): Promise&lt;boolean&gt;

检查存储对象是否包含名为给定key的存储。使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                            |
| ------ | ------ | ---- | ------------------------------- |
| key    | string | 是   | 要获取的存储key名称，不能为空。 |

**返回值：**

| 类型                   | 说明                        |
| ---------------------- | --------------------------- |
| Promise&lt;boolean&gt; | Promise实例，用于异步处理。 |

**示例：**

```js
let promisehas = storage.has('startup')
promisehas.then((isExist) => {
    if (isExist) {
        console.info("The key of startup is contained.");
    }
}).catch((err) => {
    console.info("Failed to check the key of startup with err: " + err);
})
```


### deleteSync

deleteSync(key: string): void

从存储对象中删除名为给定key的存储。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                              |
| ------ | ------ | ---- | --------------------------------- |
| key    | string | 是   | 要获取的存储key名称。它不能为空。 |

**示例：**

```js
 storage.deleteSync('startup');
```


### delete

delete(key: string, callback: AsyncCallback&lt;void&gt;): void

从存储对象中删除名为给定key的存储。使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                      | 必填 | 说明                            |
| -------- | ------------------------- | ---- | ------------------------------- |
| key      | string                    | 是   | 要获取的存储key名称，不能为空。 |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。                      |

**示例：**

```js
storage.delete('startup', function (err) {
    if (err) {
        console.info("Failed to delete startup key failed err: " + err);
        return;
    }
    console.info("Succeeded in deleting startup key.");
})
```


### delete

delete(key: string): Promise&lt;void&gt;

从存储对象删除名为给定key的存储。使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名 | 类型   | 必填 | 说明                  |
| ------ | ------ | ---- | --------------------- |
| key    | string | 是   | 要获取的存储key名称。 |

**返回值：**

| 类型                | 说明                        |
| ------------------- | --------------------------- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```js
let promisedel = storage.delete('startup')
promisedel.then(() => {
    console.info("Succeeded in deleting startup key.");
}).catch((err) => {
    console.info("Failed to delete startup key failed err: " + err);
})
```


### flushSync

flushSync(): void

将当前storage对象中的修改保存到当前的storage，并同步存储到文件中。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**示例：**

```js
storage.flushSync();
```


### flush

flush(callback: AsyncCallback&lt;void&gt;): void

将当前storage对象中的修改保存到当前的storage，并异步存储到文件中。使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                      | 必填 | 说明       |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。 |

**示例：**

```js
storage.flush(function (err) {
    if (err) {
        console.info("Failed to flush to file with err: " + err);
        return;
    }
    console.info("Succeeded in flushing to file.");
})
```


### flush

flush(): Promise&lt;void&gt;

将当前storage对象中的修改保存到当前的storage，并异步存储到文件中。使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**

| 类型                | 说明                        |
| ------------------- | --------------------------- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```js
let promiseflush = storage.flush();
promiseflush.then(() => {
    console.info("Succeeded in flushing to file.");
}).catch((err) => {
    console.info("Failed to flush to file with err: " + err);
})
```


### clearSync

clearSync(): void

清除此存储对象中的所有存储。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**示例：**

```js
storage.clearSync();
```


### clear

clear(callback: AsyncCallback&lt;void&gt;): void

清除此存储对象中的所有存储。使用callback方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                      | 必填 | 说明       |
| -------- | ------------------------- | ---- | ---------- |
| callback | AsyncCallback&lt;void&gt; | 是   | 回调函数。 |

**示例：**

```js
storage.clear(function (err) {
    if (err) {
        console.info("Failed to clear the storage with err: " + err);
        return;
    }
    console.info("Succeeded in clearing the storage.");
})
```


### clear

clear(): Promise&lt;void&gt;

清除此存储对象中的所有存储。使用Promise方式返回结果，此方法为异步方法。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**返回值：**
| 类型                | 说明                        |
| ------------------- | --------------------------- |
| Promise&lt;void&gt; | Promise实例，用于异步处理。 |

**示例：**

```js
let promiseclear = storage.clear();
promiseclear.then(() => {
    console.info("Succeeded in clearing the storage.");
}).catch((err) => {
    console.info("Failed to clear the storage with err: " + err);
})
```


### on('change')

on(type: 'change', callback: Callback&lt;StorageObserver&gt;): void

订阅数据变更者类需要实现StorageObserver接口，订阅的key的值发生变更后，在执行flush/flushSync方法后，callback方法会被回调。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                                                |  必填| 说明                                     |
| -------- | --------------------------------------------------- | ------ |---------------------------------------- |
| type     | string                                              |是| 事件类型，固定值'change'，表示数据变更。 |
| callback | Callback&lt;[StorageObserver](#storageobserver)&gt; | 是|回调对象实例。                           |

**示例：**

```js
let observer = function (key) {
    console.info("The key of " + key + " changed.");
}
storage.on('change', observer);
storage.putSync('startup', 'auto');
storage.flushSync();  // observer will be called.
```


### off('change')

off(type: 'change', callback: Callback&lt;StorageObserver&gt;): void

当不再进行订阅数据变更时，使用此接口取消订阅。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

**参数：**

| 参数名   | 类型                                                | 必填 |  说明                                 |
| -------- | --------------------------------------------------- | ------ |---------------------------------------- |
| type     | string                                              |是| 事件类型，固定值'change'，表示数据变更。 |
| callback | Callback&lt;[StorageObserver](#storageobserver)&gt; | 是|需要取消的回调对象实例。                 |

**示例：**

```js
let observer = function (key) {
    console.info("The key of " + key + " changed.");
}
storage.off('change', observer);
```


## StorageObserver

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

| 名称 | 类型 | 必填 | 说明             |
| ---- | -------- | ---- | ---------------- |
| key  | string   | 是   | 变更的数据内容。 |

## ValueType

type ValueType = number | string | boolean

用于表示允许的数据字段类型。

**系统能力：** SystemCapability.DistributedDataManager.Preferences.Core

| 类型    | 说明                 |
| ------- | -------------------- |
| number  | 表示值类型为数字。   |
| string  | 表示值类型为字符。   |
| boolean | 表示值类型为布尔值。 |
