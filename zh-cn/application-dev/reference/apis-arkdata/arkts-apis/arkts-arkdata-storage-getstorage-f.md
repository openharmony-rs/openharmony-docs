# getStorage

## 导入模块

```TypeScript
```

## getStorage

```TypeScript
function getStorage(path: string, callback: AsyncCallback<Storage>): void
```

读取指定文件，将数据加载到Storage实例，用于数据操作，使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getPreferences

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 应用程序内部数据存储路径。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Storage&gt; | 是 | 回调函数。 |

**示例**

```TypeScript
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


## getStorage

```TypeScript
function getStorage(path: string): Promise<Storage>
```

读取指定文件，将数据加载到Storage实例，用于数据操作，使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getPreferences

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 应用程序内部数据存储路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise & lt;Storage & gt; | Promise实例，用于异步获取结果。 |

**示例**

```TypeScript
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
