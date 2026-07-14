# createWatcher

## createWatcher

```TypeScript
declare function createWatcher(path: string, events: number, listener: WatchEventListener): Watcher
```

创建Watcher对象，监听文件或目录变动。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| path | string | 是 | 监听文件或目录的沙箱路径。 |
| events | number | 是 | 监听变动的事件集，多个事件通过或(\|)的方式进行集合。<br/>- 0x1: IN_ACCESS， 文件被访问。<br/>- 0x2: IN_MODIFY，文件内容被修改。<br/>- 0x4: IN_ATTRIB，文件元数据被修改。<br/>- 0x8: IN_CLOSE_WRITE，文件在打开时进行了写操作，然后被关闭。<br/>- 0x10: IN_CLOSE_NOWRITE，文件或目录在打开时未进行写操作，然后被关闭。<br/>- 0x20: IN_OPEN，文件或目录被打开。 <br/>- 0x40: IN_MOVED_FROM，监听目录中文件被移动走。<br/>- 0x80: IN_MOVED_TO，监听目录中文件被移动过来。<br/>- 0x100: IN_CREATE，监听目录中文件或子目录被创建。<br/>- 0x200: IN_DELETE，监听目录中文件或子目录被删除。<br/>- 0x400: IN_DELETE_SELF，监听的目录被删除，删除后监听停止。<br/>- 0x800: IN_MOVE_SELF，监听的文件或目录被移动，移动后监听继续。<br/>- 0xfff: IN_ALL_EVENTS，监听以上所有事件。 |
| listener | WatchEventListener | 是 | 监听事件发生后的回调。监听事件每发生一次，回调一次。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Watcher | 返回Watcher对象。 |

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
| 13900030 | File name too long |
| 13900042 | Unknown error |

