# File

由open接口打开的File对象。

**起始版本：** 9

<!--Device-unnamed-declare interface File--><!--Device-unnamed-declare interface File-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## 导入模块

```TypeScript
import { Options, ReaderIteratorResult, Watcher, ReadTextOptions, WatchEventListener, TaskSignal, WriteOptions, ListFileExtOptions, DfsListeners, Filter, ReadOptions, ListFileOptions, WatchEvent, FileFilter, ConflictFiles } from '@kit.CoreFileKit';
```

## getParent

```TypeScript
getParent(): string
```

获取File对象对应文件父目录。

**起始版本：** 11

<!--Device-File-getParent(): string--><!--Device-File-getParent(): string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string | 返回父目录路径。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |
| 14300002 | Invalid URI |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
console.info(`Succeeded in getting parent path, the parent path is: ${file.getParent()}`);
fileIo.closeSync(file);

```

## lock

```TypeScript
lock(exclusive?: boolean): Promise<void>
```

对文件阻塞式施加共享锁或独占锁，使用promise异步回调。

**起始版本：** 9

<!--Device-File-lock(exclusive?: boolean): Promise<void>--><!--Device-File-lock(exclusive?: boolean): Promise<void>-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclusive | boolean | 否 | 是否施加独占锁，默认false。true：施加独占锁；false：不施加独占锁。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回值。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
file.lock(true).then(() => {
  console.info(`Succeeded in locking file.`);
}).catch((err: BusinessError) => {
  console.error(`Failed to lock file. Code: ${err.code}, message: ${err.message}`);
}).finally(() => {
  fileIo.closeSync(file);
});

```

## lock

```TypeScript
lock(callback: AsyncCallback<void>): void
```

对文件阻塞式施加共享锁或独占锁，使Callback异步回调。

**起始版本：** 9

<!--Device-File-lock(callback: AsyncCallback<void>): void--><!--Device-File-lock(callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步文件上锁之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
file.lock((err: BusinessError) => {
  if (err) {
    console.error(`Failed to lock file. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in locking file.`);
  }
  fileIo.closeSync(file);
});

```

## lock

```TypeScript
lock(exclusive: boolean, callback: AsyncCallback<void>): void
```

对文件阻塞式施加共享锁或独占锁，使Callback异步回调。

**起始版本：** 9

<!--Device-File-lock(exclusive: boolean, callback: AsyncCallback<void>): void--><!--Device-File-lock(exclusive: boolean, callback: AsyncCallback<void>): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclusive | boolean | 是 | 是否施加独占锁，默认false。true：施加独占锁；false：不施加独占锁。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | 是 | 异步文件上锁之后的回调。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**示例：**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
file.lock(true, (err: BusinessError) => {
  if (err) {
    console.error(`Failed to lock file. Code: ${err.code}, message: ${err.message}`);
  } else {
    console.info(`Succeeded in locking file.`);
  }
  fileIo.closeSync(file);
});

```

## tryLock

```TypeScript
tryLock(exclusive?: boolean): void
```

文件非阻塞式施加共享锁或独占锁。

**起始版本：** 9

<!--Device-File-tryLock(exclusive?: boolean): void--><!--Device-File-tryLock(exclusive?: boolean): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| exclusive | boolean | 否 | 是否施加独占锁，默认false。true：施加独占锁；false：不施加独占锁。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
file.tryLock(true);
console.info(`Succeeded in locking file.`);
fileIo.closeSync(file);

```

## unlock

```TypeScript
unlock(): void
```

以同步方式解锁文件。

**起始版本：** 9

<!--Device-File-unlock(): void--><!--Device-File-unlock(): void-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**示例：**

```TypeScript
let filePath = pathDir + "/test.txt";
let file = fileIo.openSync(filePath, fileIo.OpenMode.READ_WRITE | fileIo.OpenMode.CREATE);
file.tryLock(true);
file.unlock();
console.info(`Succeeded in unlocking file.`);
fileIo.closeSync(file);

```

## fd

```TypeScript
readonly fd: number
```

打开的文件描述符。

**类型：** number

**起始版本：** 9

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务API中使用。

<!--Device-File-readonly fd: number--><!--Device-File-readonly fd: number-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## name

```TypeScript
readonly name: string
```

文件名。

**类型：** string

**起始版本：** 10

<!--Device-File-readonly name: string--><!--Device-File-readonly name: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

## path

```TypeScript
readonly path: string
```

文件路径。

**类型：** string

**起始版本：** 10

<!--Device-File-readonly path: string--><!--Device-File-readonly path: string-End-->

**系统能力：** SystemCapability.FileManagement.File.FileIO

