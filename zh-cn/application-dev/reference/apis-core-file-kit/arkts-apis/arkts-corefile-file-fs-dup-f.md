# dup

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## dup

```TypeScript
declare function dup(fd: number): File
```

复制文件描述符，并返回对应的File对象。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| fd | number | 是 | 文件描述符。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [File](arkts-corefile-file-fs-file-i.md) | 打开的File对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900005 | I/O error |
| 13900008 | Bad file descriptor |
| 13900014 | Device or resource busy |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900042 | Unknown error |

**示例**

```TypeScript
let filePath = pathDir + "/test.txt";
let file1 = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE);
let fd: number = file1.fd;
let file2 = fileIo.dup(fd);
console.info(`Succeeded in getting file name of the file2 is ${file2.name}`);
fileIo.closeSync(file1);
fileIo.closeSync(file2);
```
