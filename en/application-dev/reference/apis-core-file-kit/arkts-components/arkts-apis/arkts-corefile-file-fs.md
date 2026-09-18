# @ohos.file.fs(File Management)

FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [fileIo](arkts-corefile-fileio-n.md) | FileIO |

### Functions

| Name | Description |
| --- | --- |
| [access](arkts-corefile-file-fs-access-f.md) | Checks whether the file or directory exists or has the operation permission. This API uses a promise to return the result. |
| [access](arkts-corefile-file-fs-access-f.md) | Checks whether a file or directory exists. This API uses an asynchronous callback to return the result. |
| [access](arkts-corefile-file-fs-access-f.md) | Checks whether the file or directory is stored locally or has the operation permission. This API uses a promise to return the result. |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md) | Checks whether a file or directory exists or has the operation permission. This API returns the result synchronously. |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md) | Checks whether a file or directory is stored locally or has the operation permission. This API returns the result synchronously. |
| [close](arkts-corefile-file-fs-close-f.md) | Closes a file or directory. This API uses a promise to return the result. |
| [close](arkts-corefile-file-fs-close-f.md) | Closes a file or directory. This API uses an asynchronous callback to return the result. |
| [closeSync](arkts-corefile-file-fs-closesync-f.md) | Closes a file or directory. This API returns the result synchronously. |
| [connectDfs](arkts-corefile-file-fs-connectdfs-f.md) | Triggers connection. If the peer device is abnormal, [onStatus](arkts-corefile-file-fs-dfslisteners-i.md#onstatus) in **DfsListeners** will be called to notify the application. |
| [copy](arkts-corefile-file-fs-copy-f.md) | Copies a file or directory. This API uses a promise to return the result. |
| [copy](arkts-corefile-file-fs-copy-f.md) | Copies a file or directory. This API uses an asynchronous callback to return the result. |
| [copy](arkts-corefile-file-fs-copy-f.md) | Copies a file or directory. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md) | Copies the source directory to the destination path. This API uses a promise to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md) | Copies the source directory to the destination directory. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md) | Copies the source directory to the destination path. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md) | Copies the source directory to the destination directory. You can set the copy mode. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md) | Copies the source directory to the destination path. You can set the copy mode. This API uses an asynchronous callback to return the result. |
| [copyDirSync](arkts-corefile-file-fs-copydirsync-f.md) | Copies the source directory to the destination path. This API returns the result synchronously. |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md) | Copies a file. This API uses a promise to return the result. |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md) | Copies a file. This API overwrites the file with the same name in the destination directory and truncates the part that is not overwritten. This API uses an asynchronous callback to return the result. |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md) | Copies a file with the specified mode. This API uses an asynchronous callback to return the result. |
| [copyFileSync](arkts-corefile-file-fs-copyfilesync-f.md) | Copies a file. This API returns the result synchronously. |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md) | Creates a **RandomAccessFile** instance based on the specified file path or file object. This API uses a promise to return the result. |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md) | Creates a **RandomAccessFile** object in read-only mode based on a file path or file object. This API uses an asynchronous callback to return the result. |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md) | Creates a **RandomAccessFile** instance based on a file path or file object. This API uses an asynchronous callback to return the result. |
| [createRandomAccessFileSync](arkts-corefile-file-fs-createrandomaccessfilesync-f.md) | Creates a **RandomAccessFile** instance based on a file path or file object. |
| [createReadStream](arkts-corefile-file-fs-createreadstream-f.md) | Creates a readable stream. This API returns the result synchronously. |
| [createStream](arkts-corefile-file-fs-createstream-f.md) | Creates a stream based on a file path. This API uses a promise to return the result. To close the stream, use **close()** of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [createStream](arkts-corefile-file-fs-createstream-f.md) | Creates a stream based on a file path. This API uses an asynchronous callback to return the result. To close the stream, use **close()** of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [createStreamSync](arkts-corefile-file-fs-createstreamsync-f.md) | Creates a stream based on a file path. This API returns the result synchronously. To close the stream, use **close()** of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [createWatcher](arkts-corefile-file-fs-createwatcher-f.md) | Creates a **Watcher** object to listen for file or directory changes. |
| [createWriteStream](arkts-corefile-file-fs-createwritestream-f.md) | Creates a writeable stream. This API returns the result synchronously. |
| [disconnectDfs](arkts-corefile-file-fs-disconnectdfs-f.md) | Triggers disconnection. |
| [dup](arkts-corefile-file-fs-dup-f.md) | Duplicates the file descriptor and returns the corresponding **File** object. |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md) | Synchronizes the data of a file. This API uses a promise to return the result. |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md) | Synchronizes the data of a file. This API uses an asynchronous callback to return the result. |
| [fdatasyncSync](arkts-corefile-file-fs-fdatasyncsync-f.md) | Synchronizes the data of a file. This API returns the result synchronously. |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md) | Opens a stream based on an FD. This API uses a promise to return the result. To close the stream, use **close()** of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md) | Opens a stream based on an FD. This API uses an asynchronous callback to return the result. To close the stream, use **close()** of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [fdopenStreamSync](arkts-corefile-file-fs-fdopenstreamsync-f.md) | Opens a stream based on an FD. This API returns the result synchronously. To close the stream, use **close()** of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [fsync](arkts-corefile-file-fs-fsync-f.md) | Synchronizes the cached data of a file to storage. This API uses a promise to return the result. |
| [fsync](arkts-corefile-file-fs-fsync-f.md) | Synchronizes the cached data of a file to storage. This API uses an asynchronous callback to return the result. |
| [fsyncSync](arkts-corefile-file-fs-fsyncsync-f.md) | Synchronizes the cached data of a file to storage. This API returns the result synchronously. |
| [getxattr](arkts-corefile-file-fs-getxattr-f.md) | Obtains an extended attribute of a file or directory. This API uses a promise to return the result. |
| [getxattrSync](arkts-corefile-file-fs-getxattrsync-f.md) | Obtains an extended attribute of a file or directory. This API returns the result synchronously. |
| [listFile](arkts-corefile-file-fs-listfile-f.md) | Lists the names of all files and directories in the current path. Filtering is supported. This API uses a promise to return the result. |
| [listFile](arkts-corefile-file-fs-listfile-f.md) | Lists the names of all files and directories in the current path. Filtering is supported. This API uses an asynchronous callback to return the result. |
| [listFile](arkts-corefile-file-fs-listfile-f.md) | Lists the names of all files and directories in the current path. Filtering is supported. This API uses an asynchronous callback to return the result. |
| [listFileExt](arkts-corefile-file-fs-listfileext-f.md) | Lists all file names in a directory. This API uses a promise to return the result. This API supports recursive listing of all file names and custom file name filtering. The returned result starts with a slash (/) and contains the subdirectory. |
| [listFileExtSync](arkts-corefile-file-fs-listfileextsync-f.md) | Lists all file names in a directory. This API returns the result synchronously. This API supports recursive listing of all file names and custom file name filtering. The returned result starts with a slash (/) and contains the subdirectory. |
| [listFileSync](arkts-corefile-file-fs-listfilesync-f.md) | Lists the names of all files and directories in the current directory. This API returns the result synchronously. Filtering is supported. |
| [lseek](arkts-corefile-file-fs-lseek-f.md) | Adjusts the position of the file offset pointer. |
| [lstat](arkts-corefile-file-fs-lstat-f.md) | Obtains information about a symbolic link that is used to refer to a file or directory. This API uses a promise to return the result. |
| [lstat](arkts-corefile-file-fs-lstat-f.md) | Obtains information about a symbolic link that is used to refer to a file or directory. This API uses an asynchronous callback to return the result. |
| [lstatSync](arkts-corefile-file-fs-lstatsync-f.md) | Obtains information about a symbolic link that is used to refer to a file or directory. This API returns the result synchronously. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md) | Creates a directory. This API uses a promise to return the result. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md) | Creates a directory. This API uses a promise to return the result. The value **true** means to create a directory recursively. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md) | Creates a directory. This API uses an asynchronous callback to return the result. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md) | Creates a directory. This API uses an asynchronous callback to return the result. The value **true** means to create a directory recursively. |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md) | Creates a directory. This API returns the result synchronously. |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md) | Creates a directory. This API returns the result synchronously. The value **true** means to create a directory recursively. |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md) | Creates a temporary directory. This API uses a promise to return the result. |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md) | Creates a temporary directory. This API uses an asynchronous callback to return the result. |
| [mkdtempSync](arkts-corefile-file-fs-mkdtempsync-f.md) | Creates a temporary directory. This API returns the result synchronously. |
| [mmap](arkts-corefile-file-fs-mmap-f.md) | Creates a file mapping object based on a file descriptor or file object, using promise asynchronous callback. Maps file contents to memory for efficient read and write access to files. Note: In the read/write mode (MappingMode.READ_WRITE), if the mapping range exceeds the raw file size, the file size will be automatically expanded. |
| [mmapSync](arkts-corefile-file-fs-mmapsync-f.md) | Creates a file mapping object based on a file descriptor or file object by using the synchronization method. Maps file contents to memory for efficient read and write access to files. Note: In the read/write mode (MappingMode.READ_WRITE), if the mapping range exceeds the raw file size, the file size will be automatically expanded. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md) | Moves the source directory to the destination directory. This API uses a promise to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md) | Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md) | Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md) | Moves the source directory to the destination directory. You can set the move mode. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md) | Moves the source directory to the destination directory. You can set the move mode. This API uses an asynchronous callback to return the result. |
| [moveDirSync](arkts-corefile-file-fs-movedirsync-f.md) | Moves the source directory to the destination directory. This API returns the result synchronously. |
| [moveFile](arkts-corefile-file-fs-movefile-f.md) | Moves a file. This API uses a promise to return the result. |
| [moveFile](arkts-corefile-file-fs-movefile-f.md) | Moves a file and forcibly overwrites the file with the same name in the destination directory. This API uses an asynchronous callback to return the result. |
| [moveFile](arkts-corefile-file-fs-movefile-f.md) | Moves a file with the specified mode. This API uses an asynchronous callback to return the result. |
| [moveFileSync](arkts-corefile-file-fs-movefilesync-f.md) | Moves a file. This API returns the result synchronously. |
| [open](arkts-corefile-file-fs-open-f.md) | Opens a file or directory. This API uses a promise to return the result. This API supports the use of a URI. |
| [open](arkts-corefile-file-fs-open-f.md) | Opens a file or directory. This API uses an asynchronous callback to return the result. This API supports the use of a URI. |
| [open](arkts-corefile-file-fs-open-f.md) | Opens a file or directory with the specified mode. This API uses an asynchronous callback to return the result. |
| [openSync](arkts-corefile-file-fs-opensync-f.md) | Opens a file or directory. This API returns the result synchronously. This API supports the use of a URI. |
| [read](arkts-corefile-file-fs-read-f.md) | Reads file data. This API uses a promise to return the result. |
| [read](arkts-corefile-file-fs-read-f.md) | Reads data from a file. This API uses an asynchronous callback to return the result. |
| [read](arkts-corefile-file-fs-read-f.md) | Reads data from a file. This API uses an asynchronous callback to return the result. |
| [readLines](arkts-corefile-file-fs-readlines-f.md) | Reads the text content of a file line by line. This API uses a promise to return the result. Only the files in UTF-8 format are supported. |
| [readLines](arkts-corefile-file-fs-readlines-f.md) | Reads a file text line by line. This API uses an asynchronous callback to return the result. Only the files in UTF-8 format are supported. |
| [readLines](arkts-corefile-file-fs-readlines-f.md) | Reads a file text line by line. This API uses an asynchronous callback to return the result. Only the files in UTF-8 format are supported. |
| [readLinesSync](arkts-corefile-file-fs-readlinessync-f.md) | Reads the text content of a file line by line. This API returns the result synchronously. |
| [readSync](arkts-corefile-file-fs-readsync-f.md) | Reads data from a file. This API returns the result synchronously. |
| [readText](arkts-corefile-file-fs-readtext-f.md) | Reads the text content of a file. This API uses a promise to return the result. |
| [readText](arkts-corefile-file-fs-readtext-f.md) | Reads the text content of a file. This API uses an asynchronous callback to return the result. |
| [readText](arkts-corefile-file-fs-readtext-f.md) | Reads the text content of a file. This API uses an asynchronous callback to return the result. |
| [readTextSync](arkts-corefile-file-fs-readtextsync-f.md) | Reads the text content of a file. This API returns the result synchronously. |
| [rename](arkts-corefile-file-fs-rename-f.md) | Renames a file or directory. This API uses a promise to return the result. |
| [rename](arkts-corefile-file-fs-rename-f.md) | Renames a file or directory. This API uses an asynchronous callback to return the result. |
| [renameSync](arkts-corefile-file-fs-renamesync-f.md) | Renames a file or directory. This API returns the result synchronously. |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md) | Removes a directory and all its subdirectories and files. This API uses a promise to return the result. |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md) | Removes a directory and all its subdirectories and files. This API uses an asynchronous callback to return the result. |
| [rmdirSync](arkts-corefile-file-fs-rmdirsync-f.md) | Removes a directory and all its subdirectories and files synchronously. |
| [setxattr](arkts-corefile-file-fs-setxattr-f.md) | Sets an extended attribute of a file or directory. This API uses a promise to return the result. |
| [setxattrSync](arkts-corefile-file-fs-setxattrsync-f.md) | Sets an extended attribute of a file or directory. |
| [stat](arkts-corefile-file-fs-stat-f.md) | Obtains detailed attribute information of a file or directory. This API uses a promise to return the result. |
| [stat](arkts-corefile-file-fs-stat-f.md) | Obtains detailed attribute information of a file or directory. This API uses an asynchronous callback to return the result. |
| [statSync](arkts-corefile-file-fs-statsync-f.md) | Obtains detailed attribute information of a file or directory. This API returns the result synchronously. |
| [symlink](arkts-corefile-file-fs-symlink-f.md) | Creates a symbolic link based on a file path. This API uses a promise to return the result. |
| [symlink](arkts-corefile-file-fs-symlink-f.md) | Creates a symbolic link based on the file path. This API uses an asynchronous callback to return the result. |
| [symlinkSync](arkts-corefile-file-fs-symlinksync-f.md) | Creates a symbolic link based on the file path. This API returns the result synchronously. |
| [truncate](arkts-corefile-file-fs-truncate-f.md) | Truncates a file. This API uses a promise to return the result. |
| [truncate](arkts-corefile-file-fs-truncate-f.md) | Truncates a file. This API uses an asynchronous callback to return the result. |
| [truncate](arkts-corefile-file-fs-truncate-f.md) | Truncates a file. This API uses an asynchronous callback to return the result. |
| [truncateSync](arkts-corefile-file-fs-truncatesync-f.md) | Truncates the file content. This API returns the result synchronously. |
| [unlink](arkts-corefile-file-fs-unlink-f.md) | Removes a file. This API uses a promise to return the result. |
| [unlink](arkts-corefile-file-fs-unlink-f.md) | Removes a file. This API uses an asynchronous callback to return the result. |
| [unlinkSync](arkts-corefile-file-fs-unlinksync-f.md) | Removes a file. This API returns the result synchronously. |
| [utimes](arkts-corefile-file-fs-utimes-f.md) | Changes the time when the file was last modified. |
| [write](arkts-corefile-file-fs-write-f.md) | Writes data into a file. This API uses a promise to return the result. |
| [write](arkts-corefile-file-fs-write-f.md) | Writes data to a file. This API uses an asynchronous callback to return the result. |
| [write](arkts-corefile-file-fs-write-f.md) | Writes data to a file. This API uses an asynchronous callback to return the result. |
| [writeSync](arkts-corefile-file-fs-writesync-f.md) | Writes data to a file. This API returns the result synchronously. |

