# mmapSync

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

<a id="mmapsync"></a>
## mmapSync

```TypeScript
declare function mmapSync(file: number | File, mode: MappingMode, offset: number, size: number): FileMapping
```

以同步方法基于文件描述符或文件对象创建文件映射对象。将文件内容映射到内存，以实现文件的高效读写访问。注意：读写模式（MappingMode.READ_WRITE）下，若映射范围超过原始文件大小，将自动扩展文件大小。

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-unnamed-declare function mmapSync(file: number | File, mode: MappingMode, offset: number, size: number): FileMapping--><!--Device-unnamed-declare function mmapSync(file: number | File, mode: MappingMode, offset: number, size: number): FileMapping-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| file | number \| File | 是 | 已打开的File对象或已打开的文件描述符fd。 |
| mode | [MappingMode](arkts-corefile-file-fs-mappingmode-e.md) | 是 | 创建文件内存映射对象的选项，必须指定如下选项中的一个：<br>MappingMode.READ_ONLY(0)：只读映射模式。文件映射区不可写，修改会抛出异常。<br>MappingMode.READ_WRITE(1)：读写映射模式。修改会写入文件映射区，后续由操作系统同步到文件（非实时）。<br>MappingMode.PRIVATE(2)：私有映射模式。是一种写时复制的映射机制，对映射区的修改仅对当前进程可见，不会影响原始文件。 |
| offset | number | 是 | 文件映射区的起始位置，单位为Byte。 |
| size | number | 是 | 文件映射区的大小，单位为Byte。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [FileMapping](arkts-corefile-file-fs-filemapping-i.md) | - FileMapping object. |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900010 | Try again |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900038 | Value too large for defined data type |
| 13900050 | Internal resource error |
| 13900056 | Mmap does not support mapping this file |

