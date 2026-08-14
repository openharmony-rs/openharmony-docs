# ReadStream

文件可读流，需要先通过[fileIo.createReadStream](arkts-na-fileio-createreadstream-f.md#createReadStream)方法来构建一个ReadStream实例。ReadStream继承自数据流基类 [stream.Readable](../../apis-arkts/arkts-apis/arkts-arkts-stream-readable-c.md#Readable)。 **规格**：ReadStream读到的数据为解码后的字符串，其编码格式当前仅支持'utf-8'。

**继承/实现关系：** ReadStream extends [stream.Readable](../../apis-arkts/arkts-apis/arkts-arkts-stream-readable-c.md#Readable)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-class ReadStream--><!--Device-fileIo-class ReadStream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## close

```TypeScript
close(): void
```

关闭可读流。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ReadStream-close(): void--><!--Device-ReadStream-close(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

## constructor

```TypeScript
constructor()
```

The ReadStream constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ReadStream-constructor()--><!--Device-ReadStream-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## seek

```TypeScript
seek(offset: long, whence?: WhenceType): long
```

调整可读流偏移指针位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ReadStream-seek(offset: long, whence?: WhenceType): long--><!--Device-ReadStream-seek(offset: long, whence?: WhenceType): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | long | 是 | 相对偏移位置，单位为Byte。 |
| whence | [WhenceType](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-whencetype-e.md) | 否 | = WhenceType.SEEK_SET] - Where to start the offset. The default value is SEEK_SET, &lt;br&gt;which indicates the beginning of the file. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 当前可读流偏移指针位置（相对于文件头的偏移量，单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error |
| 13900026 | Illegal seek |
| 13900042 | Unknown error |

## bytesRead

```TypeScript
readonly bytesRead: long
```

可读流已经读取的字节数。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ReadStream-readonly bytesRead: long--><!--Device-ReadStream-readonly bytesRead: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## path

```TypeScript
readonly path: string
```

当前可读流对应的文件路径。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-ReadStream-readonly path: string--><!--Device-ReadStream-readonly path: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

