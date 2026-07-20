# open

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="open"></a>
## open

```TypeScript
declare function open(path: string, mode?: number): Promise<File>
```

打开文件或目录，使用promise异步回调。支持使用URI打开文件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function open(path: string, mode?: number): Promise<File>--><!--Device-unnamed-declare function open(path: string, mode?: number): Promise<File>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径或文件URI。 |
| mode | number | 否 | 打开文件或目录的[选项](docroot://reference/apis-core-file-kit/js-apis-file-fs.md#openmode)，必须指定如下选项中的一个，默认以只读方式打开：<br/>- OpenMode.READ_ONLY(0o0)：只读打开。<br/>- OpenMode.WRITE_ONLY(0o1)：只写打开。<br/>- OpenMode.READ_WRITE(0o2)：读写打开。<br/>给定如下功能选项，以按位或的方式追加，默认不给定任何额外选项：<br/>- OpenMode.CREATE(0o100)：若文件不存在，则创建文件。<br/>- OpenMode.TRUNC(0o1000)：如果文件存在且文件具有写权限，则将其长度裁剪为零。<br/>- OpenMode.APPEND(0o2000)：以追加方式打开，后续写将追加到文件末尾。<br/>- OpenMode.NONBLOCK(0o4000)：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。<br/>- OpenMode.DIR(0o200000)：如果path不指向目录，则出错。不允许附加写权限。<br/>-OpenMode.NOFOLLOW(0o400000)：如果path指向符号链接，则出错。<br/>- OpenMode.SYNC(0o4010000)：以同步IO的方式打开文件。<br/>- OpenMode.UNCACHE(0o10000000000)：读写文件不进行页缓存，从API版本26.0.0开始支持此选项。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;File&gt; | Promise对象。返回File对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900044 | Network is unreachable<br>**适用版本：** 12+ |


<a id="open-1"></a>
## open

```TypeScript
declare function open(path: string, callback: AsyncCallback<File>): void
```

打开文件或目录，使用callback异步回调。支持使用URI打开文件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function open(path: string, callback: AsyncCallback<File>): void--><!--Device-unnamed-declare function open(path: string, callback: AsyncCallback<File>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径或URI。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;File&gt; | 是 | 异步打开文件之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |


<a id="open-2"></a>
## open

```TypeScript
declare function open(path: string, mode: number, callback: AsyncCallback<File>): void
```

打开文件或目录，可设置打开文件的选项。使用callback异步回调。

支持使用URI打开文件。

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-unnamed-declare function open(path: string, mode: number, callback: AsyncCallback<File>): void--><!--Device-unnamed-declare function open(path: string, mode: number, callback: AsyncCallback<File>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件或目录的应用沙箱路径或URI。 |
| mode | number | 是 | 打开文件或目录的[选项](docroot://reference/apis-core-file-kit/js-apis-file-fs.md#openmode)，必须指定如下选项中的一个，默认以只读方式打开：<br/>- OpenMode.READ_ONLY(0o0)：只读打开。<br/>- OpenMode.WRITE_ONLY(0o1)：只写打开。<br/>- OpenMode.READ_WRITE(0o2)：读写打开。<br/>给定如下功能选项，以按位或的方式追加，默认不给定任何额外选项：<br/>- OpenMode.CREATE(0o100)：若文件不存在，则创建文件。<br/>- OpenMode.TRUNC(0o1000)：如果文件存在且文件具有写权限，则将其长度裁剪为零。<br/>- OpenMode.APPEND(0o2000)：以追加方式打开，后续写将追加到文件末尾。<br/>- OpenMode.NONBLOCK(0o4000)：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。<br/>- OpenMode.DIR(0o200000)：如果path不指向目录，则出错。不允许附加写权限。<br/>-OpenMode.NOFOLLOW(0o400000)：如果path指向符号链接，则出错。<br/>- OpenMode.SYNC(0o4010000)：以同步IO的方式打开文件。<br/>- OpenMode.UNCACHE(0o10000000000)：读写文件不进行页缓存，从API版本26.0.0开始支持此选项。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;File&gt; | 是 | 异步打开文件之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

