# unlink

## unlink

```TypeScript
declare function unlink(path: string): Promise<void>
```

删除文件，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:unlink](arkts-corefile-file-fs-unlink-f.md#unlink-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待删除文件的应用沙箱路径。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


## unlink

```TypeScript
declare function unlink(path: string, callback: AsyncCallback<void>): void
```

删除文件，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [fs:unlink](arkts-corefile-file-fs-unlink-f.md#unlink-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 待删除文件的应用沙箱路径。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步删除文件之后的回调。 |

