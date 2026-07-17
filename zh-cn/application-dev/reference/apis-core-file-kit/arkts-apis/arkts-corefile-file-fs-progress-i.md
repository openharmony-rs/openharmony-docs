# Progress

拷贝进度回调数据

**起始版本：** 11

<!--Device-unnamed-interface Progress--><!--Device-unnamed-interface Progress-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## processedSize

```TypeScript
readonly processedSize: number
```

已拷贝的数据大小，单位为Byte。

**类型：** number

**起始版本：** 11

<!--Device-Progress-readonly processedSize: number--><!--Device-Progress-readonly processedSize: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## totalSize

```TypeScript
readonly totalSize: number
```

待拷贝的数据总大小，单位为Byte。

**类型：** number

**起始版本：** 11

<!--Device-Progress-readonly totalSize: number--><!--Device-Progress-readonly totalSize: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

