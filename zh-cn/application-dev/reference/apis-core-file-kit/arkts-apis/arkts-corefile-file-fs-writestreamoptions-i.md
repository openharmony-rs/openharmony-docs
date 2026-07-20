# WriteStreamOptions

可选项类型，支持 createWriteStream 接口使用。

**起始版本：** 12

<!--Device-unnamed-export interface WriteStreamOptions--><!--Device-unnamed-export interface WriteStreamOptions-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## mode

```TypeScript
mode?: number
```

创建文件可写流的[选项](docroot://reference/apis-core-file-kit/js-apis-file-fs.md#openmode)，必须指定如下选项中的一个，默认只写方式创建：

- OpenMode.READ_ONLY(0o0)：只读。

- OpenMode.WRITE_ONLY(0o1)：只写。

- OpenMode.READ_WRITE(0o2)：读写。

给定如下功能选项，以按位或的方式追加，默认不给定任何额外选项：

- OpenMode.CREATE(0o100)：若文件不存在，则创建文件。

- OpenMode.TRUNC(0o1000)：如果文件存在且文件具有写权限，则将其长度裁剪为零。

- OpenMode.APPEND(0o2000)：以追加方式打开，后续写将追加到文件末尾。

- OpenMode.NONBLOCK(0o4000)：如果path指向FIFO、块特殊文件或字符特殊文件，则本次打开及后续IO进行非阻塞操作。

- OpenMode.DIR(0o200000)：如果path不指向目录，则出错。不允许附加写权限。

- OpenMode.NOFOLLOW(0o400000)：如果path指向符号链接，则出错。

- OpenMode.SYNC(0o4010000)：以同步IO的方式打开文件。

**类型：** number

**起始版本：** 12

<!--Device-WriteStreamOptions-mode?: number--><!--Device-WriteStreamOptions-mode?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## start

```TypeScript
start?: number
```

表示期望写入文件的位置，单位为Byte。可选，默认从当前位置开始写。

**类型：** number

**起始版本：** 12

<!--Device-WriteStreamOptions-start?: number--><!--Device-WriteStreamOptions-start?: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

