# CopyOptions

```TypeScript
interface CopyOptions
```

Defines the callback for listening for the copy progress.

**Since:** 11

<!--Device-unnamed-interface CopyOptions--><!--Device-unnamed-interface CopyOptions-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## progressListener

```TypeScript
progressListener?: ProgressListener
```

Listener used to observe the copy progress.

**Since:** 11

<!--Device-CopyOptions-progressListener?: ProgressListener--><!--Device-CopyOptions-progressListener?: ProgressListener-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## copySignal

```TypeScript
copySignal?: TaskSignal
```

Signal used to cancel a copy task.

**Type:** [TaskSignal](arkts-corefile-file-fs-tasksignal-c.md)

**Since:** 12

<!--Device-CopyOptions-copySignal?: TaskSignal--><!--Device-CopyOptions-copySignal?: TaskSignal-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO
