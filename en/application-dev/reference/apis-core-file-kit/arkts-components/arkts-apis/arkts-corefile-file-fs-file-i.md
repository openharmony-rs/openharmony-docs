# File

```TypeScript
declare interface File
```

Represents a **File** object opened by **open()**.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

## Modules to Import

```TypeScript
import { fileIo, ConflictFiles, FileFilter, Filter, Options, ReaderIteratorResult, WatchEvent, WatchEventListener, Watcher, ReadOptions, ReadTextOptions, WriteOptions, ListFileExtOptions, ListFileOptions, DfsListeners, TaskSignal } from '@kit.CoreFileKit';
```

## getParent

```TypeScript
getParent(): string
```

Obtains the parent directory of this file object.

**Since:** 11

**System capability:** SystemCapability.FileManagement.File.FileIO

**Return value:**

| Type | Description |
| --- | --- |
| string | Parent directory obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |
| 14300002 | Invalid URI |

**Examples**

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

Applies an exclusive lock or a shared lock on this file in blocking mode. This API uses a promise to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exclusive | boolean | No | Lock to apply.<br> The value **true** means an exclusive lock, and the value **false** (default) means a shared lock. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**Examples**

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

<a id="lock-1"></a>

## lock

```TypeScript
lock(callback: AsyncCallback<void>): void
```

Applies an exclusive lock or a shared lock on this file in blocking mode. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**Examples**

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

<a id="lock-2"></a>

## lock

```TypeScript
lock(exclusive: boolean, callback: AsyncCallback<void>): void
```

Applies an exclusive lock or a shared lock on this file in blocking mode. This API uses an asynchronous callback to return the result.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exclusive | boolean | Yes | Lock to apply.<br> The value **true** means an exclusive lock, and the value **false** (default) means a shared lock. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**Examples**

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

Applies an exclusive lock or a shared lock on this file in non-blocking mode.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| exclusive | boolean | No | Lock to apply.<br> The value **true** means an exclusive lock, and the value **false** (default) means a shared lock. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**Examples**

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

Unlocks a file. This API returns the result synchronously.

**Since:** 9

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900020 | Invalid argument |
| 13900034 | Operation would block |
| 13900042 | Unknown error |
| 13900043 | No record locks available |

**Examples**

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

FD of the file.

**Type:** number

**Since:** 9

**Atomic service API:** This API can be used in atomic services since API version 11.

**System capability:** SystemCapability.FileManagement.File.FileIO

## name

```TypeScript
readonly name: string
```

Name of the file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |

## path

```TypeScript
readonly path: string
```

Path of the file.

**Type:** string

**Since:** 10

**System capability:** SystemCapability.FileManagement.File.FileIO

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900005 | I/O error |
| 13900042 | Unknown error |
| 14300002 | Invalid URI |
