# @ohos.file.fs

FileIO

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [fileIo](arkts-corefile-fileio-n.md) | FileIO<br/> |

### 函数

| 名称 | 说明 |
| --- | --- |
| [access](arkts-corefile-file-fs-access-f.md#access-1) | 检查文件或目录是否存在，或校验操作权限，使用promise异步回调。<br/><br/>校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。<br/> |
| [access](arkts-corefile-file-fs-access-f.md#access-2) | 检查文件或目录是否存在，使用callback异步回调。<br/> |
| [access](arkts-corefile-file-fs-access-f.md#access-3) | 检查文件或目录是否在本地，或校验操作权限，使用promise异步回调。<br/><br/>校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。<br/> |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md#accessSync-1) | 以同步方法检查文件或目录是否存在，或校验操作权限。<br/><br/>校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。<br/> |
| [accessSync](arkts-corefile-file-fs-accesssync-f.md#accessSync-2) | 以同步方法检查文件或目录是否在本地，或校验操作权限。<br/><br/>校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。<br/> |
| [close](arkts-corefile-file-fs-close-f.md#close-1) | 关闭文件或目录，使用promise异步回调。<br/> |
| [close](arkts-corefile-file-fs-close-f.md#close-2) | 关闭文件或目录，使用callback异步回调。<br/> |
| [closeSync](arkts-corefile-file-fs-closesync-f.md#closeSync-1) | 以同步方法关闭文件或目录。<br/> |
| [connectDfs](arkts-corefile-file-fs-connectdfs-f.md#connectDfs-1) | 业务调用connectDfs接口，触发建链。如果对端设备出现异常，业务执行回调DfsListeners内<br/>[onStatus](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#onstatus12)通知应用。<br/> |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-1) | 拷贝文件或目录，使用promise异步回调。<br/><br/>支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。<br/><br/>跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。<br/> |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-2) | 拷贝文件或者目录，使用callback异步回调。<br/><br/>支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。<br/><br/>跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。<br/> |
| [copy](arkts-corefile-file-fs-copy-f.md#copy-3) | 拷贝文件或者目录，使用callback异步回调。<br/><br/>支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。<br/><br/>跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。<br/> |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copyDir-1) | 复制源目录至目标路径下，使用promise异步回调。<br/> |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copyDir-2) | 复制源目录至目标路径下，使用callback异步回调。<br/> |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copyDir-3) | 复制源目录至目标路径下，使用callback异步回调。<br/><br/>如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部移动至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array\&lt;<br/>[ConflictFiles](arkts-corefile-conflictfiles-i.md#ConflictFiles)&gt;形式提供。<br/> |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copyDir-4) | 复制源目录至目标路径下，可设置复制模式。使用callback异步回调。<br/> |
| [copyDir](arkts-corefile-file-fs-copydir-f.md#copyDir-5) | 复制源目录至目标路径下，可设置复制模式。使用callback异步回调。<br/> |
| [copyDirSync](arkts-corefile-file-fs-copydirsync-f.md#copyDirSync-1) | 以同步方法复制源目录至目标路径下。<br/> |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyFile-1) | 复制文件，使用promise异步回调。<br/> |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyFile-2) | 复制文件，覆盖方式为完全覆盖目标文件，未覆盖部分将被裁切。使用callback异步回调。<br/> |
| [copyFile](arkts-corefile-file-fs-copyfile-f.md#copyFile-3) | 复制文件，可设置覆盖文件的方式，使用callback异步回调。<br/> |
| [copyFileSync](arkts-corefile-file-fs-copyfilesync-f.md#copyFileSync-1) | 以同步方法复制文件。<br/> |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createRandomAccessFile-1) | 基于文件路径或文件对象创建RandomAccessFile对象，使用promise异步回调。<br/> |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createRandomAccessFile-2) | 基于文件路径或文件对象，以只读方式创建RandomAccessFile对象，使用callback异步回调。<br/> |
| [createRandomAccessFile](arkts-corefile-file-fs-createrandomaccessfile-f.md#createRandomAccessFile-3) | 基于文件路径或文件对象创建RandomAccessFile对象，使用callback异步回调。<br/> |
| [createRandomAccessFileSync](arkts-corefile-file-fs-createrandomaccessfilesync-f.md#createRandomAccessFileSync-1) | 基于文件路径或文件对象创建RandomAccessFile对象。<br/> |
| [createReadStream](arkts-corefile-file-fs-createreadstream-f.md#createReadStream-1) | 以同步方法打开文件可读流。<br/> |
| [createStream](arkts-corefile-file-fs-createstream-f.md#createStream-1) | 基于文件路径创建文件流，使用promise异步回调。需要配合[Stream](arkts-corefile-stream-i.md#Stream)中的close()函数关闭文件流。<br/> |
| [createStream](arkts-corefile-file-fs-createstream-f.md#createStream-2) | 基于文件路径创建文件流，使用callback异步回调。需要配合[Stream](arkts-corefile-stream-i.md#Stream)中的close()函数关闭文件流。<br/> |
| [createStreamSync](arkts-corefile-file-fs-createstreamsync-f.md#createStreamSync-1) | 以同步方法基于文件路径创建文件流。需要配合[Stream](arkts-corefile-stream-i.md#Stream)中的close()函数关闭文件流。<br/> |
| [createWatcher](arkts-corefile-file-fs-createwatcher-f.md#createWatcher-1) | 创建Watcher对象，监听文件或目录变动。<br/> |
| [createWriteStream](arkts-corefile-file-fs-createwritestream-f.md#createWriteStream-1) | 以同步方法打开文件可写流。<br/> |
| [disconnectDfs](arkts-corefile-file-fs-disconnectdfs-f.md#disconnectDfs-1) | 业务调用disconnectDfs接口，传入networkId参数，触发断链。<br/> |
| [dup](arkts-corefile-file-fs-dup-f.md#dup-1) | 复制文件描述符，并返回对应的File对象。<br/> |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync-1) | 实现文件内容数据同步，使用promise异步回调。<br/> |
| [fdatasync](arkts-corefile-file-fs-fdatasync-f.md#fdatasync-2) | 实现文件内容数据同步，使用callback异步回调。<br/> |
| [fdatasyncSync](arkts-corefile-file-fs-fdatasyncsync-f.md#fdatasyncSync-1) | 以同步方法实现文件内容的数据同步。<br/> |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md#fdopenStream-1) | 基于文件描述符打开文件流，使用promise异步回调。需要配合[Stream](arkts-corefile-stream-i.md#Stream)中的close()函数关闭文件流。<br/> |
| [fdopenStream](arkts-corefile-file-fs-fdopenstream-f.md#fdopenStream-2) | 基于文件描述符打开文件流，使用callback异步回调。需要配合[Stream](arkts-corefile-stream-i.md#Stream)中的close()函数关闭文件流。<br/> |
| [fdopenStreamSync](arkts-corefile-file-fs-fdopenstreamsync-f.md#fdopenStreamSync-1) | 以同步方法基于文件描述符打开文件流。需要配合[Stream](arkts-corefile-stream-i.md#Stream)中的close()函数关闭文件流。<br/> |
| [fsync](arkts-corefile-file-fs-fsync-f.md#fsync-1) | 将文件系统缓存数据写入磁盘，使用promise异步回调。<br/> |
| [fsync](arkts-corefile-file-fs-fsync-f.md#fsync-2) | 将文件系统缓存数据写入磁盘，使用callback异步回调。<br/> |
| [fsyncSync](arkts-corefile-file-fs-fsyncsync-f.md#fsyncSync-1) | 以同步方法将文件系统缓存数据写入磁盘。<br/> |
| [getxattr](arkts-corefile-file-fs-getxattr-f.md#getxattr-1) | 获取文件或目录的扩展属性。使用promise异步回调。<br/> |
| [getxattrSync](arkts-corefile-file-fs-getxattrsync-f.md#getxattrSync-1) | 使用同步接口获取文件或目录的扩展属性。<br/> |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listFile-1) | 默认列出当前目录下所有文件名和目录名。支持过滤。使用promise异步回调。<br/><br/>可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。<br/> |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listFile-2) | 默认列出当前目录下所有文件名和目录名。支持过滤。使用callback异步回调。<br/><br/>可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。<br/> |
| [listFile](arkts-corefile-file-fs-listfile-f.md#listFile-3) | 默认列出当前目录下所有文件名和目录名。支持过滤。使用callback异步回调。<br/><br/>可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。<br/> |
| [listFileExt](arkts-corefile-file-fs-listfileext-f.md#listFileExt-1) | 列出目录下所有文件名，使用Promise异步回调。<br/>该接口支持通过自定义过滤函数对文件名进行过滤。<br/>可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。<br/> |
| [listFileExtSync](arkts-corefile-file-fs-listfileextsync-f.md#listFileExtSync-1) | 以同步方法列出目录下所有文件名，支持通过自定义过滤函数对文件名进行过滤。<br/>可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。<br/> |
| [listFileSync](arkts-corefile-file-fs-listfilesync-f.md#listFileSync-1) | 默认以同步方式列出当前目录下所有文件名和目录名。支持过滤。<br/><br/>可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。<br/> |
| [lseek](arkts-corefile-file-fs-lseek-f.md#lseek-1) | 调整文件偏移指针位置。<br/> |
| [lstat](arkts-corefile-file-fs-lstat-f.md#lstat-1) | 获取符号链接文件信息，使用promise异步回调。<br/> |
| [lstat](arkts-corefile-file-fs-lstat-f.md#lstat-2) | 获取符号链接文件信息，使用callback异步回调。<br/> |
| [lstatSync](arkts-corefile-file-fs-lstatsync-f.md#lstatSync-1) | 以同步方法获取符号链接文件信息。<br/> |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-1) | 创建目录，使用promise异步回调。<br/> |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-2) | 创建目录，使用promise异步回调。当recursion指定为true时，可递归创建目录。<br/> |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-3) | 创建目录，使用callback异步回调。<br/> |
| [mkdir](arkts-corefile-file-fs-mkdir-f.md#mkdir-4) | 创建目录，使用callback异步回调。当recursion指定为true，可递归创建目录。<br/> |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md#mkdirSync-1) | 以同步方法创建目录。<br/> |
| [mkdirSync](arkts-corefile-file-fs-mkdirsync-f.md#mkdirSync-2) | 以同步方法创建目录。当recursion指定为true，可递归创建目录。<br/> |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp-1) | 创建临时目录，使用promise异步回调。<br/> |
| [mkdtemp](arkts-corefile-file-fs-mkdtemp-f.md#mkdtemp-2) | 创建临时目录，使用callback异步回调。<br/> |
| [mkdtempSync](arkts-corefile-file-fs-mkdtempsync-f.md#mkdtempSync-1) | 以同步的方法创建临时目录。<br/> |
| [mmap](arkts-corefile-file-fs-mmap-f.md#mmap-1) | 基于文件描述符或文件对象创建文件映射对象，使用promise异步回调。将文件内容映射到内存，以实现文件的高效读写访问。<br/>注意：读写模式（MappingMode.READ_WRITE）下，若映射范围超过原始文件大小，将自动扩展文件大小。<br/>&gt; **说明**<br/>&gt; 注意：在读写模式（MappingMode.READ_WRITE）下，如果映射范围超过原始文件大小，则文件大小<br/>&gt; 将自动展开。<br/> |
| [mmapSync](arkts-corefile-file-fs-mmapsync-f.md#mmapSync-1) | 以同步方法基于文件描述符或文件对象创建文件映射对象。将文件内容映射到内存，以实现文件的高效读写访问。<br/>注意：读写模式（MappingMode.READ_WRITE）下，若映射范围超过原始文件大小，将自动扩展文件大小。<br/> |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#moveDir-1) | 移动源目录至目标路径下，使用promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#moveDir-2) | Moves the source directory to the destination directory. This API uses an asynchronous callback to return the result.<br/> |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#moveDir-3) | 移动源目录至目标路径下。使用callback异步回调。<br/><br/>移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#moveDir-4) | 移动源目录至目标路径下，支持设置移动模式。使用callback异步回调。<br/> |
| [moveDir](arkts-corefile-file-fs-movedir-f.md#moveDir-5) | 移动源目录至目标路径下，支持设置移动模式。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [moveDirSync](arkts-corefile-file-fs-movedirsync-f.md#moveDirSync-1) | 以同步方法移动源目录至目标路径下。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#moveFile-1) | 移动文件，使用promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#moveFile-2) | 移动文件。如果移动位置存在同名文件，将强制覆盖。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [moveFile](arkts-corefile-file-fs-movefile-f.md#moveFile-3) | 移动文件，支持设置移动模式。使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [moveFileSync](arkts-corefile-file-fs-movefilesync-f.md#moveFileSync-1) | 以同步方式移动文件。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [open](arkts-corefile-file-fs-open-f.md#open-1) | 打开文件或目录，使用promise异步回调。支持使用URI打开文件。<br/> |
| [open](arkts-corefile-file-fs-open-f.md#open-2) | 打开文件或目录，使用callback异步回调。支持使用URI打开文件。<br/> |
| [open](arkts-corefile-file-fs-open-f.md#open-3) | 打开文件或目录，可设置打开文件的选项。使用callback异步回调。<br/><br/>支持使用URI打开文件。<br/> |
| [openSync](arkts-corefile-file-fs-opensync-f.md#openSync-1) | 以同步方法打开文件或目录。支持使用URI打开文件。<br/> |
| [read](arkts-corefile-file-fs-read-f.md#read-1) | 读取文件数据，使用promise异步回调。<br/> |
| [read](arkts-corefile-file-fs-read-f.md#read-2) | 从文件读取数据，使用callback异步回调。<br/> |
| [read](arkts-corefile-file-fs-read-f.md#read-3) | 从文件读取数据，使用callback异步回调。<br/> |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readLines-1) | 逐行读取文件文本内容，使用promise异步回调。只支持读取utf-8格式文件。<br/> |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readLines-2) | 逐行读取文件文本内容，使用callback异步回调，只支持读取utf-8格式文件。<br/> |
| [readLines](arkts-corefile-file-fs-readlines-f.md#readLines-3) | 逐行读取文件文本内容，使用callback异步回调，只支持读取utf-8格式文件。<br/> |
| [readLinesSync](arkts-corefile-file-fs-readlinessync-f.md#readLinesSync-1) | 以同步方式逐行读取文件的文本内容。<br/> |
| [readSync](arkts-corefile-file-fs-readsync-f.md#readSync-1) | 以同步方法从文件读取数据。<br/> |
| [readText](arkts-corefile-file-fs-readtext-f.md#readText-1) | 基于文本方式读取文件（即直接读取文件的文本内容），使用promise异步回调。<br/> |
| [readText](arkts-corefile-file-fs-readtext-f.md#readText-2) | 基于文本方式读取文件内容，使用callback异步回调。<br/> |
| [readText](arkts-corefile-file-fs-readtext-f.md#readText-3) | 基于文本方式读取文件内容，使用callback异步回调。<br/> |
| [readTextSync](arkts-corefile-file-fs-readtextsync-f.md#readTextSync-1) | 以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。<br/> |
| [rename](arkts-corefile-file-fs-rename-f.md#rename-1) | 重命名文件或目录，使用promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [rename](arkts-corefile-file-fs-rename-f.md#rename-2) | 重命名文件或目录，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [renameSync](arkts-corefile-file-fs-renamesync-f.md#renameSync-1) | 以同步方法重命名文件或目录。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口不支持在分布式文件路径下操作。<br/> |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md#rmdir-1) | 删除目录及其所有子目录和文件，使用promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口支持删除单个文件，但不推荐使用此方法删除单个文件，推荐使用unlink接口删除单个文件。<br/> |
| [rmdir](arkts-corefile-file-fs-rmdir-f.md#rmdir-2) | 删除目录及其所有子目录和文件，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口支持删除单个文件，但不推荐使用此方法删除单个文件，推荐使用unlink接口删除单个文件。<br/> |
| [rmdirSync](arkts-corefile-file-fs-rmdirsync-f.md#rmdirSync-1) | 以同步方法删除目录及其所有子目录和文件。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 该接口支持删除单个文件，但不推荐使用此方法删除单个文件，推荐使用unlinkSync接口删除单个文件。<br/> |
| [setxattr](arkts-corefile-file-fs-setxattr-f.md#setxattr-1) | 设置文件或目录的扩展属性。使用promise异步回调。<br/> |
| [setxattrSync](arkts-corefile-file-fs-setxattrsync-f.md#setxattrSync-1) | 设置文件或目录的扩展属性。<br/> |
| [stat](arkts-corefile-file-fs-stat-f.md#stat-1) | 获取文件或目录详细属性信息，使用promise异步回调。<br/> |
| [stat](arkts-corefile-file-fs-stat-f.md#stat-2) | 获取文件或目录的详细属性信息，使用callback异步回调。<br/> |
| [statSync](arkts-corefile-file-fs-statsync-f.md#statSync-1) | 以同步方法获取文件或目录详细属性信息。<br/> |
| [symlink](arkts-corefile-file-fs-symlink-f.md#symlink-1) | 基于文件路径创建符号链接，使用promise异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 11开始，不支持三方应用使用。<br/> |
| [symlink](arkts-corefile-file-fs-symlink-f.md#symlink-2) | 基于文件路径创建符号链接，使用callback异步回调。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 11开始，不支持三方应用使用。<br/> |
| [symlinkSync](arkts-corefile-file-fs-symlinksync-f.md#symlinkSync-1) | 以同步的方法基于文件路径创建符号链接。<br/><br/>&gt; **说明：**<br/>&gt;<br/>&gt; 从API version 11开始，不支持三方应用使用。<br/> |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-1) | 截断文件，使用promise异步回调。<br/> |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-2) | 截断文件，使用callback异步回调。<br/> |
| [truncate](arkts-corefile-file-fs-truncate-f.md#truncate-3) | 截断文件，使用callback异步回调。<br/> |
| [truncateSync](arkts-corefile-file-fs-truncatesync-f.md#truncateSync-1) | 以同步方法截断文件内容。<br/> |
| [unlink](arkts-corefile-file-fs-unlink-f.md#unlink-1) | 删除单个文件，使用promise异步回调。<br/> |
| [unlink](arkts-corefile-file-fs-unlink-f.md#unlink-2) | 删除文件，使用callback异步回调。<br/> |
| [unlinkSync](arkts-corefile-file-fs-unlinksync-f.md#unlinkSync-1) | 以同步方法删除文件。<br/> |
| [utimes](arkts-corefile-file-fs-utimes-f.md#utimes-1) | 更改文件上次修改该文件的时间。<br/> |
| [write](arkts-corefile-file-fs-write-f.md#write-1) | 将数据写入文件，使用promise异步回调。<br/> |
| [write](arkts-corefile-file-fs-write-f.md#write-2) | 将数据写入文件，使用callback异步回调。<br/> |
| [write](arkts-corefile-file-fs-write-f.md#write-3) | 将数据写入文件，使用callback异步回调。<br/> |
| [writeSync](arkts-corefile-file-fs-writesync-f.md#writeSync-1) | 以同步方法将数据写入文件。<br/> |

### 类

| 名称 | 说明 |
| --- | --- |
| [AtomicFile](arkts-corefile-atomicfile-c.md) | AtomicFile是一个用于对文件进行原子读写操作的类。<br/><br/>在写操作时，通过写入临时文件，并在写入成功后将其重命名到原始文件位置来确保写入文件的完整性；而在写入失败时删除临时文件，不修改原始文件内容。<br/><br/>使用者可以自行调用finishWrite或failWrite来完成文件内容的写入或回滚。<br/> |
| [ReadStream](arkts-corefile-readstream-c.md) | 文件可读流，需要先通过fileIo.createReadStream方法来构建一个ReadStream实例。ReadStream继承自数据流基类stream.Readable。<br/>ReadStream读到的数据为解码后的字符串，其编码格式当前仅支持'utf-8'。<br/> |
| [TaskSignal](arkts-corefile-tasksignal-c.md) | 拷贝中断信号。<br/> |
| [WriteStream](arkts-corefile-writestream-c.md) | 文件可写流，需要先通过<br/>[fileIo.createWriteStream](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatewritestream12)方法来构建一<br/>个WriteStream实例。WriteStream继承自数据流基类[stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md#Writable)。<br/> |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConflictFiles](arkts-corefile-conflictfiles-i.md) | 冲突文件信息，支持copyDir及moveDir接口使用。<br/> |
| [CopyOptions](arkts-corefile-copyoptions-i.md) | 拷贝进度回调监听<br/> |
| [DfsListeners](arkts-corefile-dfslisteners-i.md) | 事件监听类。创建DFSListener对象，用于监听分布式文件系统状态。<br/> |
| [File](arkts-corefile-file-i.md) | 由open接口打开的File对象。<br/> |
| [FileFilter](arkts-corefile-filefilter-i.md) | 文件名过滤器，支持listFileExt接口使用。<br/> |
| [FileMapping](arkts-corefile-filemapping-i.md) | 文件映射对象，在调用FileMapping的方法前，需要先通过mmap()方法（同步或异步）构建一个FileMapping实例。<br/> |
| [Filter](arkts-corefile-filter-i.md) | 文件过滤配置项，支持listFile接口使用。<br/> |
| [ListFileExtOptions](arkts-corefile-listfileextoptions-i.md) | 可选项类型，支持listFileExt接口使用自定义过滤规则。<br/> |
| [ListFileOptions](arkts-corefile-listfileoptions-i.md) | 可选项类型，支持ListFile接口使用。<br/> |
| [Options](arkts-corefile-options-i.md) | 可选项类型，支持readLines接口使用。<br/> |
| [Progress](arkts-corefile-progress-i.md) | 拷贝进度回调数据<br/> |
| [RandomAccessFile](arkts-corefile-randomaccessfile-i.md) | 随机读写文件流。在调用RandomAccessFile的方法前，需要先通过createRandomAccessFile()方法（同步或异步）来构建一个RandomAccessFile实例。<br/> |
| [RandomAccessFileOptions](arkts-corefile-randomaccessfileoptions-i.md) | 可选项类型，支持 createRandomAccessFile 接口使用。<br/> |
| [ReadOptions](arkts-corefile-readoptions-i.md) | 可选项类型，支持read接口使用。<br/> |
| [ReadStreamOptions](arkts-corefile-readstreamoptions-i.md) | 可选项类型，支持 createReadStream 接口使用。<br/> |
| [ReadTextOptions](arkts-corefile-readtextoptions-i.md) | 可选项类型，支持readText接口使用，ReadTextOptions继承至[ReadOptions](arkts-corefile-readoptions-i.md#ReadOptions)。<br/> |
| [ReaderIterator](arkts-corefile-readeriterator-i.md) | 文件读取迭代器。在调用ReaderIterator的方法前，需要先通过readLines方法（同步或异步）来构建一个ReaderIterator实例。<br/> |
| [ReaderIteratorResult](arkts-corefile-readeriteratorresult-i.md) | 文件读取迭代器返回结果，支持ReaderIterator接口使用。<br/> |
| [Stat](arkts-corefile-stat-i.md) | 文件具体信息，在调用Stat的方法前，需要先通过[stat()](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiostat)方法（同步或异步）构建一个<br/>Stat实例。<br/> |
| [Stream](arkts-corefile-stream-i.md) | 文件流，在调用Stream的方法前，需要先通过<br/>[fileIo.createStream](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatestream)方法或者<br/>[fileIo.fdopenStream](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiofdopenstream)（同步或异步）来构建一个Stream<br/>实例。<br/> |
| [WatchEvent](arkts-corefile-watchevent-i.md) | 事件类<br/> |
| [WatchEventListener](arkts-corefile-watcheventlistener-i.md) | <br/>事件监听类。<br/> |
| [Watcher](arkts-corefile-watcher-i.md) | 文件目录变化监听对象。由createWatcher接口获得。<br/> |
| [WriteOptions](arkts-corefile-writeoptions-i.md) | 可选项类型，支持write接口使用，WriteOptions继承至[Options](arkts-corefile-options-i.md#Options)。<br/> |
| [WriteStreamOptions](arkts-corefile-writestreamoptions-i.md) | 可选项类型，支持 createWriteStream 接口使用。<br/> |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessFlagType](arkts-corefile-accessflagtype-e.md) | 枚举，表示需要校验的文件位置。<br/> |
| [AccessModeType](arkts-corefile-accessmodetype-e.md) | 枚举，表示需要校验的具体权限。若不填，默认校验文件是否存在。<br/> |
| [LocationType](arkts-corefile-locationtype-e.md) | 枚举，文件位置，表示该文件是否在本地或者云端存在。<br/> |
| [MappingMode](arkts-corefile-mappingmode-e.md) | 枚举，文件内存映射模式类型，支持mmap接口使用。<br/> |
| [WhenceType](arkts-corefile-whencetype-e.md) | 枚举，文件偏移指针相对偏移位置类型，支持lseek接口使用。<br/> |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ProgressListener](arkts-corefile-progresslistener-t.md) | 拷贝进度监听。<br/> |

