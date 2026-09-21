# lstat

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## lstat

```TypeScript
declare function lstat(path: string): Promise<Stat>
```

Obtains information about a symbolic link that is used to refer to a file or directory. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path or URI of the file.<br>**Note:**  URIs can be passed since API version 22. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[Stat](arkts-corefile-file-fs-stat-i.md)&gt; | Promise used to return the symbolic link information obtained. For details, see **Stat**. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |


<a id="lstat-1"></a>

## lstat

```TypeScript
declare function lstat(path: string, callback: AsyncCallback<Stat>): void
```

Obtains information about a symbolic link that is used to refer to a file or directory. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| path | string | Yes | Application sandbox path or URI of the file.<br>**Note:**  URIs can be passed since API version 22. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[Stat](arkts-corefile-file-fs-stat-i.md)&gt; | Yes | Callback used to return the symbolic link information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900018 | Not a directory |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |
