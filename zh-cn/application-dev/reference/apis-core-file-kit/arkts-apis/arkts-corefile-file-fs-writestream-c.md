# WriteStream

文件可写流，需要先通过[fileIo.createWriteStream](../../../../reference/apis-core-file-kit/js-apis-file-fs.md#fileiocreatewritestream12)方法来构建一个WriteStream实例。WriteStream继承自数据流基类[stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md)。

**继承/实现关系：** WriteStream extends [stream.Writable](../../apis-arkts/arkts-apis/arkts-arkts-stream-writable-c.md)

**起始版本：** 12

<!--Device-unnamed-declare class WriteStream extends stream.Writable--><!--Device-unnamed-declare class WriteStream extends stream.Writable-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## close

```TypeScript
close(): void
```

关闭可写流。

**起始版本：** 12

<!--Device-WriteStream-close(): void--><!--Device-WriteStream-close(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900025 | No space left on device |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**示例：**

```TypeScript
const filePath = pathDir + "/test.txt";
const ws = fileIo.createWriteStream(filePath);
ws.close();

```

## constructor

```TypeScript
constructor()
```

The WriteStream constructor.

**起始版本：** 12

<!--Device-WriteStream-constructor()--><!--Device-WriteStream-constructor()-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## seek

```TypeScript
seek(offset: number, whence?: WhenceType): number
```

调整可写流的偏移指针位置。

**起始版本：** 12

<!--Device-WriteStream-seek(offset: number, whence?: WhenceType): number--><!--Device-WriteStream-seek(offset: number, whence?: WhenceType): number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| offset | number | 是 | 相对偏移位置，单位为Byte。 |
| whence | [WhenceType](arkts-corefile-file-fs-whencetype-e.md) | 否 | 偏移指针相对位置类型。默认值：SEEK_SET，文件起始位置处。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 当前可写流偏移指针位置（相对于文件头的偏移量，单位为Byte）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../apis-contacts-kit/errorcode-contacts.md#401-系统内部错误) | Parameter error |
| 13900020 | Invalid argument |
| 13900026 | Illegal seek |
| 13900042 | Unknown error |

**示例：**

```TypeScript
const filePath = pathDir + "/test.txt";
const ws = fileIo.createWriteStream(filePath);
const curOff = ws.seek(5, fileIo.WhenceType.SEEK_SET);
console.info(`Succeeded in seeking, current offset is ${curOff}`);
ws.close();

```

## bytesWritten

```TypeScript
readonly bytesWritten: number
```

可写流已经写入的字节数。

**类型：** number

**起始版本：** 12

<!--Device-WriteStream-readonly bytesWritten: number--><!--Device-WriteStream-readonly bytesWritten: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## path

```TypeScript
readonly path: string
```

当前可写流对应的文件路径。

**类型：** string

**起始版本：** 12

<!--Device-WriteStream-readonly path: string--><!--Device-WriteStream-readonly path: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

