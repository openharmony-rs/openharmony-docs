# @ohos.file.fs(File Management)

This module is the core module of Core File Kit. It provides APIs for basic file operations, such as creating, opening, reading, writing, copying, moving, deleting, and querying files and directories in the application sandbox.

This module provides multiple file access modes. You can select a mode based on your specific requirements:

Based on the file descriptor (FD): You can obtain a <b>File</b> object using the <b>open</b> API and then read data from the file or write data to the file using the <b>read</b> or <b>write</b> API. This mode is suitable for common file read/write scenarios. Based on the stream: You can create a <b>Stream</b> object using <b>createStream</b> or <b>fdopenStream</b>, or create a <b>ReadStream</b> or <b>WriteStream</b> object using <b>createReadStream</b> or <b>createWriteStream</b>. This mode is suitable for scenarios such as stream data processing or block-based read/write of large files. Based on <b>RandomAccessFile</b>: You can create a <b>RandomAccessFile</b> object using <b>createRandomAccessFile</b>. This mode supports independent offset pointers and random read/write operations, which is suitable for scenarios where frequent jumps between read/write positions are required. In addition, this module provides other capabilities such as <b>Watcher</b>, <b>FileMapping</b>, and <b>AtomicFile</b>.

> **How to Use**

Before using the APIs provided by this module to perform operations on a file or directory, obtain the application sandbox path of the file or directory as follows: [Obtain application file paths] (../../../application-models/application-context-stage.md#obtaining-application-file-paths). <br> A uniform resource identifier (URI) is a string pointing to a resource. For APIs that support only the sandbox path as the input parameter, you can construct a <b>fileUri</b> object and obtain the sandbox path property to convert the URI to the sandbox path, and then use the APIs. For details about the URI definition and how to convert a URI to a path, see [File URI](../../../reference/apis-core-file-kit/js-apis-file-fileuri.md).

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## Summary

### Namespaces

| Name | Description |
| --- | --- |
| [fileIo](arkts-corefile-fileio-n.md) | This module is the core module of Core File Kit. It provides APIs for basic file operations, such as creating, opening, reading, writing, copying, moving, deleting, and querying files and directories in the application sandbox. |

### Functions

| Name | Description |
| --- | --- |
| [access](arkts-corefile-file-fs-access-f.md#access-1) | Checks whether a file or directory exists or has the operation permission. This API uses a promise to return the result. |
| [access](arkts-corefile-file-fs-access-f.md#access-2) | Checks whether a file or directory exists. This API uses an asynchronous callback to return the result. |
| [access](arkts-corefile-file-fs-access-f.md#access-3) | Checks whether the file or directory is on the local host or verifies the operation permission. This API uses a promise to return the result. |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md#accesssync-1) | Checks whether a file or directory exists or has the operation permission. This API returns the result synchronously. |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md#accesssync-2) | Checks whether a file or directory is stored locally or has the operation permission. This API returns the result synchronously. |
| [close](arkts-corefile-file-fs-close-f.md#close-1) | Closes a file or directory. After the file or directory is closed, the FD becomes invalid and cannot be used for read/write operations. This API uses a promise to return the result. |
| [close](arkts-corefile-file-fs-close-f.md#close-2) | Closes a file or directory. After the file or directory is closed, the FD becomes invalid and cannot be used for read/write operations. This API uses an asynchronous callback to return the result. |
| [closeSync](arkts-corefile-file-fs-closesync-f.md#closesync-1) | Closes a file or directory synchronously. After the file or directory is closed, the FD becomes invalid and cannot be used for read/write operations. |
| [connectDfs](arkts-corefile-file-fs-connectdfs-f.md#connectdfs-1) | Triggers connection. If the peer device is abnormal, [onStatus](arkts-corefile-file-fs-dfslisteners-i.md#onstatus) in **DfsListeners** will be called to notify the application. |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-1) | Copies a file or directory. This API uses a promise to return the result. |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-2) | Copies a file or directory. This API uses an asynchronous callback to return the result. |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-3) | Copies a file or directory. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-1) | Copies the source directory and its content to the destination path. You can set the conflict handling mode. This API uses a promise to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-2) | Copies the source directory and its content to the destination path. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-3) | Copies the source directory to the destination path. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-4) | Copies the source directory and its content to the destination path. You can set the conflict handling mode. This API uses an asynchronous callback to return the result. |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-5) | Copies the source directory and its content to the destination path. You can set the conflict handling mode. This API uses an asynchronous callback to return the result. |
| [copyDirSync](arkts-corefile-file-fs-copydirsync-f.md#copydirsync-1) | Copies the source directory to the destination path. This API returns the result synchronously. |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-1) | Copies a file. This API uses a promise to return the result. |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-2) | Copies a file. This API overwrites the file with the same name in the destination directory and truncates the part that is not overwritten. This API uses an asynchronous callback to return the result. |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-3) | Copies a file with the specified mode. This API uses an asynchronous callback to return the result. |
| [copyFileSync](arkts-corefile-file-fs-copyfilesync-f.md#copyfilesync-1) | Copies a file. This API returns the result synchronously. |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createrandomaccessfile-1) | Creates a **RandomAccessFile** instance based on the specified file path or file object. This API uses a promise to return the result. |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createrandomaccessfile-2) | Creates a <b>RandomAccessFile</b> instance in read-only mode based on a file path or file object. This API uses an asynchronous callback to return the result. |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createrandomaccessfile-3) | Creates a <b>RandomAccessFile</b> instance based on a file path or file object. This API uses an asynchronous callback to return the result. |
| [createRandomAccessFileSync](arkts-corefile-file-fs-createrandomaccessfilesync-f.md#createrandomaccessfilesync-1) | Creates a **RandomAccessFile** instance based on a file path or file object. |
| [createReadStream](arkts-corefile-file-fs-createreadstream-f.md#createreadstream-1) | Creates a readable stream. This API returns the result synchronously. |
| [createStream](arkts-corefile-file-fs-createstream-f.md#createstream-1) | Creates a stream based on a file path. This API uses a promise to return the result. To close the stream, use <b>close()</b> of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [createStream](arkts-corefile-file-fs-createstream-f.md#createstream-2) | Creates a stream based on a file path. To close the stream, use <b>close()</b> of [Stream](arkts-corefile-file-fs-stream-i.md). This API uses an asynchronous callback to return the result. |
| [createStreamSync](arkts-corefile-file-fs-createstreamsync-f.md#createstreamsync-1) | Creates a stream based on a file path. This API returns the result synchronously. To close the stream, use **close()** of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [createWatcher](arkts-corefile-file-fs-createwatcher-f.md#createwatcher-1) | Creates a <b>Watcher</b> object to listen for file or directory changes such as creating, deleting, and modifying. |
| [createWriteStream](arkts-corefile-file-fs-createwritestream-f.md#createwritestream-1) | Creates a writeable stream. This API returns the result synchronously. |
| [disconnectDfs](arkts-corefile-file-fs-disconnectdfs-f.md#disconnectdfs-1) | Triggers disconnection. |
| [dup](arkts-corefile-file-fs-dup-f.md#dup-1) | Duplicates the file descriptor and returns the corresponding **File** object. |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync-1) | Synchronizes data in a file. This API uses a promise to return the result. |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync-2) | Synchronizes data in a file. This API uses an asynchronous callback to return the result. |
| [fdatasyncSync](arkts-corefile-file-fs-fdatasyncsync-f.md#fdatasyncsync-1) | Synchronizes the data of a file. This API returns the result synchronously. |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md#fdopenstream-1) | Opens a file stream based on the file descriptor. This API uses a promise to return the result. To close the stream, use <b>close()</b> of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md#fdopenstream-2) | Opens a stream based on the file descriptor. To close the stream, use <b>close()</b> of [Stream](arkts-corefile-file-fs-stream-i.md). This API uses an asynchronous callback to return the result. |
| [fdopenStreamSync](arkts-corefile-file-fs-fdopenstreamsync-f.md#fdopenstreamsync-1) | Opens a stream based on the file descriptor. This API returns the result synchronously. To close the stream, use <b>close()</b> of [Stream](arkts-corefile-file-fs-stream-i.md). |
| [fsync](arkts-corefile-file-fs-fsync-f.md#fsync-1) | Synchronizes the cached data of a file to storage. This API uses a promise to return the result. |
| [fsync](arkts-corefile-file-fs-fsync-f.md#fsync-2) | Synchronizes the cached data of a file to storage. This API uses an asynchronous callback to return the result. |
| [fsyncSync](arkts-corefile-file-fs-fsyncsync-f.md#fsyncsync-1) | Synchronizes the cached data of a file to storage. This API returns the result synchronously. |
| [getxattr](arkts-corefile-file-fs-getxattr-f.md#getxattr-1) | Obtains an extended attribute of a file or directory. This API uses a promise to return the result. |
| [getxattrSync](arkts-corefile-file-fs-getxattrsync-f.md#getxattrsync-1) | Obtains an extended attribute of a file or directory. This API returns the result synchronously. |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1) | Lists the names of all files and directories in the current path. Filtering is supported. This API uses a promise to return the result. |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listfile-2) | Lists the names of all files and directories in the current path. A file name array is returned. This API uses an asynchronous callback to return the result. |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listfile-3) | Lists the names of all files and directories in the current path. Filtering is supported. This API uses an asynchronous callback to return the result. |
| [listFileExt](arkts-corefile-file-fs-listfileext-f.md#listfileext-1) | Lists all file names in a directory. This API uses a promise to return the result. This API supports recursive listing of all file names and custom file name filtering. The returned result starts with a slash (/) and contains the subdirectory. |
| [listFileExtSync](arkts-corefile-file-fs-listfileextsync-f.md#listfileextsync-1) | Lists all file names in a directory. This API returns the result synchronously. This API supports recursive listing of all file names and custom file name filtering. The returned result starts with a slash (/) and contains the subdirectory. |
| [listFileSync](arkts-corefile-file-fs-listfilesync-f.md#listfilesync-1) | Lists the names of all files and directories in the current directory. This API returns the result synchronously. Filtering is supported. |
| [lseek](arkts-corefile-file-fs-lseek-f.md#lseek-1) | Adjusts the position of the file offset pointer. |
| [lstat](arkts-corefile-file-fs-lstat-f.md#lstat-1) | Obtains information about a symbolic link that is used to refer to a file or directory. The attributes of the symbolic link are returned, instead of the attributes of the target file. This API uses a promise to return the result. |
| [lstat](arkts-corefile-file-fs-lstat-f.md#lstat-2) | Obtains information about a symbolic link that is used to refer to a file or directory. The attributes of the symbolic link are returned, instead of the attributes of the target file. This API uses an asynchronous callback to return the result. |
| [lstatSync](arkts-corefile-file-fs-lstatsync-f.md#lstatsync-1) | Obtains information about a symbolic link that is used to refer to a file or directory synchronously. The attributes of the symbolic link are returned, instead of the attributes of the target file. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-1) | Creates a single-level directory. If the parent directory does not exist, an error is reported. This API uses a promise to return the result. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-2) | Creates a directory. This API uses a promise to return the result. The value <b>true</b> means to create a directory recursively. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-3) | Creates a single-level directory. If the parent directory does not exist, an error is reported. This API uses an asynchronous callback to return the result. |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-4) | Creates a directory. If <b>recursion</b> is set to <b>true</b>, a directory is created recursively. This API uses an asynchronous callback to return the result. |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md#mkdirsync-1) | Creates a single-level directory synchronously. If the parent directory does not exist, an error is reported. |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md#mkdirsync-2) | Creates a directory. This API returns the result synchronously. The value **true** means to create a directory recursively. |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp-1) | Create a temporary directory. This API uses a promise to return the result. |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp-2) | Create a temporary directory. This API uses an asynchronous callback to return the result. |
| [mkdtempSync](arkts-corefile-file-fs-mkdtempsync-f.md#mkdtempsync-1) | Creates a temporary directory. This API returns the result synchronously. |
| [mmap](arkts-corefile-file-fs-mmap-f.md#mmap-1) | Creates a file mapping object based on a file descriptor or file object for efficient read and write access to files. This API uses a promise to return the result. |
| [mmapSync](arkts-corefile-file-fs-mmapsync-f.md#mmapsync-1) | Creates a file mapping object synchronously based on a file descriptor or file object for efficient read and write access to files. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-1) | Moves the source directory and its content to the destination path. This API uses a promise to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-2) | Moves the source directory and its content to the destination path. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-3) | Moves the source directory and its content to the destination path. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-4) | Moves the source directory and its content to the destination path. You can set the conflict handling mode. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-5) | Moves the source directory and its content to the destination path. You can set the conflict handling mode. This API uses an asynchronous callback to return the result. |
| [moveDirSync](arkts-corefile-file-fs-movedirsync-f.md#movedirsync-1) | Moves the source directory and its content to the destination directory. This API returns the result synchronously. |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#movefile-1) | Moves a file to the target path. You can set the conflict handling mode. This API uses a promise to return the result. |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#movefile-2) | Moves a file and forcibly overwrites the file with the same name in the destination directory. This API uses an asynchronous callback to return the result. |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#movefile-3) | Moves a file to the target path. You can set the conflict handling mode. This API uses an asynchronous callback to return the result. |
| [moveFileSync](arkts-corefile-file-fs-movefilesync-f.md#movefilesync-1) | Moves a file to the destination path. This API returns the result synchronously. |
| [open](arkts-corefile-file-fs-open-f.md#open-1) | Opens a file or directory. This API supports the use of a URI. This API uses a promise to return the result. |
| [open](arkts-corefile-file-fs-open-f.md#open-2) | Opens a file or directory. This API supports the use of a URI. This API uses an asynchronous callback to return the result. |
| [open](arkts-corefile-file-fs-open-f.md#open-3) | Opens a file or directory with the specified mode. This API uses an asynchronous callback to return the result. |
| [openSync](arkts-corefile-file-fs-opensync-f.md#opensync-1) | Opens a file or directory. This API returns the result synchronously. This API supports the use of a URI. |
| [read](arkts-corefile-file-fs-read-f.md#read-1) | Reads file data. This API uses a promise to return the result. |
| [read](arkts-corefile-file-fs-read-f.md#read-2) | Reads data from a file and returns the number of bytes read. This API uses an asynchronous callback to return the result. |
| [read](arkts-corefile-file-fs-read-f.md#read-3) | Reads data from a file. This API uses an asynchronous callback to return the result. |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readlines-1) | Reads a file text line by line. Only the files in UTF-8 format are supported. This API uses a promise to return the result. |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readlines-2) | Reads a file text line by line. Only the files in UTF-8 format are supported. This API uses an asynchronous callback to return the result. |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readlines-3) | Reads a file text line by line. Read options can be configured. Only the files in UTF-8 format are supported. This API uses an asynchronous callback to return the result. |
| [readLinesSync](arkts-corefile-file-fs-readlinessync-f.md#readlinessync-1) | Reads a file text line by line synchronously. Only the files in UTF-8 format are supported. |
| [readSync](arkts-corefile-file-fs-readsync-f.md#readsync-1) | Reads data from a file. This API returns the result synchronously. |
| [readText](arkts-corefile-file-fs-readtext-f.md#readtext-1) | Reads the text content of a file. This API uses a promise to return the result. |
| [readText](arkts-corefile-file-fs-readtext-f.md#readtext-2) | Reads the text of a file. This API uses an asynchronous callback to return the result. |
| [readText](arkts-corefile-file-fs-readtext-f.md#readtext-3) | Reads the text content of a file. This API uses an asynchronous callback to return the result. |
| [readTextSync](arkts-corefile-file-fs-readtextsync-f.md#readtextsync-1) | Reads the text content of a file. This API returns the result synchronously. |
| [rename](arkts-corefile-file-fs-rename-f.md#rename-1) | Renames a file or directory. This API uses a promise to return the result. |
| [rename](arkts-corefile-file-fs-rename-f.md#rename-2) | Renames a file or directory. This API uses an asynchronous callback to return the result. |
| [renameSync](arkts-corefile-file-fs-renamesync-f.md#renamesync-1) | Renames a file or directory. This API returns the result synchronously. |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md#rmdir-1) | Deletes a directory and all its subdirectories and files. This API uses a promise to return the result. |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md#rmdir-2) | Deletes a directory and all its subdirectories and files. This API uses an asynchronous callback to return the result. |
| [rmdirSync](arkts-corefile-file-fs-rmdirsync-f.md#rmdirsync-1) | Removes a directory and all its subdirectories and files synchronously. |
| [setxattr](arkts-corefile-file-fs-setxattr-f.md#setxattr-1) | Sets an extended attribute of a file or directory. This API uses a promise to return the result. |
| [setxattrSync](arkts-corefile-file-fs-setxattrsync-f.md#setxattrsync-1) | Sets an extended attribute of a file or directory. |
| [stat](arkts-corefile-file-fs-stat-f.md#stat-1) | Obtains detailed attributes of a file or directory. The returned <b>Stat</b> object contains attributes such as the file size, permission mode, access time, and modification time. This API uses a promise to return the result. |
| [stat](arkts-corefile-file-fs-stat-f.md#stat-2) | Obtains detailed attributes of a file or directory. The returned <b>Stat</b> object contains attributes such as the file size, permission mode, access time, and modification time. This API uses an asynchronous callback to return the result. |
| [statSync](arkts-corefile-file-fs-statsync-f.md#statsync-1) | Obtains detailed attributes of a file or directory synchronously. The returned <b>Stat</b> object contains attributes such as the file size, permission mode, access time, and modification time. |
| [symlink](arkts-corefile-file-fs-symlink-f.md#symlink-1) | Creates a symbolic link based on a file path. This API uses a promise to return the result. |
| [symlink](arkts-corefile-file-fs-symlink-f.md#symlink-2) | Creates a symbolic link based on a file path. This API uses an asynchronous callback to return the result. |
| [symlinkSync](arkts-corefile-file-fs-symlinksync-f.md#symlinksync-1) | Creates a symbolic link based on the file path. This API returns the result synchronously. |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1) | Truncates a file to the specified length. Excess content will be deleted. This API uses a promise to return the result. |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-2) | Truncates a file and deletes its content. This API uses an asynchronous callback to return the result. |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-3) | Truncates a file to the specified length. Excess content will be deleted. This API uses an asynchronous callback to return the result. |
| [truncateSync](arkts-corefile-file-fs-truncatesync-f.md#truncatesync-1) | Truncates a file to the specified length synchronously. Excess content will be deleted. |
| [unlink](arkts-corefile-file-fs-unlink-f.md#unlink-1) | Deletes a single file. This method cannot be used to delete a directory. This API uses a promise to return the result. |
| [unlink](arkts-corefile-file-fs-unlink-f.md#unlink-2) | Deletes a single file. This method cannot be used to delete a directory. This API uses an asynchronous callback to return the result. |
| [unlinkSync](arkts-corefile-file-fs-unlinksync-f.md#unlinksync-1) | Deletes a single file synchronously. This method cannot be used to delete a directory. |
| [utimes](arkts-corefile-file-fs-utimes-f.md#utimes-1) | Last modification time of a file. |
| [write](arkts-corefile-file-fs-write-f.md#write-1) | Writes data into a file. This API uses a promise to return the result. |
| [write](arkts-corefile-file-fs-write-f.md#write-2) | Writes data to a file and returns the number of bytes written. This API uses an asynchronous callback to return the result. |
| [write](arkts-corefile-file-fs-write-f.md#write-3) | Writes data to a file. This API uses an asynchronous callback to return the result. |
| [writeSync](arkts-corefile-file-fs-writesync-f.md#writesync-1) | Writes data to a file. This API returns the result synchronously. |

### Classes

| Name | Description |
| --- | --- |
| [AtomicFile](arkts-corefile-file-fs-atomicfile-c.md) | <b>AtomicFile</b> is a class used to perform atomic read, write, and other operations on files. |
| [ReadStream](arkts-corefile-file-fs-readstream-c.md) | Defines a readable stream. You need to use [createReadStream](arkts-corefile-file-fs-createreadstream-f.md) to create a **ReadStream** instance, which is inherited from [stream.Readable](../../apis-arkts/arkts-apis/arkts-arkts-stream-readableoptions-i.md). |
| [TaskSignal](arkts-corefile-file-fs-tasksignal-c.md) | Provides APIs for interrupting a copy task. |
| [WriteStream](arkts-corefile-file-fs-writestream-c.md) | Defines a writeable stream. You need to use [createWriteStream](arkts-corefile-file-fs-createwritestream-f.md) to create a **WriteStream** instance, which is inherited from [stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md). |

### Interfaces

| Name | Description |
| --- | --- |
| [ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md) | Defines conflicting file information used in **copyDir()** or **moveDir()**. |
| [CopyOptions](arkts-corefile-file-fs-copyoptions-i.md) | Defines the callback for listening for the copy progress. |
| [DfsListeners](arkts-corefile-file-fs-dfslisteners-i.md) | Provides APIs for observing events. listening for the distributed file system status. |
| [File](arkts-corefile-file-fs-file-i.md) | Represents a <b>File</b> object opened by <b>open()</b>. It contains the FD and provides capabilities such as locking a file and obtaining the parent directory. |
| [FileFilter](arkts-corefile-file-fs-filefilter-i.md) | Describes a file name filter, which can be used to customize file name filtering rules. |
| [FileMapping](arkts-corefile-file-fs-filemapping-i.md) | Defines a file mapping object. Before calling the <b>FileMapping</b> method, construct a <b>FileMapping</b> instance using [mmap()](arkts-corefile-file-fs-mmap-f.md) or [mmapSync()](arkts-corefile-file-fs-mmapsync-f.md). |
| [Filter](arkts-corefile-file-fs-filter-i.md) | Defines the file filtering configuration used by **listFile()**. |
| [ListFileExtOptions](arkts-corefile-file-fs-listfileextoptions-i.md) | Defines the options used in <b>listFileExt</b>. |
| [ListFileOptions](arkts-corefile-file-fs-listfileoptions-i.md) | Defines the options used in <b>listFile()</b>. |
| [Options](arkts-corefile-file-fs-options-i.md) | Defines the options used in **readLines()**. |
| [Progress](arkts-corefile-file-fs-progress-i.md) | Defines the copy progress information. |
| [RandomAccessFile](arkts-corefile-file-fs-randomaccessfile-i.md) | Provides APIs for randomly reading and writing a stream based on offset pointers. Before invoking any API of <b>RandomAccessFile</b>, you need to use <b>createRandomAccessFile()</b> to create a <b>RandomAccessFile</b> instance synchronously or asynchronously. |
| [RandomAccessFileOptions](arkts-corefile-file-fs-randomaccessfileoptions-i.md) | Defines the options used in **createRandomAccessFile()**. |
| [ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md) | Provides a **ReaderIterator** object. Before calling APIs of **ReaderIterator**, you need to use **readLines()** to create a **ReaderIterator** instance. |
| [ReaderIteratorResult](arkts-corefile-file-fs-readeriteratorresult-i.md) | Represents the information obtained by the **ReaderIterator** object. |
| [ReadOptions](arkts-corefile-file-fs-readoptions-i.md) | Defines the options used in **read()**. |
| [ReadStreamOptions](arkts-corefile-file-fs-readstreamoptions-i.md) | Defines the options used in **createReadStream()**. |
| [ReadTextOptions](arkts-corefile-file-fs-readtextoptions-i.md) | Defines the options used in <b>readText()</b>. It inherits from [ReadOptions](arkts-corefile-file-fs-readoptions-i.md). |
| [Stat](arkts-corefile-file-fs-stat-i.md) | Obtains detailed information of a file, including attributes such as the file size, permission mode, access time, and modification time. Before calling an API of the <b>Stat</b> class, use stat() to create a <b>Stat</b> instance. |
| [Stream](arkts-corefile-file-fs-stream-i.md) | Provides APIs for stream operations, such as reading and writing data streams of files. After using an API of the <b>Stream</b> class, you need to call <b>close</b> to close the file stream. Before calling an API of the <b>Stream</b> class, you need to create a <b>Stream</b> instance by using createStream or fdopenStream synchronously or asynchronously. |
| [Watcher](arkts-corefile-file-fs-watcher-i.md) | Provides APIs for observing the changes of files or directories. Before using the APIs of **Watcher**, call **createWatcher()** to create a **Watcher** object. |
| [WatchEvent](arkts-corefile-file-fs-watchevent-i.md) | Defines the event to observe. |
| [WatchEventListener](arkts-corefile-file-fs-watcheventlistener-i.md) | Defines a watch event listener. When the monitored file or directory changes, a callback is triggered. |
| [WriteOptions](arkts-corefile-file-fs-writeoptions-i.md) | Defines the options used in <b>write()</b>. It inherits from [Options](arkts-corefile-file-fs-options-i.md). |
| [WriteStreamOptions](arkts-corefile-file-fs-writestreamoptions-i.md) | Defines the options used in **createWriteStream()**. |

### Types

| Name | Description |
| --- | --- |
| [ProgressListener](arkts-corefile-progresslistener-t.md) | Defines the listener used to observe the copy progress. |

### Enums

| Name | Description |
| --- | --- |
| [AccessFlagType](arkts-corefile-file-fs-accessflagtype-e.md) | Enumerates the locations of the file to verify. |
| [AccessModeType](arkts-corefile-file-fs-accessmodetype-e.md) | Enumerates the access modes to verify. If this parameter is left blank, the system checks whether the file exists. |
| [LocationType](arkts-corefile-file-fs-locationtype-e.md) | Enumerates the file locations. |
| [MappingMode](arkts-corefile-file-fs-mappingmode-e.md) | Enumerates file memory mapping modes. |
| [WhenceType](arkts-corefile-file-fs-whencetype-e.md) | Enumerates the types of the relative offset position used in **lseek()**. |
