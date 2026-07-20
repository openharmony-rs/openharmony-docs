# fdatasyncSync

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="fdatasyncsync"></a>
## fdatasyncSync

```TypeScript
declare function fdatasyncSync(fd: number): void
```

以同步方法实现文件内容的数据同步。

**起始版本：** 9

<!--Device-unnamed-declare function fdatasyncSync(fd: number): void--><!--Device-unnamed-declare function fdatasyncSync(fd: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 已打开的文件描述符。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

