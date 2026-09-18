# OpenMode(File Management)

Mode Indicates the open flags.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## Summary

### Constants

| Name | Description |
| --- | --- |
| [READ_ONLY](arkts-corefile-openmode-con.md#read_only) | Open the file in read-only mode. |
| [WRITE_ONLY](arkts-corefile-openmode-con.md#write_only) | Open the file in write-only mode. |
| [READ_WRITE](arkts-corefile-openmode-con.md#read_write) | Open the file in read/write mode. |
| [CREATE](arkts-corefile-openmode-con.md#create) | Create a file if the specified file does not exist. |
| [TRUNC](arkts-corefile-openmode-con.md#trunc) | If the file exists and is opened in write-only or read/write mode, truncate the file length to 0. |
| [APPEND](arkts-corefile-openmode-con.md#append) | Open the file in append mode. New data will be written to the end of the file. |
| [NONBLOCK](arkts-corefile-openmode-con.md#nonblock) | If **path** points to a named pipe (FIFO), block special file, or character special file, perform non-blocking operations on the open file and in subsequent I/Os. |
| [DIR](arkts-corefile-openmode-con.md#dir) | If **path** does not point to a directory, throw an exception. |
| [NOFOLLOW](arkts-corefile-openmode-con.md#nofollow) | If **path** points to a symbolic link, throw an exception. |
| [SYNC](arkts-corefile-openmode-con.md#sync) | Open the file in synchronous I/O mode. |
| [UNCACHE](arkts-corefile-openmode-con.md#uncache) | UNCACHE IO. |
