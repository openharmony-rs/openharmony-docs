# getStorageSync

<a id="getstoragesync"></a>
## getStorageSync

```TypeScript
function getStorageSync(path: string): Storage
```

读取指定文件，将数据加载到Storage实例，用于数据操作。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** getPreferences

<!--Device-storage-function getStorageSync(path: string): Storage--><!--Device-storage-function getStorageSync(path: string): Storage-End-->

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 应用程序内部数据存储路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Storage](arkts-arkdata-storage-storage-c.md) | 获取到要操作的Storage实例，用于进行数据存储操作。 |

