# WriteStreamOptions

Defines the options used in **createWriteStream()**.

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## mode

```TypeScript
mode?: number
```

[Option](../../../reference/apis-core-file-kit/js-apis-file-fs.md#openmode) for creating the writeable stream. You must specify one of the following options.

- **OpenMode.READ_ONLY(0o0)**: read-only, which is the default value.  
- **OpenMode.WRITE_ONLY(0o1)**: write-only.  
- **OpenMode.READ_WRITE(0o2)**: read/write.

You can also specify the following options, separated by a bitwise OR operator (|). By default, no additional options are given.

- **OpenMode.CREATE(0o100)**: If the file does not exist, create it.  
- **OpenMode.TRUNC(0o1000)**: If the file exists and is opened in write mode, truncate the file length to 0.  
- **OpenMode.APPEND(0o2000)**: Open the file in append mode. New data will be added to the end of the file.  
- **OpenMode.NONBLOCK(0o4000)**: If **path** points to a named pipe (also known as a FIFO), block special file, or  
character special file, perform non-blocking operations on the opened file and in subsequent I/Os.  
- **OpenMode.DIR(0o200000)**: If **path** does not point to a directory, throw an exception. The write permission  
is not allowed.  
- **OpenMode.NOFOLLOW(0o400000)**: If **path** points to a symbolic link, throw an exception.  
- **OpenMode.SYNC(0o4010000)**: Open the file in synchronous I/O mode.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO

## start

```TypeScript
start?: number
```

Start position to write the data, in bytes. This parameter is optional. By default, data is written from the current position.

**Type:** number

**Since:** 12

**System capability:** SystemCapability.FileManagement.File.FileIO
