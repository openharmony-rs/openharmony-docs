# ReaderIteratorResult

Represents the information obtained by the **ReaderIterator** object.

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## done

```TypeScript
done: boolean
```

Whether the iteration is complete. The value **true** means the iteration is complete; the value **false** means the opposite.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

## value

```TypeScript
value: string
```

File text content read line by line.

**Type:** string

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO
