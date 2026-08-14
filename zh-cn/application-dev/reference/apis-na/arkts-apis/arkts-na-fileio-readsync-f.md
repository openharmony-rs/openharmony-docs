# readSync

## readSync

```TypeScript
function readSync(
  fd: int,
  buffer: ArrayBuffer,
  options?: ReadOptions
): long
```

以同步方法从文件读取数据，返回实际读取的字节数。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function readSync(  fd: int,  buffer: ArrayBuffer,  options?: ReadOptions): long--><!--Device-fileIo-function readSync(  fd: int,  buffer: ArrayBuffer,  options?: ReadOptions): long-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| buffer | ArrayBuffer | 是 | 用于保存读取到的文件数据的缓冲区。 |
| options | [ReadOptions](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-readoptions-i.md) | 否 | 支持如下选项：&lt;br/&gt;- offset，number类型，表示期望读取文件的位置，单位为Byte。可选，默认从当前位置开始读。&lt;br/&gt;- length， number类型，表示期望读取数据的长度，单位为Byte。可选，默认缓冲区长度。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| long | 返回实际读取的数据长度，单位为Byte。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900034 | Operation would block |
| 13900019 | Is a directory |
| 13900044 | Network is unreachable |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900042 | Unknown error |

