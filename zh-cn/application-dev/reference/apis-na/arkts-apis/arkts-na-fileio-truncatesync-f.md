# truncateSync

## 导入模块

```TypeScript
```

## truncateSync

```TypeScript
function truncateSync(file: string | int, len?: long): void
```

以同步方法截断文件内容，将文件大小调整为指定长度，超出部分的内容将被删除。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function truncateSync(file: string | int, len?: long): void--><!--Device-fileIo-function truncateSync(file: string | int, len?: long): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| int | 是 | 文件的应用沙箱路径或已打开的文件描述符fd。 |
| len | long | 否 | 文件截断后的长度，单位为Byte。默认为0。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900020 | Invalid argument |
| 13900023 | Text file busy |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900030 | File name too long |
| 13900024 | File too large |
| 13900027 | Read-only file system |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900001 | Operation not permitted |
| 13900033 | Too many symbolic links encountered |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |

