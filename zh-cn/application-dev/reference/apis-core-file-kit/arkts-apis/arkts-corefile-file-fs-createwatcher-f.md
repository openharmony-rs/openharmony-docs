# createWatcher

## 导入模块

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## createWatcher

```TypeScript
declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher
```

创建Watcher对象，用于监听文件或目录的创建、删除、修改等变动事件。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 监听文件或目录的应用沙箱路径。 |
| events | number | 是 | 监听变动的事件集，多个事件通过或(\| )的方式进行集合。   - 0x1: IN_ACCESS， 文件被访问。   - 0x2: IN_MODIFY，文件内容被修改。 &lt;br/&gt;- 0x4: IN_ATTRIB，文件元数据被修改。   - 0x8: IN_CLOSE_WRITE，文件在打开时进行了写操作，然后被关闭。   - 0x10: IN_CLOSE_NOWRITE，文件或目录在打开时未 进行写操作，然后被关闭。   - 0x20: IN_OPEN，文件或目录被打开。    - 0x40: IN_MOVED_FROM，监听目录中文件被移动走。   - 0x80: IN_MOVED_TO，监听目录中文 件被移动过来。   - 0x100: IN_CREATE，监听目录中文件或子目录被创建。   - 0x200: IN_DELETE，监听目录中文件或子目录被删除。   - 0x400: IN_DELETE_SELF ，监听的目录被删除，删除后监听停止。   - 0x800: IN_MOVE_SELF，监听的文件或目录被移动，移动后监听继续。   - 0xfff: IN_ALL_EVENTS，监听以上所有事件。 |
| listener | [WatchEventListener](arkts-corefile-file-fs-watcheventlistener-i.md) | 是 | 监听事件发生后的回调。监听事件每发生一次，回调一次。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| [Watcher](arkts-corefile-file-fs-watcher-i.md) | 返回Watcher对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900002 | No such file or directory |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900020 | Invalid argument |
| 13900021 | File table overflow |
| 13900022 | Too many open files |
| 13900025 | No space left on device |
| 13900030 | File name too number |
| 13900042 | Unknown error |

**示例**

```TypeScript
import { common } from '@kit.AbilityKit';
import { WatchEvent } from '@kit.CoreFileKit';

// 请在组件内获取context，确保this.getUIContext().getHostContext()返回结果为UIAbilityContext
let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
let pathDir = context.filesDir;
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
let watcher = fileIo.createWatcher(filePath, 0x2 | 0x10, (watchEvent: WatchEvent) => {
  if (watchEvent.event == 0x2) {
    console.info(watchEvent.fileName + ' was modified');
  } else if (watchEvent.event == 0x10) {
    console.info(watchEvent.fileName + ' was closed');
  }
});
watcher.start();
fileIo.writeSync(file.fd, 'test');
fileIo.closeSync(file);
watcher.stop();
```
