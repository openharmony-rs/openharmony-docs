# createWriteStream

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## createWriteStream

```TypeScript
declare function createWriteStream(path: string, options?: WriteStreamOptions): WriteStream
```

Creates a writeable stream. This API returns the result synchronously.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Path of the file. |
| options | [WriteStreamOptions](arkts-corefile-file-fs-writestreamoptions-i.md) | No | The options are as follows:<br>- **start** (number): start position to write the data, in bytes. This parameter is optional. By default, data is written from the current position.<br>- **mode** (number): [mode](../../../reference/apis-core-file-kit/js-apis-file-fs.md#openmode) for creating the writeable stream. This parameter is optional. The default value is the write-only mode. |

**Return value:**

| Type | Description |
| --- | --- |
| [WriteStream](arkts-corefile-file-fs-writestream-c.md) | **WriteStream** instance obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
