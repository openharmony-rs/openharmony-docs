# close

## close

```TypeScript
function close(file: int | File): Promise<void>
```

关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function close(file: int | File): Promise<void>--><!--Device-fileIo-function close(file: int | File): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | int \| [File](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-file-i.md) | 是 | 已打开的File对象或已打开的文件描述符fd。关闭后File对象或文件描述符fd不可再用于读写等操作，继续使用可能导致错误或操作失败。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象，无返回结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


## close

```TypeScript
function close(file: int | File, callback: AsyncCallback<void>): void
```

关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function close(file: int | File, callback: AsyncCallback<void>): void--><!--Device-fileIo-function close(file: int | File, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | int \| [File](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-file-i.md) | 是 | 已打开的File对象或已打开的文件描述符fd。关闭后File对象或文件描述符fd不可再用于读写等操作，继续使用可能导致错误或操作失败。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;void&gt; | 是 | 回调函数。当异步关闭文件或目录成功，err为undefined，否则为错误对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

