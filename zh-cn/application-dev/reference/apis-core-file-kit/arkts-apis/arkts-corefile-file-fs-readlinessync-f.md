# readLinesSync

## readLinesSync

```TypeScript
declare function readLinesSync(filePath: string, options?: Options): ReaderIterator
```

以同步方式逐行读取文件的文本内容。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | Options | 否 | 可选项。支持以下选项：<br/>- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'，仅支持'utf-8'<br/>。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ReaderIterator | 返回文件读取迭代器。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900027](../../errorcode-universal.md#13900027-Readonly) | Read-only file system |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [13900044](../../errorcode-universal.md#13900044-Network) | Network is unreachable&lt;br&gt;**适用版本：** 12+ |

