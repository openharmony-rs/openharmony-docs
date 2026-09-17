# dup

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## dup

```TypeScript
declare function dup(fd: number): File
```

Duplicates the file descriptor and returns the corresponding **File** object.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| fd | number | Yes | File descriptor. |

**Return value:**

| Type | Description |
| --- | --- |
| [File](arkts-corefile-file-fs-file-i.md) | File object opened. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900042 | Unknown error |
