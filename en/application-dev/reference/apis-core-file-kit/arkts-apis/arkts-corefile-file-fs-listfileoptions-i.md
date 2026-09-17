# ListFileOptions

Defines the options used in **listFile()**.

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## filter

```TypeScript
filter?: Filter
```

File filtering configuration. This parameter is optional. It specifies the file filtering conditions.

**Type:** [Filter](arkts-corefile-file-fs-filter-i.md)

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## listNum

```TypeScript
listNum?: number
```

Number of file names to list. This parameter is optional. The default value is **0**, which means to list all files.

**Type:** number

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## recursion

```TypeScript
recursion?: boolean
```

Whether to list all files in the subdirectories recursively. This parameter is optional. The default value is **false**. If **recursion** is **false**, the names of files and directories that meet the filtering requirements in the current directory are returned. If **recursion** is **true**, relative paths (starting with"/") of all files that meet the specified conditions in the current directory are returned.

**Type:** boolean

**Since:** 11

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO
