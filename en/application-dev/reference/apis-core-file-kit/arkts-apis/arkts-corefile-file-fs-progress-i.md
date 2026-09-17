# Progress

Defines the copy progress information.

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## processedSize

```TypeScript
readonly processedSize: number
```

Size of the copied data, in bytes.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

## totalSize

```TypeScript
readonly totalSize: number
```

Total size of the data to be copied, in bytes.

**Type:** number

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO
