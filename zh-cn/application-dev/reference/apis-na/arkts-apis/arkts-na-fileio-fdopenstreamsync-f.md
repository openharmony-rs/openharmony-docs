# fdopenStreamSync

## 导入模块

```TypeScript
```

## fdopenStreamSync

```TypeScript
function fdopenStreamSync(fd: int, mode: string): Stream
```

以同步方法基于文件描述符打开文件流。需要配合[Stream](arkts-na-fileio-stream-i.md)中的close()函数关闭文件流。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function fdopenStreamSync(fd: int, mode: string): Stream--><!--Device-fileIo-function fdopenStreamSync(fd: int, mode: string): Stream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | int | 是 | 已打开的文件描述符fd。 |
| mode | string | 是 |  r：打开只读文件，该文件必须存在。<br/>- r+：打开可读写的文件，该文件必须存在。<br/> - w：打开只写文件，若文件存在则文件长度清0，即该文件内容会消失。若文件不存在则建立该文件。<br/> - w+：打开可读写文件，若文件存在则文件长度清0，即该文件内容会消失。若文件不存在则建立该文件。<br/> - a：以附加的方式打开只写文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾，即文件原先的内容会被保留。<br/> - a+：以附加方式打开可读写的文件。若文件不存在，则会建立该文件，如果文件存在，写入的数据会被加到文件尾后，即文件原先的内容会被保留。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Stream](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-stream-i.md) | 返回文件流的结果。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |

