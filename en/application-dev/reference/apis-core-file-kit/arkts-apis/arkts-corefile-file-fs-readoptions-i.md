# ReadOptions

Defines the options used in **read()**.

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## length

```TypeScript
length?: number
```

Length of the data to read, in bytes. This parameter is optional. The default value is the buffer length.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## offset

```TypeScript
offset?: number
```

Start position of the file to read, in bytes. This parameter is optional. By default, data is read from the current position.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO
