# open

## 导入模块

```TypeScript
```

## open

```TypeScript
function open(path: string, mode?: int): Promise<File>
```

打开文件或目录，支持使用URI打开文件。使用Promise异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function open(path: string, mode?: int): Promise<File>--><!--Device-fileIo-function open(path: string, mode?: int): Promise<File>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径或文件URI。 |
| mode | int | 否 | 打开文件或目录的[OpenMode](arkts-na-fileio-openmode-n.md)，必须指定如下选项中的一个，默认以只读方式打开：<br/> - OpenMode.READ_ONLY(0o0)：只读打开。<br/>- OpenMode.WRITE_ONLY(0o1)：只写打开。<br/> - OpenMode.READ_WRITE(0o2)：读写打开。<br/>可以追加以下功能选项，以按位或的方式组合，默认情况下不追加任何额外选项。<br/> - OpenMode.CREATE(0o100)：如果文件不存在，则创建文件。<br/> - OpenMode.TRUNC(0o1000)：如果文件存在且文件具有写权限，则将其长度裁剪为零。<br/> - OpenMode.APPEND(0o2000)：以追加方式打开，后续写将追加到文件末尾。<br/> - OpenMode.NONBLOCK(0o4000)：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续 IO 进行非阻塞操作。<br/> - OpenMode.DIR(0o200000)：如果path不指向目录，则出错。不允许附加写权限。<br/> - OpenMode.NOFOLLOW(0o400000)：如果path指向符号链接，则出错。<br/> - OpenMode.SYNC(0o4010000)：以同步IO方式打开文件。<br/> - OpenMode.UNCACHE(0o10000000000)：读写文件不进行页缓存，从API版本26.0.0开始支持此选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[File](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-file-i.md)&gt; | Promise对象，返回File对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900044 | Network is unreachable |
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
| 13900011 | Out of memory |


## open

```TypeScript
function open(path: string, callback: AsyncCallback<File>): void
```

打开文件或目录，支持使用URI打开文件。使用callback异步回调。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function open(path: string, callback: AsyncCallback<File>): void--><!--Device-fileIo-function open(path: string, callback: AsyncCallback<File>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径或URI。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[File](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-file-i.md)&gt; | 是 | 回调函数，返回File对象。 |

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
| 13900011 | Out of memory |


## open

```TypeScript
function open(path: string, mode: int, callback: AsyncCallback<File>): void
```

打开文件或目录，可设置打开文件的选项。使用callback异步回调。 支持使用URI打开文件。

**起始版本：** 23

**ArkTS模式：** 同时支持ArkTS-Dyn、ArkTS-Sta，起始版本为23。

<!--Device-fileIo-function open(path: string, mode: int, callback: AsyncCallback<File>): void--><!--Device-fileIo-function open(path: string, mode: int, callback: AsyncCallback<File>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径或URI。 |
| mode | int | 是 | 打开文件或目录的[OpenMode](arkts-na-fileio-openmode-n.md)，必须指定如下选项中的一个，默认以只读方式打开：<br/> - OpenMode.READ_ONLY(0o0)：只读打开。<br/>- OpenMode.WRITE_ONLY(0o1)：只写打开。<br/> - OpenMode.READ_WRITE(0o2)：读写打开。<br/>可以追加以下功能选项，以按位或的方式组合，默认情况下不追加任何额外选项。<br/> - OpenMode.CREATE(0o100)：如果文件不存在，则创建文件。<br/> - OpenMode.TRUNC(0o1000)：如果文件存在且文件具有写权限，则将其长度裁剪为零。<br/> - OpenMode.APPEND(0o2000)：以追加方式打开，后续写将追加到文件末尾。<br/> - OpenMode.NONBLOCK(0o4000)：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续 IO 进行非阻塞操作。<br/> - OpenMode.DIR(0o200000)：如果path不指向目录，则出错。不允许附加写权限。<br/> - OpenMode.NOFOLLOW(0o400000)：如果path指向符号链接，则出错。<br/> - OpenMode.SYNC(0o4010000)：以同步IO方式打开文件。<br/> - OpenMode.UNCACHE(0o10000000000)：读写文件不进行页缓存，从API版本26.0.0开始支持此选项。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;[File](../../apis-core-file-kit/arkts-apis/arkts-corefile-file-fs-file-i.md)&gt; | 是 | 回调函数，返回File对象。 |

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
| 13900011 | Out of memory |

