# stat

## stat

```TypeScript
declare function stat(path: string): Promise<Stat>
```

获取文件信息，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:stat](arkts-corefile-file-fs-stat-f.md#stat-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待获取文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Stat&gt; | Promise对象。返回文件的具体信息。 |


## stat

```TypeScript
declare function stat(path: string, callback: AsyncCallback<Stat>): void
```

获取文件信息，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:stat](arkts-corefile-file-fs-stat-f.md#stat-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待获取文件的应用沙箱路径。 |
| callback | AsyncCallback&lt;Stat&gt; | 是 | 异步获取文件的信息之后的回调。 |

