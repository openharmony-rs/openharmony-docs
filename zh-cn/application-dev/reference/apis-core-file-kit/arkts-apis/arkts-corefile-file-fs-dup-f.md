# dup

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## dup

```TypeScript
declare function dup(fd: number): File
```

复制文件描述符，并返回对应的File对象。

**起始版本：** 10

<!--Device-unnamed-declare function dup(fd: number): File--><!--Device-unnamed-declare function dup(fd: number): File-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [File](arkts-corefile-file-fs-file-i.md) | 打开的File对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900020 | Invalid argument |
| 13900005 | I/O error |
| 13900022 | Too many open files |
| 13900014 | Device or resource busy |
| 13900008 | Bad file descriptor |
| 13900042 | Unknown error |

