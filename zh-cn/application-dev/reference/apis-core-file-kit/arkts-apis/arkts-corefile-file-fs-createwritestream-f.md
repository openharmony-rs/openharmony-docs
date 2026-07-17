# createWriteStream

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## createWriteStream

```TypeScript
declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream
```

以同步方法打开文件可写流。

**起始版本：** 12

<!--Device-unnamed-declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream--><!--Device-unnamed-declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件路径。 |
| options | [WriteStreamOptions](arkts-corefile-file-fs-writestreamoptions-i.md) | 否 | 支持如下选项：<br/>- start，number类型，表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。<br/>- mode，number 类型，创建文件可写流的[选项](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#openmode)，可选，默认以只写方式创建。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [WriteStream](arkts-corefile-file-fs-writestream-c.md) | 文件可写流。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

