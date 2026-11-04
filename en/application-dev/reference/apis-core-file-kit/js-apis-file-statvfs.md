# @ohos.file.statvfs (File System Space Statistics)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0c20469e58610438940464085fdd62df82c5b560 translatedAt=2026-11-04T04:26:14.121Z pushedAt=2026-11-04T10:12:33.479Z nl=1 -->

This module provides ArkTS APIs for applications to obtain the total bytes and free bytes of a file system. With this module, developers can monitor the storage status of the file system in real time, avoid application crashes caused by insufficient storage space, and improve user experience and system stability.

Usage scenarios include: checking storage space before file download, estimating disk space before application installation, and monitoring space in cache management.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { statfs } from '@kit.CoreFileKit';
```

## statfs.getFreeSize

getFreeSize(path: string): Promise&lt;number&gt;

Obtains the free bytes of the file system where the specified file or directory is located. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name| Type  | Mandatory| Description                        |
  | ------ | ------ | ---- | ---------------------------- |
  | path   | string | Yes   | App sandbox path of the file or directory. |

**Return value**

  | Type                 | Description          |
  | --------------------- | -------------- |
  | Promise&lt;number&gt; | Promise used to return the free bytes, in bytes. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**Example**

<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getFreeSize(path).then((freeSize: number) => {
    console.info("Succeeded in getting free size: " + freeSize);
  }).catch((err: BusinessError) => {
    console.error("Failed to get free size. Code: " + err.code + ", message: " + err.message);
  });
  ```

## statfs.getFreeSize

getFreeSize(path: string, callback:AsyncCallback&lt;number&gt;): void

Obtains the free bytes of the file system where the specified file or directory is located. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name  | Type                       | Mandatory| Description                        |
  | -------- | --------------------------- | ---- | ---------------------------- |
  | path     | string                      | Yes   | App sandbox path of the file or directory. |
  | callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the free bytes in Byte. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**Example**

<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getFreeSize(path, (err: BusinessError, freeSize: number) => {
    if (err) {
      console.error("Failed to get free size. Code: " + err.code + ", message: " + err.message);
    } else {
      console.info("Succeeded in getting free size: " + freeSize);
    }
  });
  ```

## statfs.getFreeSizeSync<sup>10+</sup>

getFreeSizeSync(path: string): number

Synchronously obtains the free bytes of the file system where the specified file or directory is located.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name| Type  | Mandatory| Description                        |
  | ------ | ------ | ---- | ---------------------------- |
  | path   | string | Yes   | App sandbox path of the file or directory. |

**Return value**

  | Type                 | Description          |
  | --------------------- | -------------- |
  | number | Returns the free bytes, in Byte. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**Example**

<!--code_no_check-->
  ```ts
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  let freeSize = statfs.getFreeSizeSync(path);
  console.info("Succeeded in getting free size: " + freeSize);
  ```

## statfs.getTotalSize

getTotalSize(path: string): Promise&lt;number&gt;

Obtains the total bytes of the file system where the specified file or directory is located. This API uses a promise to return the result asynchronously.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name| Type  | Mandatory| Description                        |
  | ---- | ------ | ---- | ---------------------------- |
  | path | string | Yes | App sandbox path of the file or directory. |

**Return value**

  | Type                 | Description        |
  | --------------------- | ------------ |
  | Promise&lt;number&gt; | Promise used to return the total bytes, in Byte. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**Example**

<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getTotalSize(path).then((totalSize: number) => {
    console.info("Succeeded in getting total size: " + totalSize);
  }).catch((err: BusinessError) => {
    console.error("Failed to get total size. Code: " + err.code + ", message: " + err.message);
  });
  ```

## statfs.getTotalSize

getTotalSize(path: string, callback: AsyncCallback&lt;number&gt;): void

Obtains the total bytes of the file system where the specified file or directory is located. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name  | Type                       | Mandatory| Description                        |
  | -------- | --------------------------- | ---- | ---------------------------- |
  | path     | string                      | Yes   | App sandbox path of the file or directory. |
  | callback | AsyncCallback&lt;number&gt; | Yes   | Callback used to return the total bytes in Byte.   |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**Example**

<!--code_no_check-->
  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  statfs.getTotalSize(path, (err: BusinessError, totalSize: number) => {
    if (err) {
      console.error("Failed to get total size. Code: " + err.code + ", message: " + err.message);
    } else {
      console.info("Succeeded in getting total size: " + totalSize);
    }
  });
  ```

## statfs.getTotalSizeSync<sup>10+</sup>

getTotalSizeSync(path: string): number

Obtains the total bytes of the file system where the specified file or directory is located in synchronous mode.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name| Type  | Mandatory| Description                        |
  | ---- | ------ | ---- | ---------------------------- |
  | path | string | Yes   | App sandbox path of the file or directory. |

**Return value**

  | Type                 | Description        |
  | --------------------- | ------------ |
  | number | Returns the total bytes, in Byte. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900002 | No such file or directory. |
| 13900004 | Interrupted system call. |
| 13900005 | I/O error. |
| 13900008 | Bad file descriptor. |
| 13900011 | Out of memory. |
| 13900012 | Permission denied. |
| 13900013 | Bad address. |
| 13900018 | Not a directory. |
| 13900030 | File name too long. |
| 13900031 | Function not implemented. |
| 13900033 | Too many symbolic links encountered. |
| 13900038 | Value too large for defined data type. |
| 13900042 | Unknown error. |

**Example**

<!--code_no_check-->
  ```ts
  import { common } from '@kit.AbilityKit';

  // Obtain the context from the component and ensure that the return value of this.getUIContext().getHostContext() is UIAbilityContext.
  let context = this.getUIContext().getHostContext() as common.UIAbilityContext;
  let path = context.filesDir;
  let totalSize = statfs.getTotalSizeSync(path);
  console.info("Succeeded in getting total size: " + totalSize);
  ```
