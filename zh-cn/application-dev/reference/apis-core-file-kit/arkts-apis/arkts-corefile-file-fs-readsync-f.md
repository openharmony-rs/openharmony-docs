# readSync

## readSync

```TypeScript
declare function readSync(
  fd: number,
  buffer: ArrayBuffer,
  options?: ReadOptions
): number
```

以同步方法从文件读取数据。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 已打开的文件描述符。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| options | ReadOptions | 否 | 支持如下选项：<br/>- offset，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。<br/>- length，<br/>number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度。 [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [13900044](../../errorcode-universal.md#13900044-Network) | Network is unreachable&lt;br&gt;**适用版本：** 12+ |

