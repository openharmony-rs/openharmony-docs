# fileIo

FileIO

**起始版本：** 23

**ArkTS模式：** 仅支持ArkTS-Sta，起始版本为23。

<!--Device-unnamed-declare namespace fileIo--><!--Device-unnamed-declare namespace fileIo-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [OpenMode](arkts-corefile-fileio-openmode-n.md) | open接口flags参数常量，用于指定文件打开模式（如只读、只写、读写、创建等）。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [access](arkts-corefile-fileio-access-f.md#access) | 检查文件或目录是否存在，或校验操作权限。使用Promise异步回调。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [access](arkts-corefile-fileio-access-f.md#access-1) | 检查文件或目录是否存在。使用callback异步回调。 |
| [access](arkts-corefile-fileio-access-f.md#access-2) | 检查文件或目录是否在本地，或校验操作权限。使用Promise异步回调。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync](arkts-corefile-fileio-accesssync-f.md#accesssync) | 以同步方法检查文件或目录是否存在，或校验操作权限。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync](arkts-corefile-fileio-accesssync-f.md#accesssync-1) | 以同步方法检查文件或目录是否在本地，或校验操作权限。 校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [close](arkts-corefile-fileio-close-f.md#close) | 关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用Promise异步回调。 |
| [close](arkts-corefile-fileio-close-f.md#close-1) | 关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用callback异步回调。 |
| [closeSync](arkts-corefile-fileio-closesync-f.md#closesync) | 以同步方法关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。 |
| [copy](arkts-corefile-fileio-copy-f.md#copy) | 拷贝文件或目录。使用Promise异步回调。 支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。 跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy](arkts-corefile-fileio-copy-f.md#copy-1) | 拷贝文件或者目录。使用callback异步回调。 支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。 跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy](arkts-corefile-fileio-copy-f.md#copy-2) | 拷贝文件或者目录。使用callback异步回调。 支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。 跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copyDir](arkts-corefile-fileio-copydir-f.md#copydir) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用Promise异步回调。 |
| [copyDir](arkts-corefile-fileio-copydir-f.md#copydir-1) | 复制源目录及其内容至目标路径下。使用callback异步回调。 如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部拷贝至目标目录下，目标目录下未冲突文件将继续保留。 |
| [copyDirWithConflictFiles](arkts-corefile-fileio-copydirwithconflictfiles-f.md#copydirwithconflictfiles) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。 源目录下未冲突的文件全部移动至目标目录下，目标目录下冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_HTML\_\_\_ESCAPED\_UNDERSCORE\_\_\_TAG\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_形式提供。 |
| [copyDir](arkts-corefile-fileio-copydir-f.md#copydir-2) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 |
| [copyDirWithConflictFiles](arkts-corefile-fileio-copydirwithconflictfiles-f.md#copydirwithconflictfiles-1) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 |
| [copyDirSync](arkts-corefile-fileio-copydirsync-f.md#copydirsync) | 以同步方法复制源目录至目标路径下。 |
| [copyFile](arkts-corefile-fileio-copyfile-f.md#copyfile) | 复制文件。使用Promise异步回调。 |
| [copyFile](arkts-corefile-fileio-copyfile-f.md#copyfile-1) | 复制文件，覆盖方式为完全覆盖目标文件，未覆盖部分将被裁剪。使用callback异步回调。 |
| [copyFile](arkts-corefile-fileio-copyfile-f.md#copyfile-2) | 复制文件，可设置覆盖文件的方式。使用callback异步回调。 |
| [copyFileSync](arkts-corefile-fileio-copyfilesync-f.md#copyfilesync) | 以同步方法复制文件。 |
| [createStream](arkts-corefile-fileio-createstream-f.md#createstream) | 基于文件路径创建文件流。使用Promise异步回调。需要配合[Stream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的close()函数关闭文件流。 |
| [createStream](arkts-corefile-fileio-createstream-f.md#createstream-1) | 基于文件路径创建文件流，需要配合[Stream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的close()函数关闭文件流。使用callback异步回调。 |
| [createStreamSync](arkts-corefile-fileio-createstreamsync-f.md#createstreamsync) | 以同步方法基于文件路径创建文件流。需要配合[Stream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的close()函数关闭文件流。 |
| [createRandomAccessFile](arkts-corefile-fileio-createrandomaccessfile-f.md#createrandomaccessfile) | 基于文件路径或文件对象创建RandomAccessFile对象。使用Promise异步回调。 |
| [createRandomAccessFile](arkts-corefile-fileio-createrandomaccessfile-f.md#createrandomaccessfile-1) | 基于文件路径或文件对象，以只读方式创建RandomAccessFile对象。使用callback异步回调。 |
| [createRandomAccessFile](arkts-corefile-fileio-createrandomaccessfile-f.md#createrandomaccessfile-2) | 基于文件路径或文件对象创建RandomAccessFile对象。使用callback异步回调。 |
| [createRandomAccessFileSync](arkts-corefile-fileio-createrandomaccessfilesync-f.md#createrandomaccessfilesync) | 基于文件路径或文件对象创建RandomAccessFile对象。 |
| [createReadStream](arkts-corefile-fileio-createreadstream-f.md#createreadstream) | 以同步方法打开文件可读流。 |
| [createWriteStream](arkts-corefile-fileio-createwritestream-f.md#createwritestream) | 以同步方法打开文件可写流。 |
| [createWatcher](arkts-corefile-fileio-createwatcher-f.md#createwatcher) | 创建Watcher对象，用于监听文件或目录的创建、删除、修改等变动事件。 |
| [dup](arkts-corefile-fileio-dup-f.md#dup) | 复制文件描述符，并返回对应的File对象。 |
| [fdatasync](arkts-corefile-fileio-fdatasync-f.md#fdatasync) | 实现文件内容数据同步。使用Promise异步回调。 |
| [fdatasync](arkts-corefile-fileio-fdatasync-f.md#fdatasync-1) | 实现文件内容数据同步。使用callback异步回调。 |
| [fdatasyncSync](arkts-corefile-fileio-fdatasyncsync-f.md#fdatasyncsync) | 以同步方法实现文件内容的数据同步。 |
| [fdopenStream](arkts-corefile-fileio-fdopenstream-f.md#fdopenstream) | 基于文件描述符打开文件流。使用Promise异步回调。需要配合[Stream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的close()函数关闭文件流。 |
| [fdopenStream](arkts-corefile-fileio-fdopenstream-f.md#fdopenstream-1) | 基于文件描述符打开文件流，需要配合[Stream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的close()函数关闭文件流。使用callback异步回调。 |
| [fdopenStreamSync](arkts-corefile-fileio-fdopenstreamsync-f.md#fdopenstreamsync) | 以同步方法基于文件描述符打开文件流。需要配合[Stream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_中的close()函数关闭文件流。 |
| [fsync](arkts-corefile-fileio-fsync-f.md#fsync) | 将文件系统缓存数据写入磁盘。使用Promise异步回调。 |
| [fsync](arkts-corefile-fileio-fsync-f.md#fsync-1) | 将文件系统缓存数据写入磁盘。使用callback异步回调。 |
| [fsyncSync](arkts-corefile-fileio-fsyncsync-f.md#fsyncsync) | 以同步方法将文件系统缓存数据写入磁盘。 |
| [listFile](arkts-corefile-fileio-listfile-f.md#listfile) | 默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用Promise异步回调。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFile](arkts-corefile-fileio-listfile-f.md#listfile-1) | 默认列出当前目录下所有文件名和目录名，返回文件名数组。使用callback异步回调。 |
| [listFile](arkts-corefile-fileio-listfile-f.md#listfile-2) | 默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用callback异步回调。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileSync](arkts-corefile-fileio-listfilesync-f.md#listfilesync) | 默认以同步方式列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。 可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExt](arkts-corefile-fileio-listfileext-f.md#listfileext) | 列出目录下所有文件名，支持递归列出和自定义文件名过滤。使用Promise异步回调。 可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExtSync](arkts-corefile-fileio-listfileextsync-f.md#listfileextsync) | 以同步方式列出目录下所有文件名，支持递归列出和自定义文件名过滤。 可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [lseek](arkts-corefile-fileio-lseek-f.md#lseek) | 调整文件偏移指针位置。 |
| [lstat](arkts-corefile-fileio-lstat-f.md#lstat) | 获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用Promise异步回调。 |
| [lstat](arkts-corefile-fileio-lstat-f.md#lstat-1) | 获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用callback异步回调。 |
| [lstatSync](arkts-corefile-fileio-lstatsync-f.md#lstatsync) | 以同步方法获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。 |
| [mkdir](arkts-corefile-fileio-mkdir-f.md#mkdir) | 创建单层目录，若父目录不存在则会报错。使用Promise异步回调。 |
| [mkdir](arkts-corefile-fileio-mkdir-f.md#mkdir-1) | 创建目录。使用Promise异步回调。当recursion指定为true时，可递归创建目录。 |
| [mkdir](arkts-corefile-fileio-mkdir-f.md#mkdir-2) | 创建单层目录，若父目录不存在则会报错。使用callback异步回调。 |
| [mkdir](arkts-corefile-fileio-mkdir-f.md#mkdir-3) | 创建目录，当recursion指定为true，可递归创建目录。使用callback异步回调。 |
| [mkdirSync](arkts-corefile-fileio-mkdirsync-f.md#mkdirsync) | 以同步方法创建单层目录，若父目录不存在则会报错。 |
| [mkdirSync](arkts-corefile-fileio-mkdirsync-f.md#mkdirsync-1) | 以同步方法创建目录。当recursion指定为true，可递归创建目录。 |
| [mkdtemp](arkts-corefile-fileio-mkdtemp-f.md#mkdtemp) | 创建临时目录。使用Promise异步回调。 |
| [mkdtemp](arkts-corefile-fileio-mkdtemp-f.md#mkdtemp-1) | 创建临时目录。使用callback异步回调。 |
| [mkdtempSync](arkts-corefile-fileio-mkdtempsync-f.md#mkdtempsync) | 以同步方法创建临时目录。 |
| [mmap](arkts-corefile-fileio-mmap-f.md#mmap) | 基于文件描述符或文件对象创建文件映射对象，实现文件的高效读写访问。使用Promise异步回调。 |
| [mmapSync](arkts-corefile-fileio-mmapsync-f.md#mmapsync) | 以同步方法基于文件描述符或文件对象创建文件映射对象，实现文件的高效读写访问。 |
| [moveDir](arkts-corefile-fileio-movedir-f.md#movedir) | 移动源目录及其内容至目标路径下。使用Promise异步回调。 |
| [moveDir](arkts-corefile-fileio-movedir-f.md#movedir-1) | 移动源目录及其内容至目标路径下。使用callback异步回调。 移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。 |
| [moveDirWithConflictFiles](arkts-corefile-fileio-movedirwithconflictfiles-f.md#movedirwithconflictfiles) | Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result. |
| [moveDir](arkts-corefile-fileio-movedir-f.md#movedir-2) | 移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。 |
| [moveDirWithConflictFiles](arkts-corefile-fileio-movedirwithconflictfiles-f.md#movedirwithconflictfiles-1) | 移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。 |
| [moveDirSync](arkts-corefile-fileio-movedirsync-f.md#movedirsync) | 以同步方法移动源目录及其内容至目标路径下。 |
| [moveFile](arkts-corefile-fileio-movefile-f.md#movefile) | 移动文件至目标路径，支持设置冲突处理模式。使用Promise异步回调。 |
| [moveFile](arkts-corefile-fileio-movefile-f.md#movefile-1) | 移动文件。如果移动位置存在同名文件，将强制覆盖。使用callback异步回调。 |
| [moveFile](arkts-corefile-fileio-movefile-f.md#movefile-2) | 移动文件至目标路径，支持设置冲突处理模式。使用callback异步回调。 |
| [moveFileSync](arkts-corefile-fileio-movefilesync-f.md#movefilesync) | 以同步方式移动文件至目标路径。 |
| [open](arkts-corefile-fileio-open-f.md#open) | 打开文件或目录，支持使用URI打开文件。使用Promise异步回调。 |
| [open](arkts-corefile-fileio-open-f.md#open-1) | 打开文件或目录，支持使用URI打开文件。使用callback异步回调。 |
| [open](arkts-corefile-fileio-open-f.md#open-2) | 打开文件或目录，可设置打开文件的选项。使用callback异步回调。 支持使用URI打开文件。 |
| [openSync](arkts-corefile-fileio-opensync-f.md#opensync) | 以同步方法打开文件或目录。支持使用URI打开文件。 |
| [read](arkts-corefile-fileio-read-f.md#read) | 从文件读取数据，返回实际读取的字节数。使用Promise异步回调。 |
| [read](arkts-corefile-fileio-read-f.md#read-1) | 从文件读取数据，返回实际读取的字节数。使用callback异步回调。 |
| [read](arkts-corefile-fileio-read-f.md#read-2) | 从文件读取数据，支持配置读取选项（如偏移位置和读取长度），返回实际读取的字节数。使用callback异步回调。 |
| [readSync](arkts-corefile-fileio-readsync-f.md#readsync) | 以同步方法从文件读取数据，返回实际读取的字节数。 |
| [readLines](arkts-corefile-fileio-readlines-f.md#readlines) | 逐行读取文件文本内容，只支持读取utf-8格式文件。使用promise异步回调。 |
| [readLines](arkts-corefile-fileio-readlines-f.md#readlines-1) | 逐行读取文件文本内容，只支持读取utf-8格式文件。使用callback异步回调。 |
| [readLines](arkts-corefile-fileio-readlines-f.md#readlines-2) | 逐行读取文件文本内容，可配置读取选项，只支持读取utf-8格式文件。使用callback异步回调。 |
| [readLinesSync](arkts-corefile-fileio-readlinessync-f.md#readlinessync) | 以同步方式逐行读取文件的文本内容，只支持读取utf-8格式文件。 |
| [readText](arkts-corefile-fileio-readtext-f.md#readtext) | 基于文本方式读取文件（即直接读取文件的文本内容）。使用Promise异步回调。 |
| [readText](arkts-corefile-fileio-readtext-f.md#readtext-1) | 基于文本方式读取文件内容。使用callback异步回调。 |
| [readText](arkts-corefile-fileio-readtext-f.md#readtext-2) | 基于文本方式读取文件内容，支持配置读取选项。使用callback异步回调。 |
| [readTextSync](arkts-corefile-fileio-readtextsync-f.md#readtextsync) | 以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。 |
| [rename](arkts-corefile-fileio-rename-f.md#rename) | 重命名文件或目录。使用Promise异步回调。 |
| [rename](arkts-corefile-fileio-rename-f.md#rename-1) | 重命名文件或目录。使用callback异步回调。 |
| [renameSync](arkts-corefile-fileio-renamesync-f.md#renamesync) | 以同步方法重命名文件或目录。 |
| [rmdir](arkts-corefile-fileio-rmdir-f.md#rmdir) | 删除目录及其所有子目录和文件。使用Promise异步回调。 |
| [rmdir](arkts-corefile-fileio-rmdir-f.md#rmdir-1) | 删除目录及其所有子目录和文件。使用callback异步回调。 |
| [rmdirSync](arkts-corefile-fileio-rmdirsync-f.md#rmdirsync) | 以同步方法删除目录及其所有子目录和文件。 |
| [stat](arkts-corefile-fileio-stat-f.md#stat) | 获取文件或目录详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用Promise异步回调。 |
| [stat](arkts-corefile-fileio-stat-f.md#stat-1) | 获取文件或目录的详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用callback异步回调。 |
| [statSync](arkts-corefile-fileio-statsync-f.md#statsync) | 以同步方法获取文件或目录详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。 |
| [symlink](arkts-corefile-fileio-symlink-f.md#symlink) | 基于文件路径创建符号链接。使用Promise异步回调。 |
| [symlink](arkts-corefile-fileio-symlink-f.md#symlink-1) | 基于文件路径创建符号链接。使用callback异步回调。 |
| [symlinkSync](arkts-corefile-fileio-symlinksync-f.md#symlinksync) | 以同步的方法基于文件路径创建符号链接。 |
| [truncate](arkts-corefile-fileio-truncate-f.md#truncate) | 截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用Promise异步回调。 |
| [truncate](arkts-corefile-fileio-truncate-f.md#truncate-1) | 截断文件，删除文件内容。使用callback异步回调。 |
| [truncate](arkts-corefile-fileio-truncate-f.md#truncate-2) | 截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用callback异步回调。 |
| [truncateSync](arkts-corefile-fileio-truncatesync-f.md#truncatesync) | 以同步方法截断文件内容，将文件大小调整为指定长度，超出部分的内容将被删除。 |
| [unlink](arkts-corefile-fileio-unlink-f.md#unlink) | 删除单个文件，仅适用于文件，不可用于删除目录。使用Promise异步回调。 |
| [unlink](arkts-corefile-fileio-unlink-f.md#unlink-1) | 删除单个文件，仅适用于文件，不可用于删除目录。使用callback异步回调。 |
| [unlinkSync](arkts-corefile-fileio-unlinksync-f.md#unlinksync) | 以同步方法删除单个文件，仅适用于文件，不可用于删除目录。 |
| [utimes](arkts-corefile-fileio-utimes-f.md#utimes) | 更改文件上次修改该文件的时间。 |
| [write](arkts-corefile-fileio-write-f.md#write) | 将数据写入文件，返回实际写入的字节数。使用Promise异步回调。 |
| [write](arkts-corefile-fileio-write-f.md#write-1) | 将数据写入文件，返回实际写入的字节数。使用callback异步回调。 |
| [write](arkts-corefile-fileio-write-f.md#write-2) | 将数据写入文件，支持配置写入选项（如偏移位置和写入长度），返回实际写入的字节数。使用callback异步回调。 |
| [writeSync](arkts-corefile-fileio-writesync-f.md#writesync) | 以同步方法将数据写入文件，返回实际写入的字节数。 |
| [connectDfs](arkts-corefile-fileio-connectdfs-f.md#connectdfs) | 业务调用connectDfs接口，触发建链。如果对端设备出现异常，业务执行回调DfsListeners内 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_通知应用。可参考 \_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_文档进行开发。 |
| [disconnectDfs](arkts-corefile-fileio-disconnectdfs-f.md#disconnectdfs) | 业务调用disconnectDfs接口，传入networkId参数，触发断链。 可参考\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_MD\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_文档进行开发。 |
| [setxattr](arkts-corefile-fileio-setxattr-f.md#setxattr) | 设置文件或目录的扩展属性。使用promise异步回调。 |
| [setxattrSync](arkts-corefile-fileio-setxattrsync-f.md#setxattrsync) | 设置文件或目录的扩展属性。 |
| [getxattr](arkts-corefile-fileio-getxattr-f.md#getxattr) | 获取文件或目录的扩展属性。使用promise异步回调。 |
| [getxattrSync](arkts-corefile-fileio-getxattrsync-f.md#getxattrsync) | 使用同步接口获取文件或目录的扩展属性。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [TaskSignal](arkts-corefile-fileio-tasksignal-c.md) | 拷贝中断信号。 |
| [ReadStream](arkts-corefile-fileio-readstream-c.md) | 文件可读流，需要先通过[fileIo.createReadStream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法来构建一个ReadStream实例。ReadStream继承自数据流基类 [stream.Readable]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 **规格**：ReadStream读到的数据为解码后的字符串，其编码格式当前仅支持'utf-8'。 |
| [WriteStream](arkts-corefile-fileio-writestream-c.md) | 文件可写流，需要先通过[fileIo.createWriteStream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法来构建一个WriteStream实例。WriteStream继承自数据流基类 [stream.Writable]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_。 |
| [AtomicFile](arkts-corefile-fileio-atomicfile-c.md) | AtomicFile是一个用于对文件进行原子读写等操作的类。 在写操作时，通过写入临时文件，并在写入成功后将其重命名到原始文件位置来确保写入文件的完整性；而在写入失败时删除临时文件，不修改原始文件内容。 使用者可以自行调用finishWrite或failWrite来完成文件内容的写入或回滚。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [DfsListeners](arkts-corefile-fileio-dfslisteners-i.md) | 事件监听类。创建DFSListener对象，用于监听分布式文件系统状态。 |
| [Progress](arkts-corefile-fileio-progress-i.md) | 拷贝进度回调数据 |
| [CopyOptions](arkts-corefile-fileio-copyoptions-i.md) | 拷贝进度回调监听 |
| [File](arkts-corefile-fileio-file-i.md) | 由open接口打开的File对象，持有文件描述符fd，提供文件锁和获取父目录等能力。 |
| [FileMapping](arkts-corefile-fileio-filemapping-i.md) | 文件映射对象，在调用FileMapping的方法前，需要先通过[mmap()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_或方法[mmapSync()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_构建一个FileMapping实例。 |
| [RandomAccessFile](arkts-corefile-fileio-randomaccessfile-i.md) | 随机读写文件流，提供基于偏移指针的随机读写能力。在调用RandomAccessFile的方法前，需要先通过createRandomAccessFile()方法（同步或异步）来构建一个RandomAccessFile实例。 |
| [Stat](arkts-corefile-fileio-stat-i.md) | 文件具体信息，包含文件大小、权限模式、访问时间、修改时间等属性。在调用Stat的方法前，需要先通过[stat()]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法（同步或异步）构建一个Stat实例。 |
| [Stream](arkts-corefile-fileio-stream-i.md) | 文件流，提供流式读写文件数据的能力，使用完毕后需调用close关闭。在调用Stream的方法前，需要先通过[fileIo.createStream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_0\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_方法或者 [fileIo.fdopenStream]\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_JSDOC\_\_\_ESCAPED\_UNDERSCORE\_\_\_LINK\_\_\_ESCAPED\_UNDERSCORE\_\_\_DESC\_\_\_ESCAPED\_UNDERSCORE\_\_\_USD\_\_\_ESCAPED\_UNDERSCORE\_\_\_1\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_\_\_\_ESCAPED\_UNDERSCORE\_\_\_（同步或异步）来构建一个Stream实例。 |
| [Watcher](arkts-corefile-fileio-watcher-i.md) | 文件目录变化监听对象。由createWatcher接口获得。 |
| [ReaderIterator](arkts-corefile-fileio-readeriterator-i.md) | 文件读取迭代器。在调用ReaderIterator的方法前，需要先通过readLines方法（同步或异步）来构建一个ReaderIterator实例。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [MappingMode](arkts-corefile-fileio-mappingmode-e.md) | 文件内存映射模式类型的枚举。 |
| [WhenceType](arkts-corefile-fileio-whencetype-e.md) | 枚举，文件偏移指针相对偏移位置类型，支持lseek接口使用。 |
| [LocationType](arkts-corefile-fileio-locationtype-e.md) | 枚举，文件位置，表示该文件是否在本地或者云端存在。 |
| [AccessModeType](arkts-corefile-fileio-accessmodetype-e.md) | 枚举，表示需要校验的具体权限。若不填，默认校验文件是否存在。 |
| [AccessFlagType](arkts-corefile-fileio-accessflagtype-e.md) | 枚举，表示需要校验的文件位置。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [DfsListenerCallback](arkts-corefile-fileio-dfslistenercallback-t.md) | DfsListener Callback function. |
| [ProgressListener](arkts-corefile-fileio-progresslistener-t.md) | 拷贝进度监听。 |

