# removeStorageFromCacheSync

<a id="removestoragefromcachesync"></a>
## removeStorageFromCacheSync

```TypeScript
function removeStorageFromCacheSync(path: string): void
```

从内存中移除指定文件对应的Storage单实例。移除Storage单实例时，应用不允许再使用该实例进行数据操作，否则会出现数据一致性问题。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** removePreferencesFromCache

<!--Device-storage-function removeStorageFromCacheSync(path: string): void--><!--Device-storage-function removeStorageFromCacheSync(path: string): void-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 应用程序内部数据存储路径。 |

