# moveFileSync

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## moveFileSync

```TypeScript
declare function moveFileSync(src: string, dest: string, mode?: number): void
```

Moves a file. This API returns the result synchronously.

> **NOTE:** 
> 
> This API is not supported in a distributed directory.

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 26.0.1.

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Application sandbox path of the file to move. |
| dest | string | Yes | Application sandbox path of the destination file. |
| mode | number | No | Move mode.<br> The value **0** means to overwrite the file with the same name in the destination directory; the value **1** means to throw an exception. The default value is **0**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900016 | Cross-device link |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900028 | Too many links |
| 13900032 | Directory not empty |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
