# fdatasyncSync

## fdatasyncSync

```TypeScript
function fdatasyncSync(fd: int): void
```

以同步方法实现文件内容的数据同步。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function fdatasyncSync(fd: int): void--><!--Device-fileIo-function fdatasyncSync(fd: int): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900027 | Read-only file system |

