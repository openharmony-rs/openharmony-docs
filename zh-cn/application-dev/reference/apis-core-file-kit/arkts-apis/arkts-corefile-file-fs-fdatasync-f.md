# fdatasync

## fdatasync

```TypeScript
declare function fdatasync(fd: number): Promise<void>
```

实现文件内容数据同步，使用promise异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 已打开的文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


## fdatasync

```TypeScript
declare function fdatasync(fd: number, callback: AsyncCallback<void>): void
```

实现文件内容数据同步，使用callback异步回调。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 已打开的文件描述符。 |
| callback | AsyncCallback&lt;void&gt; | 是 | 异步将文件内容数据同步之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

