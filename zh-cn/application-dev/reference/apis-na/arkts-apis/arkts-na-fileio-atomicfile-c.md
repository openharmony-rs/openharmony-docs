# AtomicFile

AtomicFile是一个用于对文件进行原子读写等操作的类。 在写操作时，通过写入临时文件，并在写入成功后将其重命名到原始文件位置来确保写入文件的完整性；而在写入失败时删除临时文件，不修改原始文件内容。 使用者可以自行调用finishWrite或failWrite来完成文件内容的写入或回滚。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-export class AtomicFile--><!--Device-fileIo-export class AtomicFile-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
```

## constructor

```TypeScript
constructor(path: string)
```

对于给定路径的文件创建一个AtomicFile类。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-constructor(path: string)--><!--Device-AtomicFile-constructor(path: string)-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的沙箱路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) |  |

## delete

```TypeScript
delete(): void
```

删除AtomicFile类，会删除原始文件和临时文件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-delete(): void--><!--Device-AtomicFile-delete(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 |  |
| 13900002 |  |
| 13900012 |  |
| 13900042 |  |
| 13900027 |  |

## failWrite

```TypeScript
failWrite(): void
```

文件写入失败后调用，将执行文件回滚操作。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-failWrite(): void--><!--Device-AtomicFile-failWrite(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900042 |  |

## finishWrite

```TypeScript
finishWrite(): void
```

在完成对startWrite返回流的写入操作时调用，表示文件写入成功。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-finishWrite(): void--><!--Device-AtomicFile-finishWrite(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900042 |  |

## getBaseFile

```TypeScript
getBaseFile(): File
```

通过AtomicFile对象获取文件对象。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-getBaseFile(): File--><!--Device-AtomicFile-getBaseFile(): File-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [File](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-file-i.md) | File object opened. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 |  |
| 13900002 |  |
| 13900012 |  |
| 13900042 |  |

## openRead

```TypeScript
openRead(): ReadStream
```

创建一个读文件流。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-openRead(): ReadStream--><!--Device-AtomicFile-openRead(): ReadStream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [ReadStream](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readstream-c.md) | ReadStream instance obtained. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 |  |
| 13900002 |  |
| 13900012 |  |
| 13900042 |  |

## readFully

```TypeScript
readFully(): ArrayBuffer
```

读取文件全部内容。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-readFully(): ArrayBuffer--><!--Device-AtomicFile-readFully(): ArrayBuffer-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ArrayBuffer | Full content of a file. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 |  |
| 13900042 |  |

## startWrite

```TypeScript
startWrite(): WriteStream
```

对文件开始新的写入操作。将返回一个WriteStream，用于在其中写入新的文件数据。 当文件不存在时新建文件。 在写入文件完成后，写入成功需要调用finishWrite()，写入失败需要调用failWrite()。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-AtomicFile-startWrite(): WriteStream--><!--Device-AtomicFile-startWrite(): WriteStream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WriteStream](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-writestream-c.md) | Returns the file write stream. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 |  |
| 13900002 |  |
| 13900012 |  |
| 13900042 |  |
| 13900027 |  |

