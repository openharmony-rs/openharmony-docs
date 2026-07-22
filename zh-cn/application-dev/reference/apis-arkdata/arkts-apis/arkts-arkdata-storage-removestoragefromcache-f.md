# removeStorageFromCache

## removeStorageFromCache

```TypeScript
function removeStorageFromCache(path: string, callback: AsyncCallback<void>): void
```

从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。使用callback方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** removePreferencesFromCache

<!--Device-storage-function removeStorageFromCache(path: string, callback: AsyncCallback<void>): void--><!--Device-storage-function removeStorageFromCache(path: string, callback: AsyncCallback<void>): void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 应用程序内部数据存储路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 回调函数。 |


## removeStorageFromCache

```TypeScript
function removeStorageFromCache(path: string): Promise<void>
```

从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。使用Promise方式返回结果，此方法为异步方法。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** removePreferencesFromCache

<!--Device-storage-function removeStorageFromCache(path: string): Promise<void>--><!--Device-storage-function removeStorageFromCache(path: string): Promise<void>-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 应用程序内部数据存储路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise实例，用于异步获取结果。 |

