# utimes

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## utimes

```TypeScript
declare function utimes(path: string, mtime: number): void
```

更改文件上次修改该文件的时间。

**起始版本：** 11

<!--Device-unnamed-declare function utimes(path: string, mtime: number): void--><!--Device-unnamed-declare function utimes(path: string, mtime: number): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 文件的应用沙箱路径。 |
| mtime | number | 是 | 待更新的时间戳。自1970年1月1日起至目标时间的毫秒数。仅支持更改上次修改该文件的时间属性。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900020 | Invalid argument |
| 13900027 | Read-only file system |
| 13900042 | Unknown error |

