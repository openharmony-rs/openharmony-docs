# mmap

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## mmap

```TypeScript
declare function mmap(file: number | File, mode: MappingMode, offset: number, size: number): Promise<FileMapping>
```

Creates a file mapping object based on a file descriptor or file object for efficient read and write access to files. This API uses a promise to return the result.

> **NOTE:** 
> 
> 1. Memory mapping can be performed only for regular files. Non-regular files, such as pipeline, socket, and device files, are not supported. You can use [statSync()](arkts-corefile-file-fs-statsync-f.md) to obtain file attributes and then call [Stat.isFile()](arkts-corefile-file-fs-stat-i.md#isfile) to check whether the file is a regular file.
> 2. If the mapping range exceeds the raw file size and the write permission is granted for the file, the mapping file size will be automatically expanded.
> 3. For files from external storage or network files, the establishment of mappings and access to the mapped memory are not guaranteed due to differences in the underlying file system. This may cause the application to terminate unexpectedly. You are advised to use other file access APIs such as [read](arkts-corefile-file-fs-read-f.md), [write](arkts-corefile-file-fs-write-f.md), or [Stream](arkts-corefile-file-fs-stream-i.md) in this scenario.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-unnamed-declare function mmap(file: number | File, mode: MappingMode, offset: number, size: number): Promise<FileMapping>--><!--Device-unnamed-declare function mmap(file: number | File, mode: MappingMode, offset: number, size: number): Promise<FileMapping>-End-->

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| file | number &#124; [File](arkts-corefile-file-fs-file-i.md) | Yes | File object or open file descriptor fd that has been opened. |
| mode | [MappingMode](arkts-corefile-file-fs-mappingmode-e.md) | Yes | Option to create a file memory-mapped object. You must specify one of the following options: <br> <b>MappingMode.READ_ONLY(0)</b>: read-only mode. The file mapping area is not writable. An exception is thrown when the file mapping area is modified. <br> <b>MappingMode.READ_WRITE(1)</b>: read/write mode. The modification is written to the file mapping area and then synchronized to the file by the operating system (non-real-time). <b>MappingMode.PRIVATE(2)</b>: private mode. It is a copy-on-write mapping mechanism. Modifications to the mapping area are visible only to the current process and do not affect the raw file. |
| offset | number | Yes | Start location of the file mapping area, in bytes. |
| size | number | Yes | Size of the file mapping area, in bytes. The value must be greater than 0 and not greater than <b>INT32_MAX</b>. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FileMapping](arkts-corefile-file-fs-filemapping-i.md)&gt; | Promise used to return the file mapping object. Initial state of the returned object: The value of <b>position</b> is <b>0</b>, and the values of <b>limit</b> and <b>capacity</b> are equal to the value of <b>size</b>. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900038 | Value too large for defined data type |
| 13900050 | Internal resource error |
| 13900056 | Mmap does not support mapping this file |
