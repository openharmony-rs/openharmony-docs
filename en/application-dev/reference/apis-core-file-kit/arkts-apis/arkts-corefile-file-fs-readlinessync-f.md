# readLinesSync

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## readLinesSync

```TypeScript
declare function readLinesSync(filePath: string, options?: Options): ReaderIterator
```

Reads a file text line by line synchronously. Only the files in UTF-8 format are supported.

**Since:** 11

<!--Device-unnamed-declare function readLinesSync(filePath: string, options?: Options): ReaderIterator--><!--Device-unnamed-declare function readLinesSync(filePath: string, options?: Options): ReaderIterator-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Application sandbox path of the file. |
| options | [Options](arkts-corefile-file-fs-options-i.md) | No | Options. The options are as follows:<br>           - <b>encoding</b> (string): format of the string to be encoded. The default value is <b>'utf-8'</b>,   which is the only value supported. |

**Return value:**

| Type | Description |
| --- | --- |
| [ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md) | <b>ReaderIterator</b> object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 13900044 | Network is unreachable<br>**Applicable version:** 12 and later |
