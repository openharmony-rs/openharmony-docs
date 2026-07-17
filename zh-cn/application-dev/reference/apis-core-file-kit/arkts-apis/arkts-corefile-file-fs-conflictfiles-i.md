# ConflictFiles

冲突文件信息，支持copyDir及moveDir接口使用。

**起始版本：** 10

<!--Device-unnamed-export interface ConflictFiles--><!--Device-unnamed-export interface ConflictFiles-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## destFile

```TypeScript
destFile: string
```

目标冲突文件路径。

**类型：** string

**起始版本：** 10

<!--Device-ConflictFiles-destFile: string--><!--Device-ConflictFiles-destFile: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## srcFile

```TypeScript
srcFile: string
```

源冲突文件路径。

**类型：** string

**起始版本：** 10

<!--Device-ConflictFiles-srcFile: string--><!--Device-ConflictFiles-srcFile: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

