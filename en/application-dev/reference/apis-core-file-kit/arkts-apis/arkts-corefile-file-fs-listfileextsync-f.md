# listFileExtSync

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## listFileExtSync

```TypeScript
declare function listFileExtSync(
  path: string,
  options?: ListFileExtOptions
): string[]
```

Lists all file names in a directory. This API returns the result synchronously. This API supports recursive listing of all file names and custom file name filtering. The returned result starts with a slash (/) and contains the subdirectory.

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
| string[] | List of the file names obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900011 | Out of memory |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
