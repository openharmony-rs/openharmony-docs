# fsyncSync

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## fsyncSync

```TypeScript
declare function fsyncSync(fd: number): void
```

Synchronizes the cached data of a file to storage. This API returns the result synchronously.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | FD of the file. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
