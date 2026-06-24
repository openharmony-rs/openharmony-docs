# Watcher

文件目录变化监听对象。由createWatcher接口获得。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

## start

```TypeScript
start(): void
```

开启监听。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900021](../../errorcode-universal.md#13900021-File) | File table overflow |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let watcher = fileIo.createWatcher(filePath, 0xfff, () => {});
watcher.start();
watcher.stop();

```

## stop

```TypeScript
stop(): void
```

停止监听并移除Watcher对象。

**起始版本：** 10

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [13900002](../../errorcode-universal.md#13900002-No) | No such file or directory |
| [13900008](../../errorcode-universal.md#13900008-Bad) | Bad file descriptor |
| [13900011](../../errorcode-universal.md#13900011-Out) | Out of memory |
| [13900012](../../errorcode-universal.md#13900012-Permission) | Permission denied |
| [13900013](../../errorcode-universal.md#13900013-Bad) | Bad address |
| [13900015](../../errorcode-universal.md#13900015-File) | File exists |
| [13900018](../../errorcode-universal.md#13900018-Not) | Not a directory |
| [13900020](../../errorcode-universal.md#13900020-Invalid) | Invalid argument |
| [13900021](../../errorcode-universal.md#13900021-File) | File table overflow |
| [13900022](../../errorcode-universal.md#13900022-Too) | Too many open files |
| [13900025](../../errorcode-universal.md#13900025-No) | No space left on device |
| [13900030](../../errorcode-universal.md#13900030-File) | File name too long |
| [13900042](../../errorcode-universal.md#13900042-Unknown) | Unknown error |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let watcher = fileIo.createWatcher(filePath, 0xfff, () => {});
watcher.start();
watcher.stop();

```

