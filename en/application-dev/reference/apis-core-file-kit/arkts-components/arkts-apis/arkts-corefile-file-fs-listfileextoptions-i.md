# ListFileExtOptions

Defines the options used in listFileExt().

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## fileFilter

```TypeScript
fileFilter?: FileFilter
```

File name filtering interface. This parameter is optional. Filtering rules can be defined based on file names.

**Type:** [FileFilter](arkts-corefile-file-fs-filefilter-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

## listNum

```TypeScript
listNum?: number
```

Number of file names to list. This parameter is optional. The default value is 0, which means to list all files. The value should be an integer.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

## recursion

```TypeScript
recursion?: boolean
```

Whether to list all files in the subdirectories recursively. This parameter is optional. The default value is false. If recursion is false, the names of files and directories that meet the filtering requirements in the current directory are returned. If recursion is true, relative paths (starting with"/") of all files that meet the specified conditions in the current directory are returned.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO
