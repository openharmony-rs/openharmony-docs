# CopyOptions

拷贝进度回调监听

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## progressListener

```TypeScript
progressListener?: ProgressListener
```

拷贝进度监听。

**起始版本：** 11

**系统能力：** SystemCapability.FileManagement.File.FileIO

## copySignal

```TypeScript
copySignal?: TaskSignal
```

取消拷贝信号。

**类型：** [TaskSignal](arkts-corefile-file-fs-tasksignal-c.md)

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO
