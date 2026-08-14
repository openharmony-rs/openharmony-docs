# lseek

## lseek

```TypeScript
function lseek(fd: int, offset: long, whence?: WhenceType): long
```

调整文件偏移指针位置。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function lseek(fd: int, offset: long, whence?: WhenceType): long--><!--Device-fileIo-function lseek(fd: int, offset: long, whence?: WhenceType): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 文件描述符。 |
| offset | long | 是 | 相对偏移位置，单位为Byte。 |
| whence | [WhenceType](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-whencetype-e.md) | 否 | 偏移指针相对位置类型。不指定则默认为文件起始位置处。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 当前文件偏移指针位置（相对于文件头的偏移量，单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900038 | Value too large for defined data type |
| 13900008 | Bad file descriptor |
| 13900026 | Illegal seek |
| 13900042 | Unknown error |

