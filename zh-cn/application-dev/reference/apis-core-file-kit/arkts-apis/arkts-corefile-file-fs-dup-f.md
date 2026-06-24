# dup

## dup

```TypeScript
declare function dup(fd: number): File
```

复制文件描述符，并返回对应的File对象。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| File | 打开的File对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900014](../../errorcode-universal.md#13900014-Device) | Device or resource busy |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

