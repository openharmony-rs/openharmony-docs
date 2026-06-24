# readTextSync

## readTextSync

```TypeScript
declare function readTextSync(
  filePath: string,
  options?: ReadTextOptions
): string
```

以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| filePath | string | 是 | 文件的应用沙箱路径。 |
| options | ReadTextOptions | 否 | 支持如下选项：<br/>- offset，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读取。<br/>- length<br/>，number类型，表示期望读取数据，单位为Byte。可选，默认文件长度。<br/>- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认'utf-8'，仅支持'utf-8'<br/>。 [since 11] |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回读取文件的内容。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900001](../../errorcode-universal.md#13900001-Operation) | Operation not permitted |
| [13900004](../../errorcode-universal.md#13900004-Interrupted) | Interrupted system call |
| [13900005](../../errorcode-universal.md#13900005-IO) | I/O error |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900010](../../errorcode-universal.md#13900010-Try) | Try again |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900019](../../errorcode-universal.md#13900019-Is) | Is a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900024](../../errorcode-universal.md#13900024-File) | File too large |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900034](../../errorcode-universal.md#13900034-Operation) | Operation would block |
| [13900041](../../errorcode-universal.md#13900041-Quota) | Quota exceeded |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |
| [13900044](../../errorcode-universal.md#13900044-Network) | Network is unreachable&lt;br&gt;**适用版本：** 12+ |

