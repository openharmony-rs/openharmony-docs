# ConflictFiles

```TypeScript
export interface ConflictFiles
```

Defines conflicting file information used in **copyDir()** or **moveDir()**.

**Since:** 10

<!--Device-unnamed-export interface ConflictFiles--><!--Device-unnamed-export interface ConflictFiles-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## destFile

```TypeScript
destFile: string
```

Path of the destination file.

**Type:** string

**Since:** 10

<!--Device-ConflictFiles-destFile: string--><!--Device-ConflictFiles-destFile: string-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## srcFile

```TypeScript
srcFile: string
```

Path of the source file.

**Type:** string

**Since:** 10

<!--Device-ConflictFiles-srcFile: string--><!--Device-ConflictFiles-srcFile: string-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO
