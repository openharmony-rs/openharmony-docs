# fdatasync

## fdatasync

```TypeScript
declare function fdatasync(fd: number): Promise<void>
```

实现文件内容数据同步，使用Promise异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待同步文件的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |


## fdatasync

```TypeScript
declare function fdatasync(fd: number, callback: AsyncCallback<void>): void
```

实现文件内容数据同步，使用callback异步回调。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [fs:fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync-1)

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 待同步文件的文件描述符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步将文件内容数据同步之后的回调。 |

