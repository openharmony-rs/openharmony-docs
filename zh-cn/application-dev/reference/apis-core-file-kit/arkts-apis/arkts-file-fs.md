# @ohos.file.fs

FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [fileIo](arkts-corefile-fileio-n.md) | FileIO |

### 函数

| 名称 | 说明 |
| --- | --- |
| [access](arkts-corefile-file-fs-access-f.md#access) | 检查文件或目录是否存在，或校验操作权限，使用promise异步回调。  校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [access](arkts-corefile-file-fs-access-f.md#access-1) | 检查文件或目录是否存在，使用callback异步回调。 |
| [access](arkts-corefile-file-fs-access-f.md#access-2) | 检查文件或目录是否在本地，或校验操作权限，使用promise异步回调。  校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md#accesssync) | 以同步方法检查文件或目录是否存在，或校验操作权限。  校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md#accesssync-1) | 以同步方法检查文件或目录是否在本地，或校验操作权限。  校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [close](arkts-corefile-file-fs-close-f.md#close) | 关闭文件或目录，使用promise异步回调。 |
| [close](arkts-corefile-file-fs-close-f.md#close-1) | 关闭文件或目录，使用callback异步回调。 |
| [closeSync](arkts-corefile-file-fs-closesync-f.md#closesync) | 以同步方法关闭文件或目录。 |
| [connectDfs](arkts-corefile-file-fs-connectdfs-f.md#connectdfs) | 业务调用connectDfs接口，触发建链。如果对端设备出现异常，业务执行回调DfsListeners内[onStatus](../../../reference/apis-core-file-kit/js-apis-file-fs.md#onstatus12)通知应用。 |
| [copy](arkts-corefile-file-fs-copy-f.md#copy) | 拷贝文件或目录，使用promise异步回调。  支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。  跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-1) | 拷贝文件或者目录，使用callback异步回调。  支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。  跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-2) | 拷贝文件或者目录，使用callback异步回调。  支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。  跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir) | 复制源目录至目标路径下，使用promise异步回调。 |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-1) | 复制源目录至目标路径下，使用callback异步回调。 |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-2) | 复制源目录至目标路径下，使用callback异步回调。  如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array\&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;形式提供。 |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-3) | 复制源目录至目标路径下，可设置复制模式。使用callback异步回调。 |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copydir-4) | 复制源目录至目标路径下，可设置复制模式。使用callback异步回调。 |
| [copyDirSync](arkts-corefile-file-fs-copydirsync-f.md#copydirsync) | 以同步方法复制源目录至目标路径下。 |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile) | 复制文件，使用promise异步回调。 |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-1) | 复制文件，覆盖方式为完全覆盖目标文件，未覆盖部分将被裁切。使用callback异步回调。 |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyfile-2) | 复制文件，可设置覆盖文件的方式，使用callback异步回调。 |
| [copyFileSync](arkts-corefile-file-fs-copyfilesync-f.md#copyfilesync) | 以同步方法复制文件。 |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createrandomaccessfile) | 基于文件路径或文件对象创建RandomAccessFile对象，使用promise异步回调。 |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createrandomaccessfile-1) | 基于文件路径或文件对象，以只读方式创建RandomAccessFile对象，使用callback异步回调。 |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createrandomaccessfile-2) | 基于文件路径或文件对象创建RandomAccessFile对象，使用callback异步回调。 |
| [createRandomAccessFileSync](arkts-corefile-file-fs-createrandomaccessfilesync-f.md#createrandomaccessfilesync) | 基于文件路径或文件对象创建RandomAccessFile对象。 |
| [createReadStream](arkts-corefile-file-fs-createreadstream-f.md#createreadstream) | 以同步方法打开文件可读流。 |
| [createStream](arkts-corefile-file-fs-createstream-f.md#createstream) | 基于文件路径创建文件流，使用promise异步回调。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [createStream](arkts-corefile-file-fs-createstream-f.md#createstream-1) | 基于文件路径创建文件流，使用callback异步回调。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [createStreamSync](arkts-corefile-file-fs-createstreamsync-f.md#createstreamsync) | 以同步方法基于文件路径创建文件流。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [createWatcher](arkts-corefile-file-fs-createwatcher-f.md#createwatcher) | 创建Watcher对象，监听文件或目录变动。 |
| [createWriteStream](arkts-corefile-file-fs-createwritestream-f.md#createwritestream) | 以同步方法打开文件可写流。 |
| [disconnectDfs](arkts-corefile-file-fs-disconnectdfs-f.md#disconnectdfs) | 业务调用disconnectDfs接口，传入networkId参数，触发断链。 |
| [dup](arkts-corefile-file-fs-dup-f.md#dup) | 复制文件描述符，并返回对应的File对象。 |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync) | 实现文件内容数据同步，使用promise异步回调。 |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync-1) | 实现文件内容数据同步，使用callback异步回调。 |
| [fdatasyncSync](arkts-corefile-file-fs-fdatasyncsync-f.md#fdatasyncsync) | 以同步方法实现文件内容的数据同步。 |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md#fdopenstream) | 基于文件描述符打开文件流，使用promise异步回调。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md#fdopenstream-1) | 基于文件描述符打开文件流，使用callback异步回调。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [fdopenStreamSync](arkts-corefile-file-fs-fdopenstreamsync-f.md#fdopenstreamsync) | 以同步方法基于文件描述符打开文件流。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [fsync](arkts-corefile-file-fs-fsync-f.md#fsync) | 将文件系统缓存数据写入磁盘，使用promise异步回调。 |
| [fsync](arkts-corefile-file-fs-fsync-f.md#fsync-1) | 将文件系统缓存数据写入磁盘，使用callback异步回调。 |
| [fsyncSync](arkts-corefile-file-fs-fsyncsync-f.md#fsyncsync) | 以同步方法将文件系统缓存数据写入磁盘。 |
| [getxattr](arkts-corefile-file-fs-getxattr-f.md#getxattr) | 获取文件或目录的扩展属性。使用promise异步回调。 |
| [getxattrSync](arkts-corefile-file-fs-getxattrsync-f.md#getxattrsync) | 使用同步接口获取文件或目录的扩展属性。 |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listfile) | 默认列出当前目录下所有文件名和目录名。支持过滤。使用promise异步回调。  可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listfile-1) | 默认列出当前目录下所有文件名和目录名。支持过滤。使用callback异步回调。  可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listfile-2) | 默认列出当前目录下所有文件名和目录名。支持过滤。使用callback异步回调。  可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExt](arkts-corefile-file-fs-listfileext-f.md#listfileext) | 列出目录下所有文件名，使用Promise异步回调。该接口支持通过自定义过滤函数对文件名进行过滤。可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExtSync](arkts-corefile-file-fs-listfileextsync-f.md#listfileextsync) | 以同步方法列出目录下所有文件名，支持通过自定义过滤函数对文件名进行过滤。可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileSync](arkts-corefile-file-fs-listfilesync-f.md#listfilesync) | 默认以同步方式列出当前目录下所有文件名和目录名。支持过滤。  可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [lseek](arkts-corefile-file-fs-lseek-f.md#lseek) | 调整文件偏移指针位置。 |
| [lstat](arkts-corefile-file-fs-lstat-f.md#lstat) | 获取符号链接文件信息，使用promise异步回调。 |
| [lstat](arkts-corefile-file-fs-lstat-f.md#lstat-1) | 获取符号链接文件信息，使用callback异步回调。 |
| [lstatSync](arkts-corefile-file-fs-lstatsync-f.md#lstatsync) | 以同步方法获取符号链接文件信息。 |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir) | 创建目录，使用promise异步回调。 |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-1) | 创建目录，使用promise异步回调。当recursion指定为true时，可递归创建目录。 |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-2) | 创建目录，使用callback异步回调。 |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-3) | 创建目录，使用callback异步回调。当recursion指定为true，可递归创建目录。 |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md#mkdirsync) | 以同步方法创建目录。 |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md#mkdirsync-1) | 以同步方法创建目录。当recursion指定为true，可递归创建目录。 |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp) | 创建临时目录，使用promise异步回调。 |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp-1) | 创建临时目录，使用callback异步回调。 |
| [mkdtempSync](arkts-corefile-file-fs-mkdtempsync-f.md#mkdtempsync) | 以同步的方法创建临时目录。 |
| [mmap](arkts-corefile-file-fs-mmap-f.md#mmap) | 基于文件描述符或文件对象创建文件映射对象，使用promise异步回调。将文件内容映射到内存，以实现文件的高效读写访问。注意：读写模式（MappingMode.READ_WRITE）下，若映射范围超过原始文件大小，将自动扩展文件大小。  > **说明**  > 注意：在读写模式（MappingMode.READ_WRITE）下，如果映射范围超过原始文件大小，则文件大小  > 将自动展开。 |
| [mmapSync](arkts-corefile-file-fs-mmapsync-f.md#mmapsync) | 以同步方法基于文件描述符或文件对象创建文件映射对象。将文件内容映射到内存，以实现文件的高效读写访问。注意：读写模式（MappingMode.READ_WRITE）下，若映射范围超过原始文件大小，将自动扩展文件大小。 |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir) | 移动源目录至目标路径下，使用promise异步回调。 |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-1) | Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-2) | 移动源目录至目标路径下。使用callback异步回调。  移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。 |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-3) | 移动源目录至目标路径下，支持设置移动模式。使用callback异步回调。 |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#movedir-4) | 移动源目录至目标路径下，支持设置移动模式。使用callback异步回调。 |
| [moveDirSync](arkts-corefile-file-fs-movedirsync-f.md#movedirsync) | 以同步方法移动源目录至目标路径下。 |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#movefile) | 移动文件，使用promise异步回调。 |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#movefile-1) | 移动文件。如果移动位置存在同名文件，将强制覆盖。使用callback异步回调。 |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#movefile-2) | 移动文件，支持设置移动模式。使用callback异步回调。 |
| [moveFileSync](arkts-corefile-file-fs-movefilesync-f.md#movefilesync) | 以同步方式移动文件。 |
| [open](arkts-corefile-file-fs-open-f.md#open) | 打开文件或目录，使用promise异步回调。支持使用URI打开文件。 |
| [open](arkts-corefile-file-fs-open-f.md#open-1) | 打开文件或目录，使用callback异步回调。支持使用URI打开文件。 |
| [open](arkts-corefile-file-fs-open-f.md#open-2) | 打开文件或目录，可设置打开文件的选项。使用callback异步回调。  支持使用URI打开文件。 |
| [openSync](arkts-corefile-file-fs-opensync-f.md#opensync) | 以同步方法打开文件或目录。支持使用URI打开文件。 |
| [read](arkts-corefile-file-fs-read-f.md#read) | 读取文件数据，使用promise异步回调。 |
| [read](arkts-corefile-file-fs-read-f.md#read-1) | 从文件读取数据，使用callback异步回调。 |
| [read](arkts-corefile-file-fs-read-f.md#read-2) | 从文件读取数据，使用callback异步回调。 |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readlines) | 逐行读取文件文本内容，使用promise异步回调。只支持读取utf-8格式文件。 |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readlines-1) | 逐行读取文件文本内容，使用callback异步回调，只支持读取utf-8格式文件。 |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readlines-2) | 逐行读取文件文本内容，使用callback异步回调，只支持读取utf-8格式文件。 |
| [readLinesSync](arkts-corefile-file-fs-readlinessync-f.md#readlinessync) | 以同步方式逐行读取文件的文本内容。 |
| [readSync](arkts-corefile-file-fs-readsync-f.md#readsync) | 以同步方法从文件读取数据。 |
| [readText](arkts-corefile-file-fs-readtext-f.md#readtext) | 基于文本方式读取文件（即直接读取文件的文本内容），使用promise异步回调。 |
| [readText](arkts-corefile-file-fs-readtext-f.md#readtext-1) | 基于文本方式读取文件内容，使用callback异步回调。 |
| [readText](arkts-corefile-file-fs-readtext-f.md#readtext-2) | 基于文本方式读取文件内容，使用callback异步回调。 |
| [readTextSync](arkts-corefile-file-fs-readtextsync-f.md#readtextsync) | 以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。 |
| [rename](arkts-corefile-file-fs-rename-f.md#rename) | 重命名文件或目录，使用promise异步回调。 |
| [rename](arkts-corefile-file-fs-rename-f.md#rename-1) | 重命名文件或目录，使用callback异步回调。 |
| [renameSync](arkts-corefile-file-fs-renamesync-f.md#renamesync) | 以同步方法重命名文件或目录。 |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md#rmdir) | 删除目录及其所有子目录和文件，使用promise异步回调。 |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md#rmdir-1) | 删除目录及其所有子目录和文件，使用callback异步回调。 |
| [rmdirSync](arkts-corefile-file-fs-rmdirsync-f.md#rmdirsync) | 以同步方法删除目录及其所有子目录和文件。 |
| [setxattr](arkts-corefile-file-fs-setxattr-f.md#setxattr) | 设置文件或目录的扩展属性。使用promise异步回调。 |
| [setxattrSync](arkts-corefile-file-fs-setxattrsync-f.md#setxattrsync) | 设置文件或目录的扩展属性。 |
| [stat](arkts-corefile-file-fs-stat-f.md#stat) | 获取文件或目录详细属性信息，使用promise异步回调。 |
| [stat](arkts-corefile-file-fs-stat-f.md#stat-1) | 获取文件或目录的详细属性信息，使用callback异步回调。 |
| [statSync](arkts-corefile-file-fs-statsync-f.md#statsync) | 以同步方法获取文件或目录详细属性信息。 |
| [symlink](arkts-corefile-file-fs-symlink-f.md#symlink) | 基于文件路径创建符号链接，使用promise异步回调。 |
| [symlink](arkts-corefile-file-fs-symlink-f.md#symlink-1) | 基于文件路径创建符号链接，使用callback异步回调。 |
| [symlinkSync](arkts-corefile-file-fs-symlinksync-f.md#symlinksync) | 以同步的方法基于文件路径创建符号链接。 |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate) | 截断文件，使用promise异步回调。 |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1) | 截断文件，使用callback异步回调。 |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-2) | 截断文件，使用callback异步回调。 |
| [truncateSync](arkts-corefile-file-fs-truncatesync-f.md#truncatesync) | 以同步方法截断文件内容。 |
| [unlink](arkts-corefile-file-fs-unlink-f.md#unlink) | 删除单个文件，使用promise异步回调。 |
| [unlink](arkts-corefile-file-fs-unlink-f.md#unlink-1) | 删除文件，使用callback异步回调。 |
| [unlinkSync](arkts-corefile-file-fs-unlinksync-f.md#unlinksync) | 以同步方法删除文件。 |
| [utimes](arkts-corefile-file-fs-utimes-f.md#utimes) | 更改文件上次修改该文件的时间。 |
| [write](arkts-corefile-file-fs-write-f.md#write) | 将数据写入文件，使用promise异步回调。 |
| [write](arkts-corefile-file-fs-write-f.md#write-1) | 将数据写入文件，使用callback异步回调。 |
| [write](arkts-corefile-file-fs-write-f.md#write-2) | 将数据写入文件，使用callback异步回调。 |
| [writeSync](arkts-corefile-file-fs-writesync-f.md#writesync) | 以同步方法将数据写入文件。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AtomicFile](arkts-corefile-file-fs-atomicfile-c.md) | AtomicFile是一个用于对文件进行原子读写操作的类。  在写操作时，通过写入临时文件，并在写入成功后将其重命名到原始文件位置来确保写入文件的完整性；而在写入失败时删除临时文件，不修改原始文件内容。  使用者可以自行调用finishWrite或failWrite来完成文件内容的写入或回滚。 |
| [ReadStream](arkts-corefile-file-fs-readstream-c.md) | 文件可读流，需要先通过fileIo.createReadStream方法来构建一个ReadStream实例。ReadStream继承自数据流基类stream.Readable。ReadStream读到的数据为解码后的字符串，其编码格式当前仅支持'utf-8'。 |
| [TaskSignal](arkts-corefile-file-fs-tasksignal-c.md) | 拷贝中断信号。 |
| [WriteStream](arkts-corefile-file-fs-writestream-c.md) | 文件可写流，需要先通过[fileIo.createWriteStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatewritestream12)方法来构建一个WriteStream实例。WriteStream继承自数据流基类[stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md) | 冲突文件信息，支持copyDir及moveDir接口使用。 |
| [CopyOptions](arkts-corefile-file-fs-copyoptions-i.md) | 拷贝进度回调监听 |
| [DfsListeners](arkts-corefile-file-fs-dfslisteners-i.md) | 事件监听类。创建DFSListener对象，用于监听分布式文件系统状态。 |
| [File](arkts-corefile-file-fs-file-i.md) | 由open接口打开的File对象。 |
| [FileFilter](arkts-corefile-file-fs-filefilter-i.md) | 文件名过滤器，支持listFileExt接口使用。 |
| [FileMapping](arkts-corefile-file-fs-filemapping-i.md) | 文件映射对象，在调用FileMapping的方法前，需要先通过mmap()方法（同步或异步）构建一个FileMapping实例。 |
| [Filter](arkts-corefile-file-fs-filter-i.md) | 文件过滤配置项，支持listFile接口使用。 |
| [ListFileExtOptions](arkts-corefile-file-fs-listfileextoptions-i.md) | 可选项类型，支持listFileExt接口使用自定义过滤规则。 |
| [ListFileOptions](arkts-corefile-file-fs-listfileoptions-i.md) | 可选项类型，支持ListFile接口使用。 |
| [Options](arkts-corefile-file-fs-options-i.md) | 可选项类型，支持readLines接口使用。 |
| [Progress](arkts-corefile-file-fs-progress-i.md) | 拷贝进度回调数据 |
| [RandomAccessFile](arkts-corefile-file-fs-randomaccessfile-i.md) | 随机读写文件流。在调用RandomAccessFile的方法前，需要先通过createRandomAccessFile()方法（同步或异步）来构建一个RandomAccessFile实例。 |
| [RandomAccessFileOptions](arkts-corefile-file-fs-randomaccessfileoptions-i.md) | 可选项类型，支持 createRandomAccessFile 接口使用。 |
| [ReadOptions](arkts-corefile-file-fs-readoptions-i.md) | 可选项类型，支持read接口使用。 |
| [ReadStreamOptions](arkts-corefile-file-fs-readstreamoptions-i.md) | 可选项类型，支持 createReadStream 接口使用。 |
| [ReadTextOptions](arkts-corefile-file-fs-readtextoptions-i.md) | 可选项类型，支持readText接口使用，ReadTextOptions继承至[ReadOptions](arkts-corefile-file-fs-readoptions-i.md)。 |
| [ReaderIterator](arkts-corefile-file-fs-readeriterator-i.md) | 文件读取迭代器。在调用ReaderIterator的方法前，需要先通过readLines方法（同步或异步）来构建一个ReaderIterator实例。 |
| [ReaderIteratorResult](arkts-corefile-file-fs-readeriteratorresult-i.md) | 文件读取迭代器返回结果，支持ReaderIterator接口使用。 |
| [Stat](arkts-corefile-file-fs-stat-i.md) | 文件具体信息，在调用Stat的方法前，需要先通过[stat()](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiostat)方法（同步或异步）构建一个Stat实例。 |
| [Stream](arkts-corefile-file-fs-stream-i.md) | 文件流，在调用Stream的方法前，需要先通过[fileIo.createStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatestream)方法或者[fileIo.fdopenStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiofdopenstream)（同步或异步）来构建一个Stream实例。 |
| [WatchEvent](arkts-corefile-file-fs-watchevent-i.md) | 事件类 |
| [WatchEventListener](arkts-corefile-file-fs-watcheventlistener-i.md) | 事件监听类。 |
| [Watcher](arkts-corefile-file-fs-watcher-i.md) | 文件目录变化监听对象。由createWatcher接口获得。 |
| [WriteOptions](arkts-corefile-file-fs-writeoptions-i.md) | 可选项类型，支持write接口使用，WriteOptions继承至[Options](arkts-corefile-file-fs-options-i.md)。 |
| [WriteStreamOptions](arkts-corefile-file-fs-writestreamoptions-i.md) | 可选项类型，支持 createWriteStream 接口使用。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessFlagType](arkts-corefile-file-fs-accessflagtype-e.md) | 枚举，表示需要校验的文件位置。 |
| [AccessModeType](arkts-corefile-file-fs-accessmodetype-e.md) | 枚举，表示需要校验的具体权限。若不填，默认校验文件是否存在。 |
| [LocationType](arkts-corefile-file-fs-locationtype-e.md) | 枚举，文件位置，表示该文件是否在本地或者云端存在。 |
| [MappingMode](arkts-corefile-file-fs-mappingmode-e.md) | 枚举，文件内存映射模式类型，支持mmap接口使用。 |
| [WhenceType](arkts-corefile-file-fs-whencetype-e.md) | 枚举，文件偏移指针相对偏移位置类型，支持lseek接口使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ProgressListener](arkts-corefile-progresslistener-t.md) | 拷贝进度监听。 |

