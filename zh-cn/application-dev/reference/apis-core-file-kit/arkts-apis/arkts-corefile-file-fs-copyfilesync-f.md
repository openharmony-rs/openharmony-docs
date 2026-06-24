# copyFileSync

## copyFileSync

```TypeScript
declare function copyFileSync(src: string | number, dest: string | number, mode?: number): void
```

以同步方法复制文件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| src | string \| number | 是 | 待复制文件的路径或待复制文件的文件描述符。 |
| dest | string \| number | 是 | 目标文件路径或目标文件的文件描述符。 |
| mode | number | 否 | mode提供覆盖文件的选项，当前仅支持0，且默认为0。<br/>0：完全覆盖目标文件，未覆盖部分将被裁切掉。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900031](../../errorcode-universal.md#13900031-Function) | Function not implemented |
| [13900033](../../errorcode-universal.md#13900033-Too) | Too many symbolic links encountered |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900038](../../errorcode-universal.md#13900038-Value) | Value too large for defined data type |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [13900044](../../errorcode-universal.md#13900044-Network) | Network is unreachable&lt;br&gt;**适用版本：** 12+ |

