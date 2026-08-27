# @ohos.fileio(@ohos.fileio (文件管理))

该模块提供文件存储管理能力，包括文件基本管理、文件目录管理、文件信息统计、文件流式读写等常用功能。

> **使用说明：**
使用该功能模块对文件/目录进行操作前，需要先获取其应用沙箱路径，获取沙箱路径的方式及其接口用法可参考： [应用上下文Context-获取应用文件路径](../../../application-models/application-context-stage.md#获取应用文件路径)。

## 导入模块

```TypeScript
```

## 汇总

### 命名空间

| 名称 | 说明 |
| --- | --- |
| [fileIO(@ohos.fileio (文件管理))](arkts-corefile-fileio-depr-n.md) | 该模块提供文件存储管理能力，包括文件基本管理、文件目录管理、文件信息统计、文件流式读写等常用功能。 |

### 函数

| 名称 | 说明 |
| --- | --- |
| [access(@ohos.fileio (文件管理))](arkts-corefile-fileio-access-f.md) | 检查当前进程是否可访问某文件，使用Promise异步回调。 |
| [access(@ohos.fileio (文件管理))](arkts-corefile-fileio-access-f.md) | 检查当前进程是否可访问某文件，使用callback异步回调。 |
| [access(@ohos.fileio (文件管理))](arkts-corefile-fileio-access-f.md) | 检查当前进程是否可访问某文件，使用callback异步回调。 |
| [accessSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-accesssync-f.md) | 以同步方法检查当前进程是否可访问某文件。 |
| [chmod(@ohos.fileio (文件管理))](arkts-corefile-fileio-chmod-f.md) | 改变文件权限，使用Promise异步回调。 |
| [chmod(@ohos.fileio (文件管理))](arkts-corefile-fileio-chmod-f.md) | 改变文件权限，使用callback异步回调。 |
| [chmodSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-chmodsync-f.md) | 以同步方法改变文件权限。 |
| [chown(@ohos.fileio (文件管理))](arkts-corefile-fileio-chown-f.md) | 基于文件路径改变文件所有者，使用Promise异步回调。 |
| [chown(@ohos.fileio (文件管理))](arkts-corefile-fileio-chown-f.md) | 基于文件路径改变文件所有者，使用callback异步回调。 |
| [chownSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-chownsync-f.md) | 以同步的方法基于文件路径改变文件所有者。 |
| [close(@ohos.fileio (文件管理))](arkts-corefile-fileio-close-f.md) | 关闭文件，使用Promise异步回调。 |
| [close(@ohos.fileio (文件管理))](arkts-corefile-fileio-close-f.md) | 关闭文件，使用callback异步回调。 |
| [closeSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-closesync-f.md) | 以同步方法关闭文件。 |
| [copyFile(@ohos.fileio (文件管理))](arkts-corefile-fileio-copyfile-f.md) | 复制文件，使用Promise异步回调。 |
| [copyFile(@ohos.fileio (文件管理))](arkts-corefile-fileio-copyfile-f.md) | copyFile. |
| [copyFile(@ohos.fileio (文件管理))](arkts-corefile-fileio-copyfile-f.md) | 复制文件，使用callback异步回调。 |
| [copyFileSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-copyfilesync-f.md) | 以同步方法复制文件。 |
| [createStream(@ohos.fileio (文件管理))](arkts-corefile-fileio-createstream-f.md) | 基于文件路径打开文件流，使用Promise异步回调。 |
| [createStream(@ohos.fileio (文件管理))](arkts-corefile-fileio-createstream-f.md) | 基于文件路径打开文件流，使用callback异步回调。 |
| [createStreamSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-createstreamsync-f.md) | 以同步方法基于文件路径打开文件流。 |
| [createWatcher(@ohos.fileio (文件管理))](arkts-corefile-fileio-createwatcher-f.md) | 监听文件或者目录的变化，使用callback异步回调。 |
| [fchmod(@ohos.fileio (文件管理))](arkts-corefile-fileio-fchmod-f.md) | 基于文件描述符改变文件权限，使用Promise异步回调。 |
| [fchmod(@ohos.fileio (文件管理))](arkts-corefile-fileio-fchmod-f.md) | 基于文件描述符改变文件权限，使用callback异步回调。 |
| [fchmodSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fchmodsync-f.md) | 以同步方法基于文件描述符改变文件权限。 |
| [fchown(@ohos.fileio (文件管理))](arkts-corefile-fileio-fchown-f.md) | 基于文件描述符改变文件所有者，使用Promise异步回调。 |
| [fchown(@ohos.fileio (文件管理))](arkts-corefile-fileio-fchown-f.md) | 基于文件描述符改变文件所有者，使用callback异步回调。 |
| [fchownSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fchownsync-f.md) | 以同步方法基于文件描述符改变文件所有者。 |
| [fdatasync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fdatasync-f.md) | 实现文件内容数据同步，使用Promise异步回调。 |
| [fdatasync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fdatasync-f.md) | 实现文件内容数据同步，使用callback异步回调。 |
| [fdatasyncSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fdatasyncsync-f.md) | 以同步方法实现文件内容数据同步。 |
| [fdopenStream(@ohos.fileio (文件管理))](arkts-corefile-fileio-fdopenstream-f.md) | 基于文件描述符打开文件流，使用Promise异步回调。 |
| [fdopenStream(@ohos.fileio (文件管理))](arkts-corefile-fileio-fdopenstream-f.md) | 基于文件描述符打开文件流，使用callback异步回调。 |
| [fdopenStreamSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fdopenstreamsync-f.md) | 以同步方法基于文件描述符打开文件流。 |
| [fstat(@ohos.fileio (文件管理))](arkts-corefile-fileio-fstat-f.md) | 基于文件描述符获取文件状态信息，使用Promise异步回调。 |
| [fstat(@ohos.fileio (文件管理))](arkts-corefile-fileio-fstat-f.md) | 基于文件描述符获取文件状态信息，使用callback异步回调。 |
| [fstatSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fstatsync-f.md) | 以同步方法基于文件描述符获取文件状态信息。 |
| [fsync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fsync-f.md) | 同步文件数据，使用Promise异步回调。 |
| [fsync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fsync-f.md) | 同步文件数据，使用callback异步回调。 |
| [fsyncSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-fsyncsync-f.md) | 以同步方法同步文件数据。 |
| [ftruncate(@ohos.fileio (文件管理))](arkts-corefile-fileio-ftruncate-f.md) | 基于文件描述符截断文件，使用Promise异步回调。 |
| [ftruncate(@ohos.fileio (文件管理))](arkts-corefile-fileio-ftruncate-f.md) | 基于文件描述符截断文件，使用callback异步回调。 |
| [ftruncate(@ohos.fileio (文件管理))](arkts-corefile-fileio-ftruncate-f.md) | 基于文件描述符截断文件，使用callback异步回调。 |
| [ftruncateSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-ftruncatesync-f.md) | 以同步方法基于文件描述符截断文件。 |
| [hash(@ohos.fileio (文件管理))](arkts-corefile-fileio-hash-f.md) | 计算文件的哈希值，使用Promise异步回调。 |
| [hash(@ohos.fileio (文件管理))](arkts-corefile-fileio-hash-f.md) | 计算文件的哈希值，使用callback异步回调。 |
| [lchown(@ohos.fileio (文件管理))](arkts-corefile-fileio-lchown-f.md) | 基于文件路径改变文件所有者，更改符号链接本身的所有者，而不是符号链接所指向的实际文件，使用Promise异步回调。 |
| [lchown(@ohos.fileio (文件管理))](arkts-corefile-fileio-lchown-f.md) | 基于文件路径改变文件所有者，更改符号链接本身的所有者，而不是更改符号链接所指向的实际文件，使用callback异步回调。 |
| [lchownSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-lchownsync-f.md) | 以同步方法基于文件路径改变文件所有者，更改符号链接本身的所有者，而不是更改符号链接所指向的实际文件。 |
| [lstat(@ohos.fileio (文件管理))](arkts-corefile-fileio-lstat-f.md) | 获取链接信息，使用Promise异步回调。 |
| [lstat(@ohos.fileio (文件管理))](arkts-corefile-fileio-lstat-f.md) | 获取链接信息，使用callback异步回调。 |
| [lstatSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-lstatsync-f.md) | 以同步方法获取链接信息。 |
| [mkdir(@ohos.fileio (文件管理))](arkts-corefile-fileio-mkdir-f.md) | 创建目录，使用Promise异步回调。 |
| [mkdir(@ohos.fileio (文件管理))](arkts-corefile-fileio-mkdir-f.md) | 创建目录，使用callback异步回调。 |
| [mkdir(@ohos.fileio (文件管理))](arkts-corefile-fileio-mkdir-f.md) | 创建目录，使用callback异步回调。 |
| [mkdirSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-mkdirsync-f.md) | 以同步方法创建目录。 |
| [mkdtemp(@ohos.fileio (文件管理))](arkts-corefile-fileio-mkdtemp-f.md) | 创建临时目录，使用Promise异步回调。 |
| [mkdtemp(@ohos.fileio (文件管理))](arkts-corefile-fileio-mkdtemp-f.md) | 创建临时目录，使用callback异步回调。 |
| [mkdtempSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-mkdtempsync-f.md) | 以同步的方法创建临时目录。 |
| [open(@ohos.fileio (文件管理))](arkts-corefile-fileio-open-f.md) | 打开文件，使用Promise异步回调。 |
| [open(@ohos.fileio (文件管理))](arkts-corefile-fileio-open-f.md) | 打开文件，使用callback异步回调。 |
| [open(@ohos.fileio (文件管理))](arkts-corefile-fileio-open-f.md) | 打开文件，使用callback异步回调。 |
| [open(@ohos.fileio (文件管理))](arkts-corefile-fileio-open-f.md) | 打开文件，使用callback异步回调。 |
| [opendir(@ohos.fileio (文件管理))](arkts-corefile-fileio-opendir-f.md) | 打开文件目录，使用Promise异步回调。 |
| [opendir(@ohos.fileio (文件管理))](arkts-corefile-fileio-opendir-f.md) | 打开文件目录，使用callback异步回调。 |
| [opendirSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-opendirsync-f.md) | 以同步方法打开文件目录。 |
| [openSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-opensync-f.md) | 以同步方法打开文件。 |
| [read(@ohos.fileio (文件管理))](arkts-corefile-fileio-read-f.md) | 从文件读取数据，使用Promise异步回调。 |
| [read(@ohos.fileio (文件管理))](arkts-corefile-fileio-read-f.md) | 从文件读取数据，使用callback异步回调。 |
| [read(@ohos.fileio (文件管理))](arkts-corefile-fileio-read-f.md) | 从文件读取数据，使用callback异步回调。 |
| [readSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-readsync-f.md) | 以同步方法从文件读取数据。 |
| [readText(@ohos.fileio (文件管理))](arkts-corefile-fileio-readtext-f.md) | 基于文本方式读取文件（即直接读取文件的文本内容），使用Promise异步回调。 |
| [readText(@ohos.fileio (文件管理))](arkts-corefile-fileio-readtext-f.md) | 基于文本方式读取文件（即直接读取文件的文本内容），使用callback异步回调。 |
| [readTextSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-readtextsync-f.md) | 以同步方法基于文本方式读取文件（即直接读取文件的文本内容）。 |
| [rename(@ohos.fileio (文件管理))](arkts-corefile-fileio-rename-f.md) | 重命名文件，使用Promise异步回调。 |
| [rename(@ohos.fileio (文件管理))](arkts-corefile-fileio-rename-f.md) | 重命名文件，使用callback异步回调。 |
| [renameSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-renamesync-f.md) | 以同步方法重命名文件。 |
| [rmdir(@ohos.fileio (文件管理))](arkts-corefile-fileio-rmdir-f.md) | 删除目录，使用Promise异步回调。 |
| [rmdir(@ohos.fileio (文件管理))](arkts-corefile-fileio-rmdir-f.md) | 删除目录，使用callback异步回调。 |
| [rmdirSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-rmdirsync-f.md) | 以同步方法删除目录。 |
| [stat(@ohos.fileio (文件管理))](arkts-corefile-fileio-stat-f.md) | 获取文件信息，使用Promise异步回调。 |
| [stat(@ohos.fileio (文件管理))](arkts-corefile-fileio-stat-f.md) | 获取文件信息，使用callback异步回调。 |
| [statSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-statsync-f.md) | 以同步方法获取文件的信息。 |
| [symlink(@ohos.fileio (文件管理))](arkts-corefile-fileio-symlink-f.md) | 基于文件路径创建符号链接，使用Promise异步回调。 |
| [symlink(@ohos.fileio (文件管理))](arkts-corefile-fileio-symlink-f.md) | 基于文件路径创建符号链接，使用callback异步回调。 |
| [symlinkSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-symlinksync-f.md) | 以同步的方法基于文件路径创建符号链接。 |
| [truncate(@ohos.fileio (文件管理))](arkts-corefile-fileio-truncate-f.md) | 基于文件路径截断文件，使用Promise异步回调。 |
| [truncate(@ohos.fileio (文件管理))](arkts-corefile-fileio-truncate-f.md) | 基于文件路径截断文件，使用callback异步回调。 |
| [truncate(@ohos.fileio (文件管理))](arkts-corefile-fileio-truncate-f.md) | 基于文件路径截断文件，使用callback异步回调。 |
| [truncateSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-truncatesync-f.md) | 以同步方法基于文件路径截断文件。 |
| [unlink(@ohos.fileio (文件管理))](arkts-corefile-fileio-unlink-f.md) | 删除文件，使用Promise异步回调。 |
| [unlink(@ohos.fileio (文件管理))](arkts-corefile-fileio-unlink-f.md) | 删除文件，使用callback异步回调。 |
| [unlinkSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-unlinksync-f.md) | 以同步方法删除文件。 |
| [write(@ohos.fileio (文件管理))](arkts-corefile-fileio-write-f.md) | 将数据写入文件，使用Promise异步回调。 |
| [write(@ohos.fileio (文件管理))](arkts-corefile-fileio-write-f.md) | 将数据写入文件，使用callback异步回调。 |
| [write(@ohos.fileio (文件管理))](arkts-corefile-fileio-write-f.md) | 将数据写入文件，使用callback异步回调。 |
| [writeSync(@ohos.fileio (文件管理))](arkts-corefile-fileio-writesync-f.md) | 以同步方法将数据写入文件。 |

### 接口

| 名称 | 说明 |
| --- | --- |
| [Dir(@ohos.fileio (文件管理))](arkts-corefile-fileio-dir-depr-i.md) | 管理目录，在调用Dir的方法前，需要先通过opendir方法（同步或异步）来构建一个Dir实例。 |
| [Dirent(@ohos.fileio (文件管理))](arkts-corefile-fileio-dirent-depr-i.md) | 在调用Dirent的方法前，需要先通过[dir.read()](arkts-corefile-fileio-read-f.md)方法（同步或异步）来构建一个Dirent实例。 |
| [ReadOut(@ohos.fileio (文件管理))](arkts-corefile-fileio-readout-depr-i.md) | 仅用于read方法，获取文件的读取结果。 |
| [Stat(@ohos.fileio (文件管理))](arkts-corefile-fileio-stat-depr-i.md) | 文件具体信息，在调用Stat的方法前，需要先通过[stat()](arkts-corefile-fileio-stat-f.md)方法（同步或异步）来构建一个Stat实例。 |
| [Stream(@ohos.fileio (文件管理))](arkts-corefile-fileio-stream-depr-i.md) | 文件流，在调用Stream的方法前，需要先通过createStream()方法（同步或异步）来构建一个Stream实例。 |
| [Watcher(@ohos.fileio (文件管理))](arkts-corefile-fileio-watcher-depr-i.md) | Watcher是文件变化监听的实例，调用Watcher.stop()方法（同步或异步）来停止文件监听。 |
