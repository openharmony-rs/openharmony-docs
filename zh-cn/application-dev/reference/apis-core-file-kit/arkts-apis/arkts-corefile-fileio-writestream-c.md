# WriteStream

文件可写流，需要先通过[fileIo.createWriteStream]\_\_\_JSDOC\_LINK\_DESC\_USD\_0\_\_\_方法来构建一个WriteStream实例。WriteStream继承自数据流基类 [stream.Writable]\_\_\_JSDOC\_LINK\_DESC\_USD\_1\_\_\_。

**继承/实现关系：** WriteStream extends [stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md)

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-fileIo-class WriteStream extends stream.Writable--><!--Device-fileIo-class WriteStream extends stream.Writable-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## close

```TypeScript
close(): void
```

关闭可写流。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WriteStream-close(): void--><!--Device-WriteStream-close(): void-End-->

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

The WriteStream constructor.

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WriteStream-constructor()--><!--Device-WriteStream-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## seek

```TypeScript
seek(offset: long, whence?: WhenceType): long
```

调整可写流的偏移指针位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WriteStream-seek(offset: long, whence?: WhenceType): long--><!--Device-WriteStream-seek(offset: long, whence?: WhenceType): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | long | 是 | 相对偏移位置，单位为Byte。 |
| whence | \_\_\_MD\_LINK\_USD\_0\_\_\_ | 否 | = WhenceType.SEEK\_\_\_ESCAPED\_UNDERSCORE\_\_\_SET] - Where to start the offset. |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 当前可写流偏移指针位置（相对于文件头的偏移量，单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error |
| 13900020 | Invalid argument |
| 13900026 | Illegal seek |
| 13900042 | Unknown error |

## bytesWritten

```TypeScript
readonly bytesWritten: long
```

可写流已经写入的字节数。

**类型：** long

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WriteStream-readonly bytesWritten: long--><!--Device-WriteStream-readonly bytesWritten: long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## path

```TypeScript
readonly path: string
```

当前可写流对应的文件路径。

**类型：** string

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-WriteStream-readonly path: string--><!--Device-WriteStream-readonly path: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

