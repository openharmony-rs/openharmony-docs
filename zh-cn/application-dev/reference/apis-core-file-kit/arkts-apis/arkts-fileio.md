# @ohos.fileio

该模块提供文件存储管理能力，包括文件基本管理、文件目录管理、文件信息统计、文件流式读写等常用功能。 > **使用说明：** 使用该功能模块对文件/目录进行操作前，需要先获取其应用沙箱路径，获取沙箱路径的方式及其接口用法可参考： [应用上下文Context-获取应用文件路径](../../../application-models/application-context-stage.md#获取应用文件路径)。

## 导入模块

```TypeScript
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [fileIO](arkts-corefile-fileio-depr-n.md) | 该模块提供文件存储管理能力，包括文件基本管理、文件目录管理、文件信息统计、文件流式读写等常用功能。 > **使用说明：** 使用该功能模块对文件/目录进行操作前，需要先获取其应用沙箱路径，获取沙箱路径的方式及其接口用法可参考： [应用上下文Context-获取应用文件路径](../../../application-models/application-context-stage.md#获取应用文件路径)。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [access](arkts-corefile-fileio-access-f.md) | 检查当前进程是否可访问某文件，使用Promise异步回调。 |
| [access](arkts-corefile-fileio-access-f.md) | 检查当前进程是否可访问某文件，使用callback异步回调。 |
| [access](arkts-corefile-fileio-access-f.md) | 检查当前进程是否可访问某文件，使用callback异步回调。 |
| [accessSync](arkts-corefile-fileio-accesssync-f.md) | 以同步方法检查当前进程是否可访问某文件。 |
| [chmod](arkts-corefile-fileio-chmod-f.md) | 改变文件权限，使用Promise异步回调。 |
| [chmod](arkts-corefile-fileio-chmod-f.md) | 改变文件权限，使用callback异步回调。 |
| [chmodSync](arkts-corefile-fileio-chmodsync-f.md) | 以同步方法改变文件权限。 |
| [chown](arkts-corefile-fileio-chown-f.md) | 基于文件路径改变文件所有者，使用Promise异步回调。 |
| [chown](arkts-corefile-fileio-chown-f.md) | 基于文件路径改变文件所有者，使用callback异步回调。 |
| [chownSync](arkts-corefile-fileio-chownsync-f.md) | 以同步的方法基于文件路径改变文件所有者。 |
| [close](arkts-corefile-fileio-close-f.md) | 关闭文件，使用Promise异步回调。 |
| [close](arkts-corefile-fileio-close-f.md) | 关闭文件，使用callback异步回调。 |
| [closeSync](arkts-corefile-fileio-closesync-f.md) | 以同步方法关闭文件。 |
| [copyFile](arkts-corefile-fileio-copyfile-f.md) | 复制文件，使用Promise异步回调。 |
| [copyFile](arkts-corefile-fileio-copyfile-f.md) | copyFile. |
| [copyFile](arkts-corefile-fileio-copyfile-f.md) | 复制文件，使用callback异步回调。 |
| [copyFileSync](arkts-corefile-fileio-copyfilesync-f.md) | 以同步方法复制文件。 |
| [createStream](arkts-corefile-fileio-createstream-f.md) | 基于文件路径打开文件流，使用Promise异步回调。 |
| [createStream](arkts-corefile-fileio-createstream-f.md) | 基于文件路径打开文件流，使用callback异步回调。 |
| [createStreamSync](arkts-corefile-fileio-createstreamsync-f.md) | 以同步方法基于文件路径打开文件流。 |
| [createWatcher](arkts-corefile-fileio-createwatcher-f.md) | 监听文件或者目录的变化，使用callback异步回调。 |
| [fchmod](arkts-corefile-fileio-fchmod-f.md) | 基于文件描述符改变文件权限，使用Promise异步回调。 |
| [fchmod](arkts-corefile-fileio-fchmod-f.md) | 基于文件描述符改变文件权限，使用callback异步回调。 |
| [fchmodSync](arkts-corefile-fileio-fchmodsync-f.md) | 以同步方法基于文件描述符改变文件权限。 |
| [fchown](arkts-corefile-fileio-fchown-f.md) | 基于文件描述符改变文件所有者，使用Promise异步回调。 |
| [fchown](arkts-corefile-fileio-fchown-f.md) | 基于文件描述符改变文件所有者，使用callback异步回调。 |
| [fchownSync](arkts-corefile-fileio-fchownsync-f.md) | 以同步方法基于文件描述符改变文件所有者。 |
| [fdatasync](arkts-corefile-fileio-fdatasync-f.md) | 实现文件内容数据同步，使用Promise异步回调。 |
| [fdatasync](arkts-corefile-fileio-fdatasync-f.md) | 实现文件内容数据同步，使用callback异步回调。 |
| [fdatasyncSync](arkts-corefile-fileio-fdatasyncsync-f.md) | 以同步方法实现文件内容数据同步。 |
| [fdopenStream](arkts-corefile-fileio-fdopenstream-f.md) | 基于文件描述符打开文件流，使用Promise异步回调。 |
| [fdopenStream](arkts-corefile-fileio-fdopenstream-f.md) | 基于文件描述符打开文件流，使用callback异步回调。 |
| [fdopenStreamSync](arkts-corefile-fileio-fdopenstreamsync-f.md) | 以同步方法基于文件描述符打开文件流。 |
| [fstat](arkts-corefile-fileio-fstat-f.md) | 基于文件描述符获取文件状态信息，使用Promise异步回调。 |
| [fstat](arkts-corefile-fileio-fstat-f.md) | 基于文件描述符获取文件状态信息，使用callback异步回调。 |
| [fstatSync](arkts-corefile-fileio-fstatsync-f.md) | 以同步方法基于文件描述符获取文件状态信息。 |
| [fsync](arkts-corefile-fileio-fsync-f.md) | 同步文件数据，使用Promise异步回调。 |
| [fsync](arkts-corefile-fileio-fsync-f.md) | 同步文件数据，使用callback异步回调。 |
| [fsyncSync](arkts-corefile-fileio-fsyncsync-f.md) | 以同步方法同步文件数据。 |
| [ftruncate](arkts-corefile-fileio-ftruncate-f.md) | 基于文件描述符截断文件，使用Promise异步回调。 |
| [ftruncate](arkts-corefile-fileio-ftruncate-f.md) | 基于文件描述符截断文件，使用callback异步回调。 |
| [ftruncate](arkts-corefile-fileio-ftruncate-f.md) | 基于文件描述符截断文件，使用callback异步回调。 |
| [ftruncateSync](arkts-corefile-fileio-ftruncatesync-f.md) | 以同步方法基于文件描述符截断文件。 |
| [hash](arkts-corefile-fileio-hash-f.md) | 计算文件的哈希值，使用Promise异步回调。 |
| [hash](arkts-corefile-fileio-hash-f.md) | 计算文件的哈希值，使用callback异步回调。 |
| [lchown](arkts-corefile-fileio-lchown-f.md) | 基于文件路径改变文件所有者，更改符号链接本身的所有者，而不是符号链接所指向的实际文件，使用Promise异步回调。 |
| [lchown](arkts-corefile-fileio-lchown-f.md) | 基于文件路径改变文件所有者，更改符号链接本身的所有者，而不是更改符号链接所指向的实际文件，使用callback异步回调。 |
| [lchownSync](arkts-corefile-fileio-lchownsync-f.md) | 以同步方法基于文件路径改变文件所有者，更改符号链接本身的所有者，而不是更改符号链接所指向的实际文件。 |
| [lstat](arkts-corefile-fileio-lstat-f.md) | 获取链接信息，使用Promise异步回调。 |
| [lstat](arkts-corefile-fileio-lstat-f.md) | 获取链接信息，使用callback异步回调。 |
| [lstatSync](arkts-corefile-fileio-lstatsync-f.md) | 以同步方法获取链接信息。 |
| [mkdir](arkts-corefile-fileio-mkdir-f.md) | 创建目录，使用Promise异步回调。 |
| [mkdir](arkts-corefile-fileio-mkdir-f.md) | 创建目录，使用callback异步回调。 |
| [mkdir](arkts-corefile-fileio-mkdir-f.md) | 创建目录，使用callback异步回调。 |
| [mkdirSync](arkts-corefile-fileio-mkdirsync-f.md) | 以同步方法创建目录。 |
| [mkdtemp](arkts-corefile-fileio-mkdtemp-f.md) | 创建临时目录，使用Promise异步回调。 |
| [mkdtemp](arkts-corefile-fileio-mkdtemp-f.md) | 创建临时目录，使用callback异步回调。 |
| [mkdtempSync](arkts-corefile-fileio-mkdtempsync-f.md) | 以同步的方法创建临时目录。 |
| [open](arkts-corefile-fileio-open-f.md) | 打开文件，使用Promise异步回调。 |
| [open](arkts-corefile-fileio-open-f.md) | 打开文件，使用callback异步回调。 |
| [open](arkts-corefile-fileio-open-f.md) | 打开文件，使用callback异步回调。 |
| [open](arkts-corefile-fileio-open-f.md) | 打开文件，使用callback异步回调。 |
| [openSync](arkts-corefile-fileio-opensync-f.md) | 以同步方法打开文件。 |
| [opendir](arkts-corefile-fileio-opendir-f.md) | 打开文件目录，使用Promise异步回调。 |
| [opendir](arkts-corefile-fileio-opendir-f.md) | 打开文件目录，使用callback异步回调。 |
| [opendirSync](arkts-corefile-fileio-opendirsync-f.md) | 以同步方法打开文件目录。 |
| [read](arkts-corefile-fileio-read-f.md) | 从文件读取数据，使用Promise异步回调。 |
| [read](arkts-corefile-fileio-read-f.md) | 从文件读取数据，使用callback异步回调。 |
| [read](arkts-corefile-fileio-read-f.md) | 从文件读取数据，使用callback异步回调。 |
| [readSync](arkts-corefile-fileio-readsync-f.md) | 以同步方法从文件读取数据。 |
| [readText](arkts-corefile-fileio-readtext-f.md) | 基于文本方式读取文件（即直接读取文件的文本内容），使用Promise异步回调。 |
| [readText](arkts-corefile-fileio-readtext-f.md) | 基于文本方式读取文件（即直接读取文件的文本内容），使用callback异步回调。 |
| [readTextSync](arkts-corefile-fileio-readtextsync-f.md) | 以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。 |
| [rename](arkts-corefile-fileio-rename-f.md) | 重命名文件，使用Promise异步回调。 |
| [rename](arkts-corefile-fileio-rename-f.md) | 重命名文件，使用callback异步回调。 |
| [renameSync](arkts-corefile-fileio-renamesync-f.md) | 以同步方法重命名文件。 |
| [rmdir](arkts-corefile-fileio-rmdir-f.md) | 删除目录，使用Promise异步回调。 |
| [rmdir](arkts-corefile-fileio-rmdir-f.md) | 删除目录，使用callback异步回调。 |
| [rmdirSync](arkts-corefile-fileio-rmdirsync-f.md) | 以同步方法删除目录。 |
| [stat](arkts-corefile-fileio-stat-f.md) | 获取文件信息，使用Promise异步回调。 |
| [stat](arkts-corefile-fileio-stat-f.md) | 获取文件信息，使用callback异步回调。 |
| [statSync](arkts-corefile-fileio-statsync-f.md) | 以同步方法获取文件的信息。 |
| [symlink](arkts-corefile-fileio-symlink-f.md) | 基于文件路径创建符号链接，使用Promise异步回调。 |
| [symlink](arkts-corefile-fileio-symlink-f.md) | 基于文件路径创建符号链接，使用callback异步回调。 |
| [symlinkSync](arkts-corefile-fileio-symlinksync-f.md) | 以同步的方法基于文件路径创建符号链接。 |
| [truncate](arkts-corefile-fileio-truncate-f.md) | 基于文件路径截断文件，使用Promise异步回调。 |
| [truncate](arkts-corefile-fileio-truncate-f.md) | 基于文件路径截断文件，使用callback异步回调。 |
| [truncate](arkts-corefile-fileio-truncate-f.md) | 基于文件路径截断文件，使用callback异步回调。 |
| [truncateSync](arkts-corefile-fileio-truncatesync-f.md) | 以同步方法基于文件路径截断文件。 |
| [unlink](arkts-corefile-fileio-unlink-f.md) | 删除文件，使用Promise异步回调。 |
| [unlink](arkts-corefile-fileio-unlink-f.md) | 删除文件，使用callback异步回调。 |
| [unlinkSync](arkts-corefile-fileio-unlinksync-f.md) | 以同步方法删除文件。 |
| [write](arkts-corefile-fileio-write-f.md) | 将数据写入文件，使用Promise异步回调。 |
| [write](arkts-corefile-fileio-write-f.md) | 将数据写入文件，使用callback异步回调。 |
| [write](arkts-corefile-fileio-write-f.md) | 将数据写入文件，使用callback异步回调。 |
| [writeSync](arkts-corefile-fileio-writesync-f.md) | 以同步方法将数据写入文件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Dir](arkts-corefile-fileio-dir-depr-i.md) | 管理目录，在调用Dir的方法前，需要先通过opendir方法（同步或异步）来构建一个Dir实例。 |
| [Dirent](arkts-corefile-fileio-dirent-depr-i.md) | 在调用Dirent的方法前，需要先通过[dir.read()](arkts-corefile-fileio-read-f.md)方法（同步或异步）来构建一个Dirent实例。 |
| [ReadOut](arkts-corefile-fileio-readout-depr-i.md) | 仅用于read方法，获取文件的读取结果。 |
| [Stat](arkts-corefile-fileio-stat-depr-i.md) | 文件具体信息，在调用Stat的方法前，需要先通过[stat()](arkts-corefile-fileio-stat-f.md)方法（同步或异步）来构建一个Stat实例。 |
| [Stream](arkts-corefile-fileio-stream-depr-i.md) | 文件流，在调用Stream的方法前，需要先通过createStream()方法（同步或异步）来构建一个Stream实例。 |
| [Watcher](arkts-corefile-fileio-watcher-depr-i.md) | Watcher是文件变化监听的实例，调用Watcher.stop()方法（同步或异步）来停止文件监听。 |

