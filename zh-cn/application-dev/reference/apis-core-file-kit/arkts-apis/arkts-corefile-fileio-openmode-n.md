# OpenMode(@ohos.file.fs (文件管理))

open接口flags参数常量，用于指定文件打开模式（如只读、只写、读写、创建等）。

**起始版本：** 9

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## 汇总

### 常量

| 名称 | 说明 |
| --- | --- |
| [READ_ONLY(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#read_only) | 只读打开。 |
| [WRITE_ONLY(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#write_only) | 只写打开。 |
| [READ_WRITE(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#read_write) | 读写打开。 |
| [CREATE(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#create) | 若文件不存在，则创建文件。 |
| [TRUNC(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#trunc) | 如果文件存在且以只写或读写的方式打开，则将其长度裁剪为零。 |
| [APPEND(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#append) | 以追加方式打开，后续写将追加到文件末尾。 |
| [NONBLOCK(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#nonblock) | 如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。 |
| [DIR(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#dir) | 如果path不指向目录，则出错。 |
| [NOFOLLOW(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#nofollow) | 如果path指向符号链接，则出错。 |
| [SYNC(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#sync) | 以同步IO的方式打开文件。 |
| [UNCACHE(@ohos.file.fs (文件管理))](arkts-corefile-openmode-con.md#uncache) | 读写文件不进行页缓存。 |
