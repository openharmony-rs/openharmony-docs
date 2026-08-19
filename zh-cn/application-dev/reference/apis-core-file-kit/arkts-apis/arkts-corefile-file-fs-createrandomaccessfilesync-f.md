# createRandomAccessFileSync

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## createRandomAccessFileSync

```TypeScript
declare function createRandomAccessFileSync(file: string | File, mode?: number,
  options?: RandomAccessFileOptions): RandomAccessFile
```

基于文件路径或文件对象创建RandomAccessFile对象。

**起始版本：** 10

<!--Device-unnamed-declare function createRandomAccessFileSync(file: string | File, mode?: number,  options?: RandomAccessFileOptions): RandomAccessFile--><!--Device-unnamed-declare function createRandomAccessFileSync(file: string | File, mode?: number,  options?: RandomAccessFileOptions): RandomAccessFile-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | string \| [File](arkts-corefile-file-fs-file-i.md) | 是 | 文件的应用沙箱路径或已打开的File对象。 |
| mode | number | 否 | 创建文件RandomAccessFile对象的 选项，仅当传入文件沙箱路径时生效，必须指定如下选项中的一个，默认以只读方式创建：&lt;br /&gt;- OpenMode.READ_ONLY(0o0)：只读创建。<br/>- OpenMode.WRITE_ONLY(0o1)：只写创建。<br/>- OpenMode.READ_WRITE(0o2)：读写创建。<br/>给 定如下功能选项，以按位或的方式追加，默认不给定任何额外选项：<br/>- OpenMode.CREATE(0o100)：若文件不存在，则创建文件。<br/>- OpenMode.TRUNC(0o1000)：如果 RandomAccessFile对象存在且对应文件具有写权限，则将其长度裁剪为零。<br/>- OpenMode.APPEND(0o2000)：以追加方式打开，后续写将追加到RandomAccessFile对象末尾。<br/> - OpenMode.NONBLOCK(0o4000)：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。<br/>- OpenMode.DIR(0o200000)：如果path不指向 目录，则出错。不允许附加写权限。<br/>- OpenMode.NOFOLLOW(0o400000)：如果path指向符号链接，则出错。<br/>- OpenMode.SYNC(0o4010000)：以同步IO的方式创建 RandomAccessFile对象。 |
| options | [RandomAccessFileOptions](../../apis-na/arkts-apis/arkts-na-file-fs-randomaccessfileoptions-i.md) | 否 | 支持如下选项：<br/>- start，number类型，表示文件的起始偏移位置，单位为Byte。可选，默认文件当前位置。<br/>- end，number类型，表示文件的结束偏移位置，单位为Byte。可选，默认文件末尾。<br/>此选项仅对[getreadstream](arkts-corefile-file-fs-randomaccessfile-i.md#getreadstream)及 [getwritestream](arkts-corefile-file-fs-randomaccessfile-i.md#getwritestream)获取的文件流对象生效。<br>**起始版本：** 12 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [RandomAccessFile](arkts-corefile-file-fs-randomaccessfile-i.md) | 返回RandomAccessFile对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900038 | Value too large for defined data type |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900044 | Network is unreachable<br>**适用版本：** 12+ |
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

