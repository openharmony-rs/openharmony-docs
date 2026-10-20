# readLines

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## readLines

```TypeScript
declare function readLines(filePath: string, options?: Options): Promise<ReaderIterator>
```

Reads a file text line by line. Only the files in UTF-8 format are supported. This API uses a promise to return the result.

**Since:** 11

<!--Device-unnamed-declare function readLines(filePath: string, options?: Options): Promise<ReaderIterator>--><!--Device-unnamed-declare function readLines(filePath: string, options?: Options): Promise<ReaderIterator>-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Application sandbox path of the file. |
| options | [Options](arkts-corefile-file-fs-options-i.md) | No | Options. The options are as follows:<br>           - <b>encoding</b> (string): format of the string to be encoded. The default value is <b>'utf-8'</b>,   which is the only value supported. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | Promise used to return the <b>ReaderIterator</b> object. |

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


## readLines

```TypeScript
declare function readLines(filePath: string, callback: AsyncCallback<ReaderIterator>): void
```

Reads a file text line by line. Only the files in UTF-8 format are supported. This API uses an asynchronous callback to return the result.

**Since:** 11

<!--Device-unnamed-declare function readLines(filePath: string, callback: AsyncCallback<ReaderIterator>): void--><!--Device-unnamed-declare function readLines(filePath: string, callback: AsyncCallback<ReaderIterator>): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Application sandbox path of the file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | Yes | Callback used to return the <b>ReaderIterator</b> object. |

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


## readLines

```TypeScript
declare function readLines(filePath: string, options: Options, callback: AsyncCallback<ReaderIterator>): void
```

Reads a file text line by line. Read options can be configured. Only the files in UTF-8 format are supported. This API uses an asynchronous callback to return the result.

**Since:** 11

<!--Device-unnamed-declare function readLines(filePath: string, options: Options, callback: AsyncCallback<ReaderIterator>): void--><!--Device-unnamed-declare function readLines(filePath: string, options: Options, callback: AsyncCallback<ReaderIterator>): void-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| filePath | string | Yes | Application sandbox path of the file. |
| options | [Options](arkts-corefile-file-fs-options-i.md) | Yes | Options. The options are as follows:<br>           - <b>encoding</b> (string): format of the string to be encoded. The default value is <b>'utf-8'</b>,   which is the only value supported. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md)&gt; | Yes | Callback used to return the <b>ReaderIterator</b> object. |

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