### Classes

| Name | Description |
| --- | --- |
| [AtomicFile](arkts-corefile-file-fs-atomicfile-c.md) | AtomicFile is a class used to perform atomic read and write operations on files. |
| [ReadStream](arkts-corefile-file-fs-readstream-c.md) | Defines a readable stream. You need to use [fileIo.createReadStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatereadstream12) to create a **ReadStream** instance, which is inherited from [stream.Readable](../../apis-arkts/arkts-apis/arkts-arkts-stream-readableoptions-i.md). |
| [TaskSignal](arkts-corefile-file-fs-tasksignal-c.md) | Provides APIs for interrupting a copy task. |
| [WriteStream](arkts-corefile-file-fs-writestream-c.md) | Defines a writeable stream. You need to use [fileIo.createWriteStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatewritestream12) to create a **WriteStream** instance, which is inherited from [stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md). |

### Interfaces

| Name | Description |
| --- | --- |
| [ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md) | Defines conflicting file information used in **copyDir()** or **moveDir()**. |
| [CopyOptions](arkts-corefile-file-fs-copyoptions-i.md) | Defines the callback for listening for the copy progress. |
| [DfsListeners](arkts-corefile-file-fs-dfslisteners-i.md) | Provides APIs for observing events. listening for the distributed file system status. |
| [File](arkts-corefile-file-fs-file-i.md) | Represents a **File** object opened by **open()**. |
| [FileFilter](arkts-corefile-file-fs-filefilter-i.md) | Defines the file name filtering interface used by listFileExt(). |
| [FileMapping](arkts-corefile-file-fs-filemapping-i.md) | File mapping object. Before invoking the FileMapping method, you need to use the mmap() method (synchronous or asynchronous) to construct a FileMapping instance. |
| [Filter](arkts-corefile-file-fs-filter-i.md) | Defines the file filtering configuration used by **listFile()**. |
| [ListFileExtOptions](arkts-corefile-file-fs-listfileextoptions-i.md) | Defines the options used in listFileExt(). |
| [ListFileOptions](arkts-corefile-file-fs-listfileoptions-i.md) | Defines the options used in **listFile()**. |
| [Options](arkts-corefile-file-fs-options-i.md) | Defines the options used in **readLines()**. |
| [Progress](arkts-corefile-file-fs-progress-i.md) | Defines the copy progress information. |
| [RandomAccessFile](arkts-corefile-file-fs-randomaccessfile-i.md) | Provides APIs for randomly reading and writing a stream. Before invoking any API of **RandomAccessFile**, you need to use **createRandomAccessFile()** to create a **RandomAccessFile** instance synchronously or asynchronously. |
| [RandomAccessFileOptions](arkts-corefile-file-fs-randomaccessfileoptions-i.md) | Defines the options used in **createRandomAccessFile()**. |
| [ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md) | Provides a **ReaderIterator** object. Before calling APIs of **ReaderIterator**, you need to use **readLines()** to create a **ReaderIterator** instance. |
| [ReaderIteratorResult](arkts-corefile-file-fs-readeriteratorresult-i.md) | Represents the information obtained by the **ReaderIterator** object. |
| [ReadOptions](arkts-corefile-file-fs-readoptions-i.md) | Defines the options used in **read()**. |
| [ReadStreamOptions](arkts-corefile-file-fs-readstreamoptions-i.md) | Defines the options used in **createReadStream()**. |
| [ReadTextOptions](arkts-corefile-file-fs-readtextoptions-i.md) | Defines the options used in **readText()**. It inherits from [ReadOptions](arkts-corefile-file-fs-readoptions-i.md). |
| [Stat](arkts-corefile-file-fs-stat-i.md) | Represents detailed file information. Before calling any API of the **Stat()** class, use [stat()](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiostat) to create a **Stat** instance. |
| [Stream](arkts-corefile-file-fs-stream-i.md) | Provides API for stream operations. Before calling any API of **Stream**, you need to create a **Stream** instance by using [fileIo.createStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatestream) or [fileIo.fdopenStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiofdopenstream). |
| [Watcher](arkts-corefile-file-fs-watcher-i.md) | Provides APIs for observing the changes of files or directories. Before using the APIs of **Watcher**, call **createWatcher()** to create a **Watcher** object. |
| [WatchEvent](arkts-corefile-file-fs-watchevent-i.md) | Defines the event to observe. |
| [WatchEventListener](arkts-corefile-file-fs-watcheventlistener-i.md) | (event: WatchEvent): void |
| [WriteOptions](arkts-corefile-file-fs-writeoptions-i.md) | Defines the options used in **write()**. It inherits from [Options](arkts-corefile-file-fs-options-i.md). |
| [WriteStreamOptions](arkts-corefile-file-fs-writestreamoptions-i.md) | Defines the options used in **createWriteStream()**. |

### Enums

| Name | Description |
| --- | --- |
| [AccessFlagType](arkts-corefile-file-fs-accessflagtype-e.md) | Enumerates the locations of the file to verify. |
| [AccessModeType](arkts-corefile-file-fs-accessmodetype-e.md) | Enumerates the access modes to verify. If this parameter is left blank, the system checks whether the file exists. |
| [LocationType](arkts-corefile-file-fs-locationtype-e.md) | Enumerates the file locations. |
| [MappingMode](arkts-corefile-file-fs-mappingmode-e.md) | Enumerated type of the file memory mapping mode, which can be used by the mmap API. |
| [WhenceType](arkts-corefile-file-fs-whencetype-e.md) | Enumerates the types of the relative offset position used in **lseek()**. |

### Types

| Name | Description |
| --- | --- |
| [ProgressListener](arkts-corefile-progresslistener-t.md) | Listener used to observe the copy progress. |
