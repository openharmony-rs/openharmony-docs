# writeSync

## writeSync

```TypeScript
function writeSync(
  fd: int,
  buffer: ArrayBuffer | string,
  options?: WriteOptions
): long
```

以同步方法将数据写入文件，返回实际写入的字节数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function writeSync(  fd: int,  buffer: ArrayBuffer | string,  options?: WriteOptions): long--><!--Device-fileIo-function writeSync(  fd: int,  buffer: ArrayBuffer | string,  options?: WriteOptions): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer \| string | 是 | 待写入文件的数据，可来自缓冲区或字符串。 |
| options | [WriteOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-writeoptions-i.md) | 否 | 支持如下选项：&lt;br/&gt;- offset，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。&lt;br/&gt;- length， number类型，表示期望写入数据的长度，单位为Byte。可选，默认缓冲区长度。&lt;br/&gt;- encoding，string类型，当数据是string类型时有效，表示数据的编码方式，默认 'utf-8'。 当前仅支持 'utf-8'。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回实际写入的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900034 | Operation would block |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900010 | Try again |
| 13900042 | Unknown error |

