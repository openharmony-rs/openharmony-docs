# FileFilter

Defines the file name filtering interface used by listFileExt().

**Since:** 26.0.0

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## filter

```TypeScript
filter(name: string): boolean
```

Filtering function, which determines whether the specified file name should be included in the file list.

Note: This function is frequently invoked. Avoid time-consuming operations, such as file I/O and network requests.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| name | string | Yes | Name of the file to be filtered. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns true if the file should be included, false otherwise. |
