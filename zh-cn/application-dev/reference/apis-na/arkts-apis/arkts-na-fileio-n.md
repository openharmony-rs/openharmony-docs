# fileIo

FileIO

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

**废弃版本：** -1

<!--Device-unnamed-declare namespace fileIo--><!--Device-unnamed-declare namespace fileIo-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [OpenMode](arkts-na-fileio-openmode-n.md) | open接口flags参数常量，用于指定文件打开模式（如只读、只写、读写、创建等）。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [access](arkts-na-fileio-access-f.md#access) | 检查文件或目录是否存在，或校验操作权限。使用Promise异步回调。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [access](arkts-na-fileio-access-f.md#access) | 检查文件或目录是否存在。使用callback异步回调。 |
| [access](arkts-na-fileio-access-f.md#access) | 检查文件或目录是否在本地，或校验操作权限。使用Promise异步回调。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync](arkts-na-fileio-accesssync-f.md#accessSync) | 以同步方法检查文件或目录是否存在，或校验操作权限。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync](arkts-na-fileio-accesssync-f.md#accessSync) | 以同步方法检查文件或目录是否在本地，或校验操作权限。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [close](arkts-na-fileio-close-f.md#close) | 关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用Promise异步回调。 |
| [close](arkts-na-fileio-close-f.md#close) | 关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用callback异步回调。 |
| [closeSync](arkts-na-fileio-closesync-f.md#closeSync) | 以同步方法关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。 |
| [copy](arkts-na-fileio-copy-f.md#copy) | 拷贝文件或目录。使用Promise异步回调。 支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。 跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy](arkts-na-fileio-copy-f.md#copy) | 拷贝文件或者目录。使用callback异步回调。 支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。 跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy](arkts-na-fileio-copy-f.md#copy) | 拷贝文件或者目录。使用callback异步回调。 支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。 跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copyDir](arkts-na-fileio-copydir-f.md#copyDir) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用Promise异步回调。 |
| [copyDir](arkts-na-fileio-copydir-f.md#copyDir) | 复制源目录及其内容至目标路径下。使用callback异步回调。 如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部拷贝至目标目录下，目标目录下未冲突文件将继续保留。 |
| [copyDirWithConflictFiles](arkts-na-fileio-copydirwithconflictfiles-f.md#copyDirWithConflictFiles) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。 源目录下未冲突的文件全部移动至目标目录下，目标目录下冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array&lt;ConflictFiles&gt;形式提供。 |
| [copyDir](arkts-na-fileio-copydir-f.md#copyDir) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 |
| [copyDirWithConflictFiles](arkts-na-fileio-copydirwithconflictfiles-f.md#copyDirWithConflictFiles) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 |
| [copyDirSync](arkts-na-fileio-copydirsync-f.md#copyDirSync) | 以同步方法复制源目录至目标路径下。 |
| [copyFile](arkts-na-fileio-copyfile-f.md#copyFile) | 复制文件。使用Promise异步回调。 |
| [copyFile](arkts-na-fileio-copyfile-f.md#copyFile) | 复制文件，覆盖方式为完全覆盖目标文件，未覆盖部分将被裁剪。使用callback异步回调。 |
| [copyFile](arkts-na-fileio-copyfile-f.md#copyFile) | 复制文件，可设置覆盖文件的方式。使用callback异步回调。 |
| [copyFileSync](arkts-na-fileio-copyfilesync-f.md#copyFileSync) | 以同步方法复制文件。 |
| [createStream](arkts-na-fileio-createstream-f.md#createStream) | 基于文件路径创建文件流。使用Promise异步回调。需要配合[Stream](arkts-na-fileio-stream-i.md#Stream)中的close()函数关闭文件流。 |
| [createStream](arkts-na-fileio-createstream-f.md#createStream) | 基于文件路径创建文件流，需要配合[Stream](arkts-na-fileio-stream-i.md#Stream)中的close()函数关闭文件流。使用callback异步回调。 |
| [createStreamSync](arkts-na-fileio-createstreamsync-f.md#createStreamSync) | 以同步方法基于文件路径创建文件流。需要配合[Stream](arkts-na-fileio-stream-i.md#Stream)中的close()函数关闭文件流。 |
| [createRandomAccessFile](arkts-na-fileio-createrandomaccessfile-f.md#createRandomAccessFile) | 基于文件路径或文件对象创建RandomAccessFile对象。使用Promise异步回调。 |
| [createRandomAccessFile](arkts-na-fileio-createrandomaccessfile-f.md#createRandomAccessFile) | 基于文件路径或文件对象，以只读方式创建RandomAccessFile对象。使用callback异步回调。 |
| [createRandomAccessFile](arkts-na-fileio-createrandomaccessfile-f.md#createRandomAccessFile) | 基于文件路径或文件对象创建RandomAccessFile对象。使用callback异步回调。 |
| [createRandomAccessFileSync](arkts-na-fileio-createrandomaccessfilesync-f.md#createRandomAccessFileSync) | 基于文件路径或文件对象创建RandomAccessFile对象。 |
| [createReadStream](arkts-na-fileio-createreadstream-f.md#createReadStream) | 以同步方法打开文件可读流。 |
| [createWriteStream](arkts-na-fileio-createwritestream-f.md#createWriteStream) | 以同步方法打开文件可写流。 |
| [createWatcher](arkts-na-fileio-createwatcher-f.md#createWatcher) | 创建Watcher对象，用于监听文件或目录的创建、删除、修改等变动事件。 |
| [dup](arkts-na-fileio-dup-f.md#dup) | 复制文件描述符，并返回对应的File对象。 |
| [fdatasync](arkts-na-fileio-fdatasync-f.md#fdatasync) | 实现文件内容数据同步。使用Promise异步回调。 |
| [fdatasync](arkts-na-fileio-fdatasync-f.md#fdatasync) | 实现文件内容数据同步。使用callback异步回调。 |
| [fdatasyncSync](arkts-na-fileio-fdatasyncsync-f.md#fdatasyncSync) | 以同步方法实现文件内容的数据同步。 |
| [fdopenStream](arkts-na-fileio-fdopenstream-f.md#fdopenStream) | 基于文件描述符打开文件流。使用Promise异步回调。需要配合[Stream](arkts-na-fileio-stream-i.md#Stream)中的close()函数关闭文件流。 |
| [fdopenStream](arkts-na-fileio-fdopenstream-f.md#fdopenStream) | 基于文件描述符打开文件流，需要配合[Stream](arkts-na-fileio-stream-i.md#Stream)中的close()函数关闭文件流。使用callback异步回调。 |
| [fdopenStreamSync](arkts-na-fileio-fdopenstreamsync-f.md#fdopenStreamSync) | 以同步方法基于文件描述符打开文件流。需要配合[Stream](arkts-na-fileio-stream-i.md#Stream)中的close()函数关闭文件流。 |
| [fsync](arkts-na-fileio-fsync-f.md#fsync) | 将文件系统缓存数据写入磁盘。使用Promise异步回调。 |
| [fsync](arkts-na-fileio-fsync-f.md#fsync) | 将文件系统缓存数据写入磁盘。使用callback异步回调。 |
| [fsyncSync](arkts-na-fileio-fsyncsync-f.md#fsyncSync) | 以同步方法将文件系统缓存数据写入磁盘。 |
| [listFile](arkts-na-fileio-listfile-f.md#listFile) | 默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用Promise异步回调。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFile](arkts-na-fileio-listfile-f.md#listFile) | 默认列出当前目录下所有文件名和目录名，返回文件名数组。使用callback异步回调。 |
| [listFile](arkts-na-fileio-listfile-f.md#listFile) | 默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用callback异步回调。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileSync](arkts-na-fileio-listfilesync-f.md#listFileSync) | 默认以同步方式列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExt](arkts-na-fileio-listfileext-f.md#listFileExt) | 列出目录下所有文件名，支持递归列出和自定义文件名过滤。使用Promise异步回调。 可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExtSync](arkts-na-fileio-listfileextsync-f.md#listFileExtSync) | 以同步方式列出目录下所有文件名，支持递归列出和自定义文件名过滤。 可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [lseek](arkts-na-fileio-lseek-f.md#lseek) | 调整文件偏移指针位置。 |
| [lstat](arkts-na-fileio-lstat-f.md#lstat) | 获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用Promise异步回调。 |
| [lstat](arkts-na-fileio-lstat-f.md#lstat) | 获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用callback异步回调。 |
| [lstatSync](arkts-na-fileio-lstatsync-f.md#lstatSync) | 以同步方法获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。 |
| [mkdir](arkts-na-fileio-mkdir-f.md#mkdir) | 创建单层目录，若父目录不存在则会报错。使用Promise异步回调。 |
| [mkdir](arkts-na-fileio-mkdir-f.md#mkdir) | 创建目录。使用Promise异步回调。当recursion指定为true时，可递归创建目录。 |
| [mkdir](arkts-na-fileio-mkdir-f.md#mkdir) | 创建单层目录，若父目录不存在则会报错。使用callback异步回调。 |
| [mkdir](arkts-na-fileio-mkdir-f.md#mkdir) | 创建目录，当recursion指定为true，可递归创建目录。使用callback异步回调。 |
| [mkdirSync](arkts-na-fileio-mkdirsync-f.md#mkdirSync) | 以同步方法创建单层目录，若父目录不存在则会报错。 |
| [mkdirSync](arkts-na-fileio-mkdirsync-f.md#mkdirSync) | 以同步方法创建目录。当recursion指定为true，可递归创建目录。 |
| [mkdtemp](arkts-na-fileio-mkdtemp-f.md#mkdtemp) | 创建临时目录。使用Promise异步回调。 |
| [mkdtemp](arkts-na-fileio-mkdtemp-f.md#mkdtemp) | 创建临时目录。使用callback异步回调。 |
| [mkdtempSync](arkts-na-fileio-mkdtempsync-f.md#mkdtempSync) | 以同步方法创建临时目录。 |
| [mmap](arkts-na-fileio-mmap-f.md#mmap) | 基于文件描述符或文件对象创建文件映射对象，实现文件的高效读写访问。使用Promise异步回调。 |
| [mmapSync](arkts-na-fileio-mmapsync-f.md#mmapSync) | 以同步方法基于文件描述符或文件对象创建文件映射对象，实现文件的高效读写访问。 |
| [moveDir](arkts-na-fileio-movedir-f.md#moveDir) | 移动源目录及其内容至目标路径下。使用Promise异步回调。 |
| [moveDir](arkts-na-fileio-movedir-f.md#moveDir) | 移动源目录及其内容至目标路径下。使用callback异步回调。 移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。 |
| [moveDirWithConflictFiles](arkts-na-fileio-movedirwithconflictfiles-f.md#moveDirWithConflictFiles) | Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-na-fileio-movedir-f.md#moveDir) | 移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。 |
| [moveDirWithConflictFiles](arkts-na-fileio-movedirwithconflictfiles-f.md#moveDirWithConflictFiles) | 移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。 |
| [moveDirSync](arkts-na-fileio-movedirsync-f.md#moveDirSync) | 以同步方法移动源目录及其内容至目标路径下。 |
| [moveFile](arkts-na-fileio-movefile-f.md#moveFile) | 移动文件至目标路径，支持设置冲突处理模式。使用Promise异步回调。 |
| [moveFile](arkts-na-fileio-movefile-f.md#moveFile) | 移动文件。如果移动位置存在同名文件，将强制覆盖。使用callback异步回调。 |
| [moveFile](arkts-na-fileio-movefile-f.md#moveFile) | 移动文件至目标路径，支持设置冲突处理模式。使用callback异步回调。 |
| [moveFileSync](arkts-na-fileio-movefilesync-f.md#moveFileSync) | 以同步方式移动文件至目标路径。 |
| [open](arkts-na-fileio-open-f.md#open) | 打开文件或目录，支持使用URI打开文件。使用Promise异步回调。 |
| [open](arkts-na-fileio-open-f.md#open) | 打开文件或目录，支持使用URI打开文件。使用callback异步回调。 |
| [open](arkts-na-fileio-open-f.md#open) | 打开文件或目录，可设置打开文件的选项。使用callback异步回调。 支持使用URI打开文件。 |
| [openSync](arkts-na-fileio-opensync-f.md#openSync) | 以同步方法打开文件或目录。支持使用URI打开文件。 |
| [read](arkts-na-fileio-read-f.md#read) | 从文件读取数据，返回实际读取的字节数。使用Promise异步回调。 |
| [read](arkts-na-fileio-read-f.md#read) | 从文件读取数据，返回实际读取的字节数。使用callback异步回调。 |
| [read](arkts-na-fileio-read-f.md#read) | 从文件读取数据，支持配置读取选项（如偏移位置和读取长度），返回实际读取的字节数。使用callback异步回调。 |
| [readSync](arkts-na-fileio-readsync-f.md#readSync) | 以同步方法从文件读取数据，返回实际读取的字节数。 |
| [readLines](arkts-na-fileio-readlines-f.md#readLines) | 逐行读取文件文本内容，只支持读取utf-8格式文件。使用promise异步回调。 |
| [readLines](arkts-na-fileio-readlines-f.md#readLines) | 逐行读取文件文本内容，只支持读取utf-8格式文件。使用callback异步回调。 |
| [readLines](arkts-na-fileio-readlines-f.md#readLines) | 逐行读取文件文本内容，可配置读取选项，只支持读取utf-8格式文件。使用callback异步回调。 |
| [readLinesSync](arkts-na-fileio-readlinessync-f.md#readLinesSync) | 以同步方式逐行读取文件的文本内容，只支持读取utf-8格式文件。 |
| [readText](arkts-na-fileio-readtext-f.md#readText) | 基于文本方式读取文件（即直接读取文件的文本内容）。使用Promise异步回调。 |
| [readText](arkts-na-fileio-readtext-f.md#readText) | 基于文本方式读取文件内容。使用callback异步回调。 |
| [readText](arkts-na-fileio-readtext-f.md#readText) | 基于文本方式读取文件内容，支持配置读取选项。使用callback异步回调。 |
| [readTextSync](arkts-na-fileio-readtextsync-f.md#readTextSync) | 以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。 |
| [rename](arkts-na-fileio-rename-f.md#rename) | 重命名文件或目录。使用Promise异步回调。 |
| [rename](arkts-na-fileio-rename-f.md#rename) | 重命名文件或目录。使用callback异步回调。 |
| [renameSync](arkts-na-fileio-renamesync-f.md#renameSync) | 以同步方法重命名文件或目录。 |
| [rmdir](arkts-na-fileio-rmdir-f.md#rmdir) | 删除目录及其所有子目录和文件。使用Promise异步回调。 |
| [rmdir](arkts-na-fileio-rmdir-f.md#rmdir) | 删除目录及其所有子目录和文件。使用callback异步回调。 |
| [rmdirSync](arkts-na-fileio-rmdirsync-f.md#rmdirSync) | 以同步方法删除目录及其所有子目录和文件。 |
| [stat](arkts-na-fileio-stat-f.md#stat) | 获取文件或目录详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用Promise异步回调。 |
| [stat](arkts-na-fileio-stat-f.md#stat) | 获取文件或目录的详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用callback异步回调。 |
| [statSync](arkts-na-fileio-statsync-f.md#statSync) | 以同步方法获取文件或目录详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。 |
| [symlink](arkts-na-fileio-symlink-f.md#symlink) | 基于文件路径创建符号链接。使用Promise异步回调。 |
| [symlink](arkts-na-fileio-symlink-f.md#symlink) | 基于文件路径创建符号链接。使用callback异步回调。 |
| [symlinkSync](arkts-na-fileio-symlinksync-f.md#symlinkSync) | 以同步的方法基于文件路径创建符号链接。 |
| [truncate](arkts-na-fileio-truncate-f.md#truncate) | 截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用Promise异步回调。 |
| [truncate](arkts-na-fileio-truncate-f.md#truncate) | 截断文件，删除文件内容。使用callback异步回调。 |
| [truncate](arkts-na-fileio-truncate-f.md#truncate) | 截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用callback异步回调。 |
| [truncateSync](arkts-na-fileio-truncatesync-f.md#truncateSync) | 以同步方法截断文件内容，将文件大小调整为指定长度，超出部分的内容将被删除。 |
| [unlink](arkts-na-fileio-unlink-f.md#unlink) | 删除单个文件，仅适用于文件，不可用于删除目录。使用Promise异步回调。 |
| [unlink](arkts-na-fileio-unlink-f.md#unlink) | 删除单个文件，仅适用于文件，不可用于删除目录。使用callback异步回调。 |
| [unlinkSync](arkts-na-fileio-unlinksync-f.md#unlinkSync) | 以同步方法删除单个文件，仅适用于文件，不可用于删除目录。 |
| [utimes](arkts-na-fileio-utimes-f.md#utimes) | 更改文件上次修改该文件的时间。 |
| [write](arkts-na-fileio-write-f.md#write) | 将数据写入文件，返回实际写入的字节数。使用Promise异步回调。 |
| [write](arkts-na-fileio-write-f.md#write) | 将数据写入文件，返回实际写入的字节数。使用callback异步回调。 |
| [write](arkts-na-fileio-write-f.md#write) | 将数据写入文件，支持配置写入选项（如偏移位置和写入长度），返回实际写入的字节数。使用callback异步回调。 |
| [writeSync](arkts-na-fileio-writesync-f.md#writeSync) | 以同步方法将数据写入文件，返回实际写入的字节数。 |
| [connectDfs](arkts-na-fileio-connectdfs-f.md#connectDfs) | 业务调用connectDfs接口，触发建链。如果对端设备出现异常，业务执行回调DfsListeners内 onStatus通知应用。可参考 [跨设备文件共享和访问](../../../file-management/file-access-across-devices.md)文档进行开发。 |
| [disconnectDfs](arkts-na-fileio-disconnectdfs-f.md#disconnectDfs) | 业务调用disconnectDfs接口，传入networkId参数，触发断链。 可参考[跨设备文件共享和访问](../../../file-management/file-access-across-devices.md)文档进行开发。 |
| [setxattr](arkts-na-fileio-setxattr-f.md#setxattr) | 设置文件或目录的扩展属性。使用promise异步回调。 |
| [setxattrSync](arkts-na-fileio-setxattrsync-f.md#setxattrSync) | 设置文件或目录的扩展属性。 |
| [getxattr](arkts-na-fileio-getxattr-f.md#getxattr) | 获取文件或目录的扩展属性。使用promise异步回调。 |
| [getxattrSync](arkts-na-fileio-getxattrsync-f.md#getxattrSync) | 使用同步接口获取文件或目录的扩展属性。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [TaskSignal](arkts-na-fileio-tasksignal-c.md) | 拷贝中断信号。 |
| [ReadStream](arkts-na-fileio-readstream-c.md) | 文件可读流，需要先通过[fileIo.createReadStream](arkts-na-fileio-createreadstream-f.md#createReadStream)方法来构建一个ReadStream实例。ReadStream继承自数据流基类 [stream.Readable](../../apis-arkts/arkts-apis/arkts-arkts-stream-readable-c.md#Readable)。 **规格**：ReadStream读到的数据为解码后的字符串，其编码格式当前仅支持'utf-8'。 |
| [WriteStream](arkts-na-fileio-writestream-c.md) | 文件可写流，需要先通过[fileIo.createWriteStream](arkts-na-fileio-createwritestream-f.md#createWriteStream)方法来构建一个WriteStream实例。WriteStream继承自数据流基类 [stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md#Writable)。 |
| [AtomicFile](arkts-na-fileio-atomicfile-c.md) | AtomicFile是一个用于对文件进行原子读写等操作的类。 在写操作时，通过写入临时文件，并在写入成功后将其重命名到原始文件位置来确保写入文件的完整性；而在写入失败时删除临时文件，不修改原始文件内容。 使用者可以自行调用finishWrite或failWrite来完成文件内容的写入或回滚。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DfsListeners](arkts-na-fileio-dfslisteners-i.md) | 事件监听类。创建DFSListener对象，用于监听分布式文件系统状态。 |
| [Progress](arkts-na-fileio-progress-i.md) | 拷贝进度回调数据 |
| [CopyOptions](arkts-na-fileio-copyoptions-i.md) | 拷贝进度回调监听 |
| [File](arkts-na-fileio-file-i.md) | 由open接口打开的File对象，持有文件描述符fd，提供文件锁和获取父目录等能力。 |
| [FileMapping](arkts-na-fileio-filemapping-i.md) | 文件映射对象，在调用FileMapping的方法前，需要先通过[mmap()](arkts-na-fileio-mmap-f.md#mmap)或方法[mmapSync()](arkts-na-fileio-mmapsync-f.md#mmapSync)构建一个FileMapping实例。 |
| [RandomAccessFile](arkts-na-fileio-randomaccessfile-i.md) | 随机读写文件流，提供基于偏移指针的随机读写能力。在调用RandomAccessFile的方法前，需要先通过createRandomAccessFile()方法（同步或异步）来构建一个RandomAccessFile实例。 |
| [Stat](arkts-na-fileio-stat-i.md) | 文件具体信息，包含文件大小、权限模式、访问时间、修改时间等属性。在调用Stat的方法前，需要先通过[stat()](arkts-na-fileio-stat-f.md#stat)方法（同步或异步）构建一个Stat实例。 |
| [Stream](arkts-na-fileio-stream-i.md) | 文件流，提供流式读写文件数据的能力，使用完毕后需调用close关闭。在调用Stream的方法前，需要先通过[fileIo.createStream](arkts-na-fileio-createstream-f.md#createStream)方法或者 [fileIo.fdopenStream](arkts-na-fileio-fdopenstream-f.md#fdopenStream)（同步或异步）来构建一个Stream实例。 |
| [Watcher](arkts-na-fileio-watcher-i.md) | 文件目录变化监听对象。由createWatcher接口获得。 |
| [ReaderIterator](arkts-na-fileio-readeriterator-i.md) | 文件读取迭代器。在调用ReaderIterator的方法前，需要先通过readLines方法（同步或异步）来构建一个ReaderIterator实例。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MappingMode](arkts-na-fileio-mappingmode-e.md) | 文件内存映射模式类型的枚举。 |
| [WhenceType](arkts-na-fileio-whencetype-e.md) | 枚举，文件偏移指针相对偏移位置类型，支持lseek接口使用。 |
| [LocationType](arkts-na-fileio-locationtype-e.md) | 枚举，文件位置，表示该文件是否在本地或者云端存在。 |
| [AccessModeType](arkts-na-fileio-accessmodetype-e.md) | 枚举，表示需要校验的具体权限。若不填，默认校验文件是否存在。 |
| [AccessFlagType](arkts-na-fileio-accessflagtype-e.md) | 枚举，表示需要校验的文件位置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DfsListenerCallback](arkts-na-fileio-dfslistenercallback-t.md) | DfsListener Callback function. |
| [ProgressListener](arkts-na-fileio-progresslistener-t.md) | 拷贝进度监听。 |

