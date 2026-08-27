# @ohos.file.fs(@ohos.file.fs (文件管理))

本模块是Core File Kit的核心模块，提供基础文件操作API，用于对应用沙箱内的文件和目录进行创建、打开、读写、拷贝、移动、删除、查询属性等操作。模块提供了多种文件访问模式，开发者可根据场景选择：基于文件描述符（fd）：通过open获取File对象，再使用read/write进行读写，适用于通用文件读写场景。 基于流（Stream）：通过createStream/fdopenStream创建Stream，或通过createReadStream/createWriteStream创建ReadStream/WriteStream，适用于流式数据处理或大文件分块读写等场景。 基于RandomAccessFile：通过createRandomAccessFile创建RandomAccessFile对象，支持独立的偏移指针和随机读写，适用于需要频繁跳转读写位置的场景。 此外，模块还提供文件监听（Watcher）、内存映射（FileMapping）、安全原子写入（AtomicFile）等其他能力。

> **使用说明：**
使用该功能模块对文件/目录进行操作前，需要先获取其应用沙箱路径，获取沙箱路径的方式及其接口用法可参考： [应用上下文Context-获取应用文件路径](../../../application-models/application-context-stage.md#获取应用文件路径)。指向资源的字符串称为URI。对于只支持沙箱路径作为入参的接口，可以使用构造fileUri对象并获取其沙箱路径的属性的方式将URI转换为沙箱路径，然后使用文件接口。 URI定义及其转换方式请参考：[文件URI](../../../reference/apis-core-file-kit/js-apis-file-fileuri.md)。

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [fileIo(@ohos.file.fs (文件管理))](arkts-corefile-fileio-n.md) | 本模块是Core File Kit的核心模块，提供基础文件操作API，用于对应用沙箱内的文件和目录进行创建、打开、读写、拷贝、移动、删除、查询属性等操作。模块提供了多种文件访问模式，开发者可根据场景选择：基于文件描述符（fd）：通过open获取File对象，再使用read/write进行读写，适用于通用文件读写场景。 基于流（Stream）：通过createStream/fdopenStream创建Stream，或通过createReadStream/createWriteStream创建ReadStream/WriteStream，适用于流式数据处理或大文件分块读写等场景。 基于RandomAccessFile：通过createRandomAccessFile创建RandomAccessFile对象，支持独立的偏移指针和随机读写，适用于需要频繁跳转读写位置的场景。 此外，模块还提供文件监听（Watcher）、内存映射（FileMapping）、安全原子写入（AtomicFile）等其他能力。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [access(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-access-f.md) | 检查文件或目录是否存在，或校验操作权限。使用Promise异步回调。校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [access(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-access-f.md) | 检查文件或目录是否存在。使用callback异步回调。 |
| [access(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-access-f.md) | 检查文件或目录是否在本地，或校验操作权限。使用Promise异步回调。校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-accesssync-f.md) | 以同步方法检查文件或目录是否存在，或校验操作权限。校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [accessSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-accesssync-f.md) | 以同步方法检查文件或目录是否在本地，或校验操作权限。校验读、写或读写权限不通过会抛出13900012（Permission denied）错误码。 |
| [close(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-close-f.md) | 关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用Promise异步回调。 |
| [close(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-close-f.md) | 关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。使用callback异步回调。 |
| [closeSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-closesync-f.md) | 以同步方法关闭文件或目录，关闭后文件描述符fd失效，不可再用于读写等操作。 |
| [connectDfs(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-connectdfs-f.md) | 业务调用connectDfs接口，触发建链。如果对端设备出现异常，业务执行回调DfsListeners内 [onStatus](../../../reference/apis-core-file-kit/js-apis-file-fs.md#onstatus12)通知应用。 |
| [copy(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copy-f.md) | 拷贝文件或目录。使用Promise异步回调。支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copy-f.md) | 拷贝文件或者目录。使用callback异步回调。支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copy(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copy-f.md) | 拷贝文件或者目录。使用callback异步回调。支持跨设备拷贝。强制覆盖拷贝。入参支持文件或目录URI。跨端拷贝时，最多同时存在10个拷贝任务；单次拷贝的文件数量不得超过500个。 |
| [copyDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copydir-f.md) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用Promise异步回调。 |
| [copyDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copydir-f.md) | 复制源目录及其内容至目标路径下。使用callback异步回调。 |
| [copyDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copydir-f.md) | 复制源目录至目标路径下。使用callback异步回调。如果目标目录下有与源目录名冲突的目录，且冲突目录下有同名文件，则抛出异常。源目录下未冲突的文件全部拷贝至目标目录下，目标目录下未冲突文件将继续保留，且冲突文件信息将在抛出异常的data属性中以Array\&lt;[ConflictFiles](arkts-corefile-file-fs-conflictfiles-i.md)&gt;形式提供。 |
| [copyDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copydir-f.md) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 |
| [copyDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copydir-f.md) | 复制源目录及其内容至目标路径下，可设置冲突处理模式。使用callback异步回调。 |
| [copyDirSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copydirsync-f.md) | 以同步方法复制源目录至目标路径下。 |
| [copyFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copyfile-f.md) | 复制文件。使用Promise异步回调。 |
| [copyFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copyfile-f.md) | 复制文件，覆盖方式为完全覆盖目标文件，未覆盖部分将被裁剪。使用callback异步回调。 |
| [copyFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copyfile-f.md) | 复制文件，可设置覆盖文件的方式。使用callback异步回调。 |
| [copyFileSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copyfilesync-f.md) | 以同步方法复制文件。 |
| [createRandomAccessFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createrandomaccessfile-f.md) | 基于文件路径或文件对象创建RandomAccessFile对象。使用Promise异步回调。 |
| [createRandomAccessFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createrandomaccessfile-f.md) | 基于文件路径或文件对象，以只读方式创建RandomAccessFile对象。使用callback异步回调。 |
| [createRandomAccessFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createrandomaccessfile-f.md) | 基于文件路径或文件对象创建RandomAccessFile对象。使用callback异步回调。 |
| [createRandomAccessFileSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createrandomaccessfilesync-f.md) | 基于文件路径或文件对象创建RandomAccessFile对象。 |
| [createReadStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createreadstream-f.md) | 以同步方法打开文件可读流。 |
| [createStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createstream-f.md) | 基于文件路径创建文件流。使用Promise异步回调。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [createStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createstream-f.md) | 基于文件路径创建文件流，需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。使用callback异步回调。 |
| [createStreamSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createstreamsync-f.md) | 以同步方法基于文件路径创建文件流。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [createWatcher(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createwatcher-f.md) | 创建Watcher对象，用于监听文件或目录的创建、删除、修改等变动事件。 |
| [createWriteStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-createwritestream-f.md) | 以同步方法打开文件可写流。 |
| [disconnectDfs(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-disconnectdfs-f.md) | 业务调用disconnectDfs接口，传入networkId参数，触发断链。 |
| [dup(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-dup-f.md) | 复制文件描述符，并返回对应的File对象。 |
| [fdatasync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fdatasync-f.md) | 实现文件内容数据同步。使用Promise异步回调。 |
| [fdatasync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fdatasync-f.md) | 实现文件内容数据同步。使用callback异步回调。 |
| [fdatasyncSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fdatasyncsync-f.md) | 以同步方法实现文件内容的数据同步。 |
| [fdopenStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fdopenstream-f.md) | 基于文件描述符打开文件流。使用Promise异步回调。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [fdopenStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fdopenstream-f.md) | 基于文件描述符打开文件流，需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。使用callback异步回调。 |
| [fdopenStreamSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fdopenstreamsync-f.md) | 以同步方法基于文件描述符打开文件流。需要配合[Stream](arkts-corefile-file-fs-stream-i.md)中的close()函数关闭文件流。 |
| [fsync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fsync-f.md) | 将文件系统缓存数据写入磁盘。使用Promise异步回调。 |
| [fsync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fsync-f.md) | 将文件系统缓存数据写入磁盘。使用callback异步回调。 |
| [fsyncSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-fsyncsync-f.md) | 以同步方法将文件系统缓存数据写入磁盘。 |
| [getxattr(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-getxattr-f.md) | 获取文件或目录的扩展属性。使用promise异步回调。 |
| [getxattrSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-getxattrsync-f.md) | 使用同步接口获取文件或目录的扩展属性。 |
| [listFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfile-f.md) | 默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用Promise异步回调。可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfile-f.md) | 默认列出当前目录下所有文件名和目录名，返回文件名数组。使用callback异步回调。 |
| [listFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfile-f.md) | 默认列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。使用callback异步回调。可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExt(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfileext-f.md) | 列出目录下所有文件名，支持递归列出和自定义文件名过滤。使用Promise异步回调。可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileExtSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfileextsync-f.md) | 以同步方式列出目录下所有文件名，支持递归列出和自定义文件名过滤。可通过配置options中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [listFileSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfilesync-f.md) | 默认以同步方式列出当前目录下所有文件名和目录名，返回文件名数组，支持按后缀、文件名等条件过滤。可通过配置ListFileOptions中recursion参数实现递归列出所有文件的相对路径，相对路径以“/”开头。 |
| [lseek(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-lseek-f.md) | 调整文件偏移指针位置。 |
| [lstat(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-lstat-f.md) | 获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用Promise异步回调。 |
| [lstat(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-lstat-f.md) | 获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。使用callback异步回调。 |
| [lstatSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-lstatsync-f.md) | 以同步方法获取符号链接文件信息，返回符号链接本身的属性而非目标文件的属性。 |
| [mkdir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdir-f.md) | 创建单层目录，若父目录不存在则会报错。使用Promise异步回调。 |
| [mkdir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdir-f.md) | 创建目录。使用Promise异步回调。当recursion指定为true时，可递归创建目录。 |
| [mkdir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdir-f.md) | 创建单层目录，若父目录不存在则会报错。使用callback异步回调。 |
| [mkdir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdir-f.md) | 创建目录，当recursion指定为true，可递归创建目录。使用callback异步回调。 |
| [mkdirSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdirsync-f.md) | 以同步方法创建单层目录，若父目录不存在则会报错。 |
| [mkdirSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdirsync-f.md) | 以同步方法创建目录。当recursion指定为true，可递归创建目录。 |
| [mkdtemp(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdtemp-f.md) | 创建临时目录。使用Promise异步回调。 |
| [mkdtemp(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdtemp-f.md) | 创建临时目录。使用callback异步回调。 |
| [mkdtempSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mkdtempsync-f.md) | 以同步方法创建临时目录。 |
| [mmap(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mmap-f.md) | 基于文件描述符或文件对象创建文件映射对象，实现文件的高效读写访问。使用Promise异步回调。 |
| [mmapSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mmapsync-f.md) | 以同步方法基于文件描述符或文件对象创建文件映射对象，实现文件的高效读写访问。 |
| [moveDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movedir-f.md) | 移动源目录及其内容至目标路径下。使用Promise异步回调。 |
| [moveDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movedir-f.md) | 移动源目录及其内容至目标路径下。使用callback异步回调。移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。 |
| [moveDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movedir-f.md) | 移动源目录及其内容至目标路径下。使用callback异步回调。移动模式为目录级别抛异常。当目标目录下存在与源目录名冲突的目录，则抛出异常。 |
| [moveDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movedir-f.md) | 移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。 |
| [moveDir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movedir-f.md) | 移动源目录及其内容至目标路径下，支持设置冲突处理模式。使用callback异步回调。 |
| [moveDirSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movedirsync-f.md) | 以同步方法移动源目录及其内容至目标路径下。 |
| [moveFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movefile-f.md) | 移动文件至目标路径，支持设置冲突处理模式。使用Promise异步回调。 |
| [moveFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movefile-f.md) | 移动文件。如果移动位置存在同名文件，将强制覆盖。使用callback异步回调。 |
| [moveFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movefile-f.md) | 移动文件至目标路径，支持设置冲突处理模式。使用callback异步回调。 |
| [moveFileSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-movefilesync-f.md) | 以同步方式移动文件至目标路径。 |
| [open(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-open-f.md) | 打开文件或目录，支持使用URI打开文件。使用Promise异步回调。 |
| [open(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-open-f.md) | 打开文件或目录，支持使用URI打开文件。使用callback异步回调。 |
| [open(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-open-f.md) | 打开文件或目录，可设置打开文件的选项。使用callback异步回调。支持使用URI打开文件。 |
| [openSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-opensync-f.md) | 以同步方法打开文件或目录。支持使用URI打开文件。 |
| [read(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-read-f.md) | 从文件读取数据，返回实际读取的字节数。使用Promise异步回调。 |
| [read(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-read-f.md) | 从文件读取数据，返回实际读取的字节数。使用callback异步回调。 |
| [read(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-read-f.md) | 从文件读取数据，支持配置读取选项（如偏移位置和读取长度），返回实际读取的字节数。使用callback异步回调。 |
| [readLines(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readlines-f.md) | 逐行读取文件文本内容，只支持读取utf-8格式文件。使用promise异步回调。 |
| [readLines(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readlines-f.md) | 逐行读取文件文本内容，只支持读取utf-8格式文件。使用callback异步回调。 |
| [readLines(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readlines-f.md) | 逐行读取文件文本内容，可配置读取选项，只支持读取utf-8格式文件。使用callback异步回调。 |
| [readLinesSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readlinessync-f.md) | 以同步方式逐行读取文件的文本内容，只支持读取utf-8格式文件。 |
| [readSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readsync-f.md) | 以同步方法从文件读取数据，返回实际读取的字节数。 |
| [readText(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readtext-f.md) | 基于文本方式读取文件（即直接读取文件的文本内容）。使用Promise异步回调。 |
| [readText(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readtext-f.md) | 基于文本方式读取文件内容。使用callback异步回调。 |
| [readText(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readtext-f.md) | 基于文本方式读取文件内容，支持配置读取选项。使用callback异步回调。 |
| [readTextSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readtextsync-f.md) | 以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。 |
| [rename(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-rename-f.md) | 重命名文件或目录。使用Promise异步回调。 |
| [rename(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-rename-f.md) | 重命名文件或目录。使用callback异步回调。 |
| [renameSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-renamesync-f.md) | 以同步方法重命名文件或目录。 |
| [rmdir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-rmdir-f.md) | 删除目录及其所有子目录和文件。使用Promise异步回调。 |
| [rmdir(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-rmdir-f.md) | 删除目录及其所有子目录和文件。使用callback异步回调。 |
| [rmdirSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-rmdirsync-f.md) | 以同步方法删除目录及其所有子目录和文件。 |
| [setxattr(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-setxattr-f.md) | 设置文件或目录的扩展属性。使用promise异步回调。 |
| [setxattrSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-setxattrsync-f.md) | 设置文件或目录的扩展属性。 |
| [stat(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-stat-f.md) | 获取文件或目录详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用Promise异步回调。 |
| [stat(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-stat-f.md) | 获取文件或目录的详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。使用callback异步回调。 |
| [statSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-statsync-f.md) | 以同步方法获取文件或目录详细属性信息，返回包含文件大小、权限模式、访问时间、修改时间等属性的Stat对象。 |
| [symlink(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-symlink-f.md) | 基于文件路径创建符号链接。使用Promise异步回调。 |
| [symlink(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-symlink-f.md) | 基于文件路径创建符号链接。使用callback异步回调。 |
| [symlinkSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-symlinksync-f.md) | 以同步的方法基于文件路径创建符号链接。 |
| [truncate(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-truncate-f.md) | 截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用Promise异步回调。 |
| [truncate(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-truncate-f.md) | 截断文件，删除文件内容。使用callback异步回调。 |
| [truncate(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-truncate-f.md) | 截断文件，将文件大小调整为指定长度，超出部分的内容将被删除。使用callback异步回调。 |
| [truncateSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-truncatesync-f.md) | 以同步方法截断文件内容，将文件大小调整为指定长度，超出部分的内容将被删除。 |
| [unlink(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-unlink-f.md) | 删除单个文件，仅适用于文件，不可用于删除目录。使用Promise异步回调。 |
| [unlink(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-unlink-f.md) | 删除单个文件，仅适用于文件，不可用于删除目录。使用callback异步回调。 |
| [unlinkSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-unlinksync-f.md) | 以同步方法删除单个文件，仅适用于文件，不可用于删除目录。 |
| [utimes(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-utimes-f.md) | 更改文件的上次修改时间。 |
| [write(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-write-f.md) | 将数据写入文件，返回实际写入的字节数。使用Promise异步回调。 |
| [write(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-write-f.md) | 将数据写入文件，返回实际写入的字节数。使用callback异步回调。 |
| [write(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-write-f.md) | 将数据写入文件，支持配置写入选项（如偏移位置和写入长度），返回实际写入的字节数。使用callback异步回调。 |
| [writeSync(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-writesync-f.md) | 以同步方法将数据写入文件，返回实际写入的字节数。 |

### 类

| 名称 | 说明 |
| --- | --- |
| [AtomicFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-atomicfile-c.md) | AtomicFile是一个用于对文件进行原子读写等操作的类。在写操作时，通过写入临时文件，并在写入成功后将其重命名到原始文件位置来确保写入文件的完整性；而在写入失败时删除临时文件，不修改原始文件内容。使用者可以自行调用finishWrite或failWrite来完成文件内容的写入或回滚。 |
| [ReadStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readstream-c.md) | 文件可读流，需要先通过fileIo.createReadStream方法来构建一个ReadStream实例。ReadStream继承自数据流基类stream.Readable。 ReadStream读到的数据为解码后的字符串，其编码格式当前仅支持'utf-8'。 |
| [TaskSignal(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-tasksignal-c.md) | 拷贝中断信号。 |
| [WriteStream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-writestream-c.md) | 文件可写流，需要先通过 [fileIo.createWriteStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatewritestream12)方法来构建一 个WriteStream实例。WriteStream继承自数据流基类[stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md)。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [ConflictFiles(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-conflictfiles-i.md) | 冲突文件信息，支持copyDir及moveDir接口使用。 |
| [CopyOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-copyoptions-i.md) | 拷贝进度回调监听 |
| [DfsListeners(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-dfslisteners-i.md) | 事件监听类。创建DFSListener对象，用于监听分布式文件系统状态。 |
| [File(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-file-i.md) | 由open接口打开的File对象，持有文件描述符fd，提供文件锁和获取父目录等能力。 |
| [FileFilter(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-filefilter-i.md) | 文件名过滤器接口，可通过该接口自定义文件名过滤规则。 |
| [FileMapping(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-filemapping-i.md) | 文件映射对象，在调用FileMapping的方法前，需要先通过[mmap()](arkts-corefile-file-fs-mmap-f.md)或方法[mmapSync()](arkts-corefile-file-fs-mmapsync-f.md)构建一个FileMapping实例。 |
| [Filter(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-filter-i.md) | 文件过滤配置项，支持listFile接口使用。 |
| [ListFileExtOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfileextoptions-i.md) | 可选项类型，支持listFileExt接口使用。 |
| [ListFileOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-listfileoptions-i.md) | 可选项类型，支持listFile接口使用。 |
| [Options(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-options-i.md) | 可选项类型，支持readLines接口使用。 |
| [Progress(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-progress-i.md) | 拷贝进度回调数据 |
| [RandomAccessFile(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-randomaccessfile-i.md) | 随机读写文件流，提供基于偏移指针的随机读写能力。在调用RandomAccessFile的方法前，需要先通过createRandomAccessFile()方法（同步或异步）来构建一个RandomAccessFile实例。 |
| [RandomAccessFileOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-randomaccessfileoptions-i.md) | 可选项类型，支持 createRandomAccessFile 接口使用。 |
| [ReaderIterator(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readeriterator-i.md) | 文件读取迭代器。在调用ReaderIterator的方法前，需要先通过readLines方法（同步或异步）来构建一个ReaderIterator实例。 |
| [ReaderIteratorResult(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readeriteratorresult-i.md) | 文件读取迭代器返回结果，支持ReaderIterator接口使用。 |
| [ReadOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readoptions-i.md) | 可选项类型，支持read接口使用。 |
| [ReadStreamOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readstreamoptions-i.md) | 可选项类型，支持 createReadStream 接口使用。 |
| [ReadTextOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-readtextoptions-i.md) | 可选项类型，支持readText接口使用，ReadTextOptions继承自[ReadOptions](arkts-corefile-file-fs-readoptions-i.md)。 |
| [Stat(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-stat-i.md) | 文件具体信息，包含文件大小、权限模式、访问时间、修改时间等属性。在调用Stat的方法前，需要先通过[stat()](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiostat)方法（同步或异步）构建一个 Stat实例。 |
| [Stream(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-stream-i.md) | 文件流，提供流式读写文件数据的能力，使用完毕后需调用close关闭。在调用Stream的方法前，需要先通过 [fileIo.createStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatestream)方法或者 [fileIo.fdopenStream](../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiofdopenstream)（同步或异步）来构建一个Stream 实例。 |
| [Watcher(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-watcher-i.md) | 文件目录变化监听对象。由createWatcher接口获得。 |
| [WatchEvent(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-watchevent-i.md) | 事件类 |
| [WatchEventListener(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-watcheventlistener-i.md) | 事件监听类，当监听的文件或目录发生变动事件时触发回调。 |
| [WriteOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-writeoptions-i.md) | 可选项类型，支持write接口使用，WriteOptions继承自[Options](arkts-corefile-file-fs-options-i.md)。 |
| [WriteStreamOptions(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-writestreamoptions-i.md) | 可选项类型，支持 createWriteStream 接口使用。 |

### 枚举

| 名称 | 说明 |
| --- | --- |
| [AccessFlagType(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-accessflagtype-e.md) | 枚举，表示需要校验的文件位置。 |
| [AccessModeType(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-accessmodetype-e.md) | 枚举，表示需要校验的具体权限。若不填，默认校验文件是否存在。 |
| [LocationType(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-locationtype-e.md) | 枚举，文件位置，表示该文件是否在本地或者云端存在。 |
| [MappingMode(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-mappingmode-e.md) | 文件内存映射模式类型的枚举。 |
| [WhenceType(@ohos.file.fs (文件管理))](arkts-corefile-file-fs-whencetype-e.md) | 枚举，文件偏移指针相对偏移位置类型，支持lseek接口使用。 |

### 类型

| 名称 | 说明 |
| --- | --- |
| [ProgressListener(@ohos.file.fs (文件管理))](arkts-corefile-progresslistener-t.md) | 拷贝进度监听。 |
