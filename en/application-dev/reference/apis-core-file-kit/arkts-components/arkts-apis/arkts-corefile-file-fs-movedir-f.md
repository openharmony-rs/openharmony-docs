# moveDir

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, mode?: number): Promise<void>
```

Moves the source directory to the destination directory. This API uses a promise to return the result.

> **NOTE:** 
> 
> This API is not supported in a distributed directory.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Application sandbox path of the source directory. |
| dest | string | Yes | Application sandbox path of the destination directory. |
| mode | number | No | Move mode. The default value is **0**.<br>- **0**: Throw an exception if a directory conflict occurs.<br> An exception will be thrown if the destination directory contains a non-empty directory with the same name as the source directory.<br>- **1**: Throw an exception if a file conflict occurs.<br> An exception will be thrown if the destination directory contains a directory with the same name as the source directory, and a file with the same name exists in the conflict directory. All the non-conflicting files in the source directory will be moved to the destination directory, and the non-conflicting files in the destination directory will be retained. The data attribute in the error returned provides information about the conflicting files in the Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt; format.<br>- **2**: Forcibly overwrite the conflicting files in the destination directory.<br> When the destination directory contains a directory with the same name as the source directory, the files with the same names in the destination directory are overwritten forcibly; the files without conflicts in the destination directory are retained.<br>- **3**: Forcibly overwrite the conflicting directory.<br> The source directory is moved to the destination directory, and the content of the moved directory is the same as that of the source directory. If the destination directory contains a directory with the same name as the source directory, all original files in the directory will be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

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


<a id="movedir-1"></a>

## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, callback: AsyncCallback<void>): void
```

Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Application sandbox path of the source directory. |
| dest | string | Yes | Application sandbox path of the destination directory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

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


<a id="movedir-2"></a>

## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result.

An exception will be thrown if a directory conflict occurs, that is, the destination directory contains a directory with the same name as the source directory.

> **NOTE:** 
> 
> This API is not supported in a distributed directory.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Application sandbox path of the source directory. |
| dest | string | Yes | Application sandbox path of the destination directory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void, Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900015 | File exists |


<a id="movedir-3"></a>

## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback<void>): void
```

Moves the source directory to the destination directory. You can set the move mode. This API uses an asynchronous callback to return the result.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Application sandbox path of the source directory. |
| dest | string | Yes | Application sandbox path of the destination directory. |
| mode | number | Yes | Move mode. The default value is 0.<br>0: Throw an exception if a directory conflict occurs. <br>An exception will be thrown if the destination directory contains a non-empty directory with <br>the same name as the source directory. <br>1: Throw an exception if a file conflict occurs. <br>An exception will be thrown if the destination directory contains a directory with <br>the same name as the source directory, and a file with the same name exists in the conflict directory. <br>All the non-conflicting files in the source directory will be moved to the destination directory, <br>and the non-conflicting files in the destination directory will be retained. <br>The data attribute in the error returned provides information about the conflicting files in <br>the Array&lt;ConflictFiles&gt; format. <br>2: Forcibly overwrite the conflicting files in the destination directory. <br>When the destination directory contains a directory with the same name as the source directory, <br>the files with the same names in the destination directory are overwritten forcibly; <br>the files without conflicts in the destination directory are retained. <br>3: Forcibly overwrite the conflicting directory. <br>The source directory is moved to the destination directory, and the content of the moved directory is the <br>same as that of the source directory. If the destination directory contains a directory with the same name <br>as the source directory, all original files in the directory will be deleted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Return the callback function. |

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


<a id="movedir-4"></a>

## moveDir

```TypeScript
declare function moveDir(src: string, dest: string, mode: number, callback: AsyncCallback<void, Array<ConflictFiles>>): void
```

Moves the source directory to the destination directory. You can set the move mode. This API uses an asynchronous callback to return the result.

> **NOTE:** 
> 
> This API is not supported in a distributed directory.

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| src | string | Yes | Application sandbox path of the source directory. |
| dest | string | Yes | Application sandbox path of the destination directory. |
| mode | number | Yes | Move mode. The default value is **0**.<br>- **0**: Throw an exception if a directory conflict occurs.<br> An exception will be thrown if the destination directory contains a directory with the same name as the source directory.<br>- **1**: Throw an exception if a file conflict occurs.<br> An exception will be thrown if the destination directory contains a directory with the same name as the source directory, and a file with the same name exists in the conflict directory. All the non-conflicting files in the source directory will be moved to the destination directory, and the non-conflicting files in the destination directory will be retained. The data attribute in the error returned provides information about the conflicting files in the Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt; format.<br>- **2**: Forcibly overwrite the conflicting files in the destination directory.<br> When the destination directory contains a directory with the same name as the source directory, the files with the same names in the destination directory are overwritten forcibly; the files without conflicts in the destination directory are retained.<br>- **3**: Forcibly overwrite the conflicting directory.<br> The source directory is moved to the destination directory, and the content of the moved directory is the same as that of the source directory. If the destination directory contains a directory with the same name as the source directory, all original files in the directory will be deleted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void, Array&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900015 | File exists |
