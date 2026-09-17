# WatchEvent

Defines the event to observe.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## cookie

```TypeScript
readonly cookie: number
```

Cookie bound with the event.

Currently, only the **IN_MOVED_FROM** and **IN_MOVED_TO** events are supported. The **IN_MOVED_FROM** and **IN_MOVED_TO** events of the same file have the same **cookie** value.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

## event

```TypeScript
readonly event: number
```

Events to observe. Multiple events can be separated by vertical bars (

**Type:** number

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

## fileName

```TypeScript
readonly fileName: string
```

Sandbox path of the file to observe. The sandbox path contains the file name.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO
