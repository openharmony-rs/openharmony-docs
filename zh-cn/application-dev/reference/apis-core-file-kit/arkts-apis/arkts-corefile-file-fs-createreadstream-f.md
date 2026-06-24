# createReadStream

## createReadStream

```TypeScript
declare function createReadStream(path: string, options?: ReadStreamOptions): ReadStream
```

以同步方法打开文件可读流。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件路径。 |
| options | ReadStreamOptions | 否 | 支持如下选项：<br/>- start，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。<br/>- end，<br/>number类型，表示期望读取结束的位置，单位为Byte。可选，默认文件末尾。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| ReadStream | 文件可读流。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-Parameter) | Parameter error |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900017](../../errorcode-universal.md#13900017-No) | No such device |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [13900044](../../errorcode-universal.md#13900044-Network) | Network is unreachable |

