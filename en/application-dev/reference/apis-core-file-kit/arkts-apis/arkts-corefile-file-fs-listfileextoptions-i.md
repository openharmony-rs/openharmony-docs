# ListFileExtOptions

```TypeScript
export interface ListFileExtOptions
```

Defines the options used in <b>listFileExt</b>.

**Since:** 26.0.0

<!--Device-unnamed-export interface ListFileExtOptions--><!--Device-unnamed-export interface ListFileExtOptions-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## fileFilter

```TypeScript
fileFilter?: FileFilter
```

File name filtering rule. The default value is empty, indicating that no filtering is performed.

**Type:** [FileFilter](arkts-corefile-file-fs-filefilter-i.md)

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ListFileExtOptions-fileFilter?: FileFilter--><!--Device-ListFileExtOptions-fileFilter?: FileFilter-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## listNum

```TypeScript
listNum?: number
```

Number of file names to be listed. The default value is <b>0</b>, indicating that all files are listed.

**Type:** number

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ListFileExtOptions-listNum?: number--><!--Device-ListFileExtOptions-listNum?: number-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

## recursion

```TypeScript
recursion?: boolean
```

Whether to list all files in subfolders recursively. The default value is <b>false</b>. <br><b>false</b>: The names of files and directories that meet the filtering requirements in the current directory are returned. <br><b>true</b>: Relative paths (starting with /) of all files that meet the filtering requirements in the directory are returned.

**Type:** boolean

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-ListFileExtOptions-recursion?: boolean--><!--Device-ListFileExtOptions-recursion?: boolean-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO
