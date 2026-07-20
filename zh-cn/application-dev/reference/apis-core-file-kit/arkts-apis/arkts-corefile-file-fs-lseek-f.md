# lseek

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="lseek"></a>
## lseek

```TypeScript
declare function lseek(fd: number, offset: number, whence?: WhenceType): number
```

调整文件偏移指针位置。

**起始版本：** 11

<!--Device-unnamed-declare function lseek(fd: number, offset: number, whence?: WhenceType): number--><!--Device-unnamed-declare function lseek(fd: number, offset: number, whence?: WhenceType): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符。 |
| offset | number | 是 | 相对偏移位置，单位为Byte。 |
| whence | [WhenceType](arkts-corefile-file-fs-whencetype-e.md) | 否 | 偏移指针相对位置类型。不指定则默认为文件起始位置处。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前文件偏移指针位置（相对于文件头的偏移量，单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900026 | Illegal seek |
| 13900038 | Value too large for defined data type |
| 13900042 | Unknown error |

