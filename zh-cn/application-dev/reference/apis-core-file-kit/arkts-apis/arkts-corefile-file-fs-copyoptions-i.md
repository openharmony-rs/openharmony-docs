# CopyOptions

拷贝进度回调监听

**起始版本：** 11

<!--Device-unnamed-interface CopyOptions--><!--Device-unnamed-interface CopyOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
import { fileIo } from '@kit.CoreFileKit'
import { ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, TaskSignal } from '@kit.CoreFileKit';
```

## copySignal

```TypeScript
copySignal?: TaskSignal
```

取消拷贝信号。

**类型：** [TaskSignal](../../apis-na/arkts-apis/arkts-na-tasksignal-t.md)

**起始版本：** 12

<!--Device-CopyOptions-copySignal?: TaskSignal--><!--Device-CopyOptions-copySignal?: TaskSignal-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## progressListener

```TypeScript
progressListener?: ProgressListener
```

拷贝进度监听。

**类型：** [ProgressListener](arkts-corefile-progresslistener-t.md)

**起始版本：** 11

<!--Device-CopyOptions-progressListener?: ProgressListener--><!--Device-CopyOptions-progressListener?: ProgressListener-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

