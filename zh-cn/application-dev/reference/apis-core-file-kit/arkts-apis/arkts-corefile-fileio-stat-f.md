# stat

<a id="stat"></a>
## stat

```TypeScript
declare function stat(path: string): Promise<Stat>
```

获取文件信息，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:stat](arkts-corefile-file-fs-stat-f.md#stat-1)

<!--Device-unnamed-declare function stat(path: string): Promise<Stat>--><!--Device-unnamed-declare function stat(path: string): Promise<Stat>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待获取文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Stat&gt; | Promise对象。返回文件的具体信息。 |


<a id="stat-1"></a>
## stat

```TypeScript
declare function stat(path: string, callback: AsyncCallback<Stat>): void
```

获取文件信息，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:stat](arkts-corefile-file-fs-stat-f.md#stat-1)

<!--Device-unnamed-declare function stat(path: string, callback: AsyncCallback<Stat>): void--><!--Device-unnamed-declare function stat(path: string, callback: AsyncCallback<Stat>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待获取文件的应用沙箱路径。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Stat&gt; | 是 | 异步获取文件的信息之后的回调。 |

