# listFileExt

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## listFileExt

```TypeScript
declare function listFileExt(
  path: string,
  options?: ListFileExtOptions
): Promise<string[]>
```

Lists all file names in a directory. This API uses a promise to return the result. This API supports recursive listing of all file names and custom file name filtering. The returned result starts with a slash (/) and contains the subdirectory.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path of the directory. |
| options | [ListFileExtOptions](arkts-corefile-file-fs-listfileextoptions-i.md) | No | Options for filtering files. The files are not filtered by default. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string[]&gt; | Promise used to return the file names listed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900011 | Out of memory |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
