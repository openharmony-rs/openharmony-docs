# truncate

## truncate

```TypeScript
function truncate(file: string | int, len?: long): Promise<void>
```

截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function truncate(file: string | int, len?: long): Promise<void>--><!--Device-fileIo-function truncate(file: string | int, len?: long): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| int | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | long | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |


## truncate

```TypeScript
function truncate(file: string | int, callback: AsyncCallback<void>): void
```

截断文件，删除文件内容。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function truncate(file: string | int, callback: AsyncCallback<void>): void--><!--Device-fileIo-function truncate(file: string | int, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| int | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当截断文件成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |


## truncate

```TypeScript
function truncate(file: string | int, len: long, callback: AsyncCallback<void>): void
```

截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function truncate(file: string | int, len: long, callback: AsyncCallback<void>): void--><!--Device-fileIo-function truncate(file: string | int, len: long, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| int | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | long | 是 | 文件截断后的长度，单位为Byte。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当截断文件成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |

