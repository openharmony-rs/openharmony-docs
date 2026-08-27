# RandomAccessFileOptions

可选项类型，支持 createRandomAccessFile 接口使用。

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## end

```TypeScript
end?: number
```

表示文件的结束偏移位置，单位为Byte。可选，默认文件末尾。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

## start

```TypeScript
start?: number
```

表示文件的起始偏移位置，单位为Byte。可选，默认从当前位置开始读。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.FileManagement.File.FileIO

**示例**

```TypeScript
let filePath = pathDir + "/test.txt";
let watcher = fileIo.createWatcher(filePath, 0xfff, () => {});
watcher.start();
watcher.stop();
```
