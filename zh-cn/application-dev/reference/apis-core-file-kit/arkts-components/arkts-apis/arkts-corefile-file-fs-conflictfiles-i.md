# ConflictFiles

冲突文件信息，支持copyDir及moveDir接口使用。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## destFile

```TypeScript
destFile: string
```

目标冲突文件路径。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

## srcFile

```TypeScript
srcFile: string
```

源冲突文件路径。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO
