# closeSync

## closeSync

```TypeScript
function closeSync(file: int | File): void
```

以同步方法关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-fileIo-function closeSync(file: int | File): void--><!--Device-fileIo-function closeSync(file: int | File): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | int \| [File](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-file-i.md) | 是 | 已打开的File对象或已打开的文件描述符fd。关闭后File对象或文件描述符fd不可再用于读写等操作，继续使用可能导致错误或操作失败。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

