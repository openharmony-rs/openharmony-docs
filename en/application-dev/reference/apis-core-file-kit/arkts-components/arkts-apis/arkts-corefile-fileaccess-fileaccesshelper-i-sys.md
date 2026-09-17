# FileAccessHelper (System API)

Provides a **FileAccessHelper** object.

**Since:** 9

**Deprecated since:** 23

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { fileAccess } from '@kit.CoreFileKit';
```

## access

```TypeScript
access(sourceFileUri: string) : Promise<boolean>
```

Checks whether a file or directory exists. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** access(path: string, mode?: AccessModeType)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceFileUri | string | Yes | Indicates the selected file or directory. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Returns whether it exists. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceDir indicates a file in the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
async function accessFunc() {
  let sourceDir: string = "file://docs/storage/Users/currentUser/Download/1.txt";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let existJudgment = await fileAccessHelper.access(sourceDir);
      if (existJudgment) {
        console.info("sourceDir exists");
      } else {
        console.info("sourceDir does not exist");
      }
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("access failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceDir indicates a directory in the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceDir: string = "file://docs/storage/Users/currentUser/Download/test";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.access(sourceDir, (err: BusinessError, existJudgment: boolean) => {
      if (err) {
        console.error("Failed to access in async, errCode:" + err.code + ", errMessage:" + err.message);
        return;
      }
      if (existJudgment)
        console.info("sourceDir exists");
      else
        console.info("sourceDir does not exist");
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("access failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## access

```TypeScript
access(sourceFileUri: string, callback: AsyncCallback<boolean>): void
```

Checks whether a file or directory exists. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** access(path: string, callback: AsyncCallback&lt;boolean&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceFileUri | string | Yes | Indicates the selected file or directory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes | The callback is used to return whether it exists. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [access](#access)

## copy

```TypeScript
copy(sourceUri: string, destUri: string, force?: boolean): Promise<Array<CopyResult>>
```

Copies a file or directory. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** copy(srcUri: string, destUri: string, options?: CopyOptions)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to copy. For example, **file://docs/storage/Users/currentUser/Download/1.txt**. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. For example, **file://docs/storage/Users/currentUser/Download/test**. |
| force | boolean | No | Whether to forcibly overwrite the file with the same name. If **force** is **true**, the file with the same name will be overwritten. If **force** is **false** or not specified, the file with the same name will not be overwritten. The default value is **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[CopyResult](arkts-corefile-fileaccess-copyresult-i-sys.md)&gt;&gt; | Promise used to return the result. If the file or directory is copied successfully, no information is returned. If the file copy fails, a **copyResult** array is returned. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
// A built-in storage directory is used as an example.
// In the sample code, sourceFile indicates the file (directory) in the Download directory to copy, destFile indicates the destination directory in the Download directory, and URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceFile: string = "file://docs/storage/Users/currentUser/Download/1.txt";
let destFile: string = "file://docs/storage/Users/currentUser/Download/test";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.copy(sourceFile, destFile, async (err: BusinessError, copyResult: Array<fileAccess.CopyResult>) => {
      if (err) {
        console.error("copy failed, errCode:" + err.code + ", errMessage:" + err.message);
      }
      if (copyResult.length === 0) {
        console.info("copy success");
      } else {
        for (let i = 0; i < copyResult.length; i++) {
          console.error("errCode" + copyResult[i].errCode);
          console.error("errMsg" + copyResult[i].errMsg);
          console.error("sourceUri" + copyResult[i].sourceUri);
          console.error("destUri" + copyResult[i].destUri);
        }
      }
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("copy failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

```TypeScript
import { BusinessError } from '@ohos.base';
// A built-in storage directory is used as an example.
// In the sample code, sourceFile indicates the file (directory) in the Download directory to copy, destFile indicates the destination directory in the Download directory, and URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceFile: string = "file://docs/storage/Users/currentUser/Download/1.txt";
let destFile: string = "file://docs/storage/Users/currentUser/Download/test";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.copy(sourceFile, destFile, true, async (err: BusinessError, copyResult: Array<fileAccess.CopyResult>) => {
      if (err) {
        console.error("copy failed, errCode:" + err.code + ", errMessage:" + err.message);
      }
      if (copyResult.length === 0) {
        console.info("copy success");
      } else {
        for (let i = 0; i < copyResult.length; i++) {
          console.error("errCode" + copyResult[i].errCode);
          console.error("errMsg" + copyResult[i].errMsg);
          console.error("sourceUri" + copyResult[i].sourceUri);
          console.error("destUri" + copyResult[i].destUri);
        }
      }
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("copy failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## copy

```TypeScript
copy(sourceUri: string, destUri: string, callback: AsyncCallback<Array<CopyResult>>): void
```

Copies a file or directory. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** copy(srcUri: string, destUri: string, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to copy. For example, **file://docs/storage/Users/currentUser/Download/1.txt**. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. For example, **file://docs/storage/Users/currentUser/Download/test**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[CopyResult](arkts-corefile-fileaccess-copyresult-i-sys.md)&gt;&gt; | Yes | Callback invoked to return the result. If the file or directory is copied successfully, no information is returned. If the copy fails, a **copyResult** array is returned. |

**Examples**

See [copy](#copy)

## copy

```TypeScript
copy(sourceUri: string, destUri: string, force: boolean, callback: AsyncCallback<Array<CopyResult>>): void
```

Copies a file or directory. If a file with the same name already exists, you can choose whether to forcibly overwrite the original file. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** copy(srcUri: string, destUri: string, options: CopyOptions, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to copy. For example, **file://docs/storage/Users/currentUser/Download/1.txt**. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. For example, **file://docs/storage/Users/currentUser/Download/test**. |
| force | boolean | Yes | Whether to forcibly overwrite the original file with the same name. If **force** is set to **true**, the original file is forcibly overwritten. If **force** is left empty or set to **false**, the original file is not overwritten. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[CopyResult](arkts-corefile-fileaccess-copyresult-i-sys.md)&gt;&gt; | Yes | Callback invoked to return the result. If the file or directory is copied successfully, no information is returned. If the copy fails, a **copyResult** array is returned. |

**Examples**

See [copy](#copy)

## copyFile

```TypeScript
copyFile(sourceUri: string, destUri: string, fileName: string): Promise<string>
```

Copies a file with an alternative file name. This API uses a promise to return the result.

**Since:** 11

**Deprecated since:** 23

**Substitutes:** copyFile(src: string | number, dest: string | number, mode?: number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to copy. For example, **file://docs/storage/Users/currentUser/Download/1.txt**. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. For example, **file://docs/storage/Users/currentUser/Download/test**. |
| fileName | string | Yes | File name to use if there is a file with the same name as the source file in the destination directory. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | URI of the file generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
// A built-in storage directory is used as an example.
// In the sample code, sourceFile indicates the file (directory) in the Download directory to copy, destFile indicates the destination directory in the Download directory, and URI is the URI in fileInfo.
// You can use the URI obtained.
async function copyFunc01() {
  let sourceFile: string = "file://docs/storage/Users/currentUser/Download/1.txt";
  let destFile: string = "file://docs/storage/Users/currentUser/Download/test";
  let fileName: string = "2.txt";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let copyResult = await fileAccessHelper.copyFile(sourceFile, destFile, fileName);
      console.info("copyResult uri: " + copyResult);
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("copy failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@ohos.base';
// A built-in storage directory is used as an example.
// In the sample code, sourceFile indicates the file (directory) in the Download directory to copy, destFile indicates the destination directory in the Download directory, and URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceFile: string = "file://docs/storage/Users/currentUser/Download/1.txt";
let destFile: string = "file://docs/storage/Users/currentUser/Download/test";
let fileName: string = "2.txt";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.copyFile(sourceFile, destFile, fileName, async (err: BusinessError, copyResult: string) => {
          console.info("copyResult uri: " + copyResult);
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("copy failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## copyFile

```TypeScript
copyFile(sourceUri: string, destUri: string, fileName: string, callback: AsyncCallback<string>): void
```

Copies a file with an alternative file name. This API uses an asynchronous callback to return the result.

**Since:** 11

**Deprecated since:** 23

**Substitutes:** copyFile(src: string | number, dest: string | number, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Test API:** This API is used only in automated test scripts.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to copy. For example, **file://docs/storage/Users/currentUser/Download/1.txt**. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. For example, **file://docs/storage/Users/currentUser/Download/test**. |
| fileName | string | Yes | File name to use if there is a file with the same name as the source file in the destination directory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | URI of the file generated. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [copyFile](#copyfile)

## createFile

```TypeScript
createFile(uri: string, displayName: string) : Promise<string>
```

Creates a file in a directory. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** createRandomAccessFile(file: string | File, mode?: number, options?: RandomAccessFileOptions)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Represents a specific parent directory. |
| displayName | string | Yes | Indicates the new file name, and supports with suffix. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the new file's URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function createFile() {
  // A built-in storage directory is used as an example.
  // In the sample code, sourceUri indicates the Download directory. The URI is the URI in fileInfo.
  // You can use the URI obtained.
  let sourceUri: string = "file://docs/storage/Users/currentUser/Download";
  let displayName: string = "file1";
  let fileUri: string;
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
      if (fileAccessHelper != undefined) {
      fileUri = await fileAccessHelper.createFile(sourceUri, displayName);
      if (!fileUri) {
        console.error("createFile return undefined object");
        return;
      }
      console.info("createFile success, fileUri: " + JSON.stringify(fileUri));       
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("createFile failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceUri indicates the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceUri: string = "file://docs/storage/Users/currentUser/Download";
let displayName: string = "file1";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.createFile(sourceUri, displayName, (err: BusinessError, fileUri: string) => {
      if (err) {
        console.error("Failed to createFile in async, errCode:" + err.code + ", errMessage:" + err.message);
      }
      console.info("createFile success, fileUri: " + JSON.stringify(fileUri));
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("createFile failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## createFile

```TypeScript
createFile(uri: string, displayName: string, callback: AsyncCallback<string>): void
```

Creates a file in a directory. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** createRandomAccessFile(file: string | File, callback: AsyncCallback&lt;RandomAccessFile&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Represents a specific parent directory. |
| displayName | string | Yes | Indicates the new file name, and supports with suffix. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | The callback is used to return the new file's URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [createFile](#createfile)

## delete

```TypeScript
delete(uri: string) : Promise<number>
```

Deletes a file or directory. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** [delete](arkts-corefile-file-fs-atomicfile-c.md#delete)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the file or directory to be deleted. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function deleteFile01() {
  // A built-in storage directory is used as an example.
  // In the sample code, targetUri indicates a file in the Download directory. The URI is the URI in fileInfo.
  // You can use the URI obtained.
  let targetUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let code = await fileAccessHelper.delete(targetUri);
      if (code != 0)
        console.error("delete failed, code " + code);
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("delete failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, targetUri indicates a file in the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let targetUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.delete(targetUri, (err: BusinessError, code: number) => {
      if (err) {
        console.error("Failed to delete in async, errCode:" + err.code + ", errMessage:" + err.message);
      }
      console.info("delete success, code: " + code);
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("delete failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## delete

```TypeScript
delete(uri: string, callback: AsyncCallback<number>): void
```

Deletes a file or directory. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** [delete](arkts-corefile-file-fs-atomicfile-c.md#delete)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the file or directory to be deleted. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes |  |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [delete](#delete)

## getFileInfoFromRelativePath

```TypeScript
getFileInfoFromRelativePath(relativePath: string) : Promise<FileInfo>
```

Obtains a **FileInfo** object based on a relative path. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** stat(file: string | number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relativePath | string | Yes | Indicates the selected file or directory. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md)&gt; | Returns a FileInfo. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// In the sample code, relativePath indicates the Download directory, which is the relativePath in fileInfo.
// You can use the relativePath obtained.
async function getRelativePath() {
  let relativePath: string = "Download/";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let fileInfo = await fileAccessHelper.getFileInfoFromRelativePath(relativePath);
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("getFileInfoFromRelativePath failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// In the sample code, relativePath indicates the Download directory, which is the relativePath in fileInfo.
// You can use the relativePath obtained.
let relativePath: string = "Download/";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.getFileInfoFromRelativePath(relativePath, (err: BusinessError, fileInfo: fileAccess.FileInfo) => {
      if (err) {
        console.error("Failed to getFileInfoFromRelativePath in async, errCode:" + err.code + ", errMessage:" + err.message);
        return;
      }
      console.info("getFileInfoFromRelativePath success, fileInfo: " + JSON.stringify(fileInfo));
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getFileInfoFromRelativePath failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## getFileInfoFromRelativePath

```TypeScript
getFileInfoFromRelativePath(relativePath: string, callback: AsyncCallback<FileInfo>) : void
```

Obtains a **FileInfo** object based on a relative path. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** stat(file: string | number, callback: AsyncCallback&lt;Stat&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| relativePath | string | Yes | Indicates the selected file or directory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md)&gt; | Yes | The callback is used to return a fileinfo object. |

**Examples**

See [getFileInfoFromRelativePath](#getfileinfofromrelativepath)

## getFileInfoFromUri

```TypeScript
getFileInfoFromUri(uri: string) : Promise<FileInfo>
```

Obtains a **FileInfo** object based on a URI. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** stat(file: string | number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the selected file or directory. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md)&gt; | Returns a FileInfo. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceUri indicates the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
async function getUri() {
  let sourceUri: string = "file://docs/storage/Users/currentUser/Download";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let fileInfo = await fileAccessHelper.getFileInfoFromUri(sourceUri);
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("getFileInfoFromUri failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceUri indicates the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceUri: string = "file://docs/storage/Users/currentUser/Download";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.getFileInfoFromUri(sourceUri, (err: BusinessError, fileInfo: fileAccess.FileInfo) => {
      if (err) {
        console.error("Failed to getFileInfoFromUri in async, errCode:" + err.code + ", errMessage:" + err.message);
        return;
      }
      console.info("getFileInfoFromUri success, fileInfo: " + JSON.stringify(fileInfo));
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("getFileInfoFromUri failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## getFileInfoFromUri

```TypeScript
getFileInfoFromUri(uri: string, callback: AsyncCallback<FileInfo>) : void
```

Obtains a **FileInfo** object based on a URI. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** stat(file: string | number, callback: AsyncCallback&lt;Stat&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the selected file or directory. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md)&gt; | Yes | The callback is used to return a fileinfo object. |

**Examples**

See [getFileInfoFromUri](#getfileinfofromuri)

## getRoots

```TypeScript
getRoots(): Promise<RootIterator>
```

Obtains information about the device root nodes of the file management services associated with the **Helper** object. This API uses a promise to return a **RootIterator** object. You can use [next](arkts-corefile-fileaccess-fileiterator-i-sys.md#next) to return [RootInfo](arkts-corefile-fileaccess-rootinfo-i-sys.md).

**Since:** 9

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[RootIterator](arkts-corefile-fileaccess-rootiterator-i-sys.md)&gt; | Returns a RootIterator. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
async function getRoots() {
  let rootIterator: fileAccess.RootIterator;
  let rootinfos: Array<fileAccess.RootInfo> = [];
  let isDone: boolean = false;
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      rootIterator = await fileAccessHelper.getRoots();
      if (!rootIterator) {
        console.error("getRoots interface returns an undefined object");
      }
      while (!isDone) {
        let result = rootIterator.next();
        console.info("next result = " + JSON.stringify(result));
        isDone = result.done;
        if (!isDone) {
          rootinfos.push(result.value);
        }
      }     
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("getRoots failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function getRoots() {
  let rootinfos: Array<fileAccess.RootInfo> = [];
  let isDone: boolean = false;
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      fileAccessHelper.getRoots((err: BusinessError, rootIterator: fileAccess.RootIterator) => {
        if (err) {
          console.error("Failed to getRoots in async, errCode:" + err.code + ", errMessage:" + err.message);
        }
        while (!isDone) {
          let result = rootIterator.next();
          console.info("next result = " + JSON.stringify(result));
          isDone = result.done;
          if (!isDone) {
            rootinfos.push(result.value);
          }
        }
      });       
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("getRoots failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

## getRoots

```TypeScript
getRoots(callback: AsyncCallback<RootIterator>): void
```

Obtains information about the device root nodes of the file management services associated with the **Helper** object. This API uses an asynchronous callback to return a **RootIterator** object. You can use [next](arkts-corefile-fileaccess-fileiterator-i-sys.md#next) to return [RootInfo](arkts-corefile-fileaccess-rootinfo-i-sys.md).

**Since:** 9

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[RootIterator](arkts-corefile-fileaccess-rootiterator-i-sys.md)&gt; | Yes | The callback is used to return a RootIterator. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [getRoots](#getroots)

## mkDir

```TypeScript
mkDir(parentUri: string, displayName: string) : Promise<string>
```

Creates a directory in a specified directory. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** mkdir(path: string)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parentUri | string | Yes | Represents a specific parent directory. |
| displayName | string | Yes | Indicates the new directory name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns the new directory's URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceUri indicates the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
async function createDirectory() {
  let sourceUri: string = "file://docs/storage/Users/currentUser/Download";
  let dirName: string = "dirTest";
  let dirUri: string;
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      dirUri = await fileAccessHelper.mkDir(sourceUri, dirName);
      if (!dirUri) {
        console.error("mkDir return undefined object");
      } else {
        console.info("mkDir success, dirUri: " + JSON.stringify(dirUri));
      }
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("mkDir failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceUri indicates the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceUri: string = "file://docs/storage/Users/currentUser/Download";
let dirName: string = "dirTest";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.mkDir(sourceUri, dirName, (err: BusinessError, dirUri: string) => {
      if (err) {
        console.error("Failed to mkDir in async, errCode:" + err.code + ", errMessage:" + err.message);
      }
      console.info("mkDir success, dirUri: " + JSON.stringify(dirUri));
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("mkDir failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## mkDir

```TypeScript
mkDir(parentUri: string, displayName: string, callback: AsyncCallback<string>): void
```

Creates a directory in a specified directory. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** mkdir(path: string, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| parentUri | string | Yes | Represents a specific parent directory. |
| displayName | string | Yes | Indicates the new directory name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | The callback is used to return the new directory's URI. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [mkDir](#mkdir)

## move

```TypeScript
move(sourceFile: string, destFile: string) : Promise<string>
```

Moves a file or directory. This API uses a promise to return the result. Currently, this API does not support move of files or directories across devices.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** moveFile(src: string, dest: string, mode?: number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceFile | string | Yes | Indicates the file or directory to be moved. |
| destFile | string | Yes | Represents the destination folder. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the file or directory in the destination directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function moveFile01() {
  // A built-in storage directory is used as an example.
  // In the sample code, sourceFile and destFile indicate the files and directories in the Download directory. The URI is the URI in fileInfo.
  // You can use the URI obtained.
  let sourceFile: string = "file://docs/storage/Users/currentUser/Download/1.txt";
  let destFile: string = "file://docs/storage/Users/currentUser/Download/test";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let fileUri = await fileAccessHelper.move(sourceFile, destFile);
      console.info("move success, fileUri: " + JSON.stringify(fileUri));
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("move failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceFile and destFile indicate the files and directories in the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceFile: string = "file://docs/storage/Users/currentUser/Download/1.txt";
let destFile: string = "file://docs/storage/Users/currentUser/Download/test";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.move(sourceFile, destFile, (err: BusinessError, fileUri: string) => {
      if (err) {
        console.error("Failed to move in async, errCode:" + err.code + ", errMessage:" + err.message);
      }
      console.info("move success, fileUri: " + JSON.stringify(fileUri));
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("move failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## move

```TypeScript
move(sourceFile: string, destFile: string, callback: AsyncCallback<string>): void
```

Moves a file or directory. This API uses an asynchronous callback to return the result. Currently, this API does not support move of files or directories across devices.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** moveFile(src: string, dest: string, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceFile | string | Yes | Indicates the file or directory to be moved. |
| destFile | string | Yes | Represents the destination folder. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | The callback is used to return the generated new file or directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [move](#move)

## moveFile

```TypeScript
moveFile(sourceUri: string, destUri: string, fileName: string): Promise<string>
```

Moves a file, and renames it if a file with the same name already exists in the destination directory. This API uses a promise to return the result. If a file with the same name exists (that is, a file moving conflict occurs), you can rename the file to be moved and save it to the destination directory. Currently, this API does not support move of files across devices.

**Since:** 11

**Deprecated since:** 23

**Substitutes:** moveFile(src: string, dest: string, mode?: number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file to move. |
| destUri | string | Yes | URI of the destination directory, to which the file is moved. |
| fileName | string | Yes | New name of the file. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return the URI of the file in the destination directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function moveFile01() {
  // A built-in storage directory is used as an example.
  // In the sample code, sourceUri and destUri indicate the files or directories in the Download directory. The URI is the URI in fileInfo.
  // You can use the URI obtained.
  let sourceUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
  let destUri: string = "file://docs/storage/Users/currentUser/Download/test";
  let fileName: string = "2.txt";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
  if (fileAccessHelper != undefined) {
      let fileUri = await fileAccessHelper.moveFile(sourceUri, destUri, fileName);
      console.info("moveFile success, fileUri: " + JSON.stringify(fileUri));
  }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("moveFile failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceUri and destUri indicate the files or directories in the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
let destUri: string = "file://docs/storage/Users/currentUser/Download/test";
let fileName: string = "2.txt";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.moveFile(sourceUri, destUri, fileName, (err: BusinessError, fileUri: string) => {
      if (err) {
        console.error("Failed to moveFile in async, errCode:" + err.code + ", errMessage:" + err.message);
      }
      console.info("moveFile success, fileUri: " + JSON.stringify(fileUri));
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("moveFile failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## moveFile

```TypeScript
moveFile(sourceUri: string, destUri: string, fileName: string, callback: AsyncCallback<string>): void
```

Moves a file, and renames it if a file with the same name already exists in the destination directory. This API uses an asynchronous callback to return the result. If a file with the same name exists (that is, a file moving conflict occurs), you can rename the file to be moved and save it to the destination directory. Currently, this API does not support move of files across devices.

**Since:** 11

**Deprecated since:** 23

**Substitutes:** moveFile(src: string, dest: string, mode: number, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file to move. |
| destUri | string | Yes | URI of the destination directory, to which the file is moved. |
| fileName | string | Yes | New name of the file. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback invoked to return the URI of the file in the destination directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [moveFile](#movefile)

## moveItem

```TypeScript
moveItem(sourceUri: string, destUri: string, force?: boolean): Promise<Array<MoveResult>>
```

Moves a file or directory. This API uses a promise to return the result. You can forcibly overwrite the file with the same name in the destination directory. Currently, this API does not support move of files or directories across devices.

**Since:** 11

**Deprecated since:** 23

**Substitutes:** moveFile(src: string, dest: string, mode?: number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to move. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. |
| force | boolean | No | Whether to forcibly overwrite the file with the same name. The value **true** means to overwrite the file forcibly; the value **false** means the opposite. The default value is **false**. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MoveResult](arkts-corefile-fileaccess-moveresult-i-sys.md)&gt;&gt; | Promise used to return the result. If the operation is successful, no information is returned. If the operation fails, a **MoveResult** array is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
// A built-in storage directory is used as an example.
// In the sample code, sourceFile indicates the file (directory) in the Download directory to copy, destFile indicates the destination directory in the Download directory, and URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
let destUri: string = "file://docs/storage/Users/currentUser/Download/test";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.moveItem(sourceUri, destUri, async (err: BusinessError, moveResult: Array<fileAccess.MoveResult>) => {
      if (err) {
        console.error("moveItem failed, errCode:" + err.code + ", errMessage:" + err.message);
      }
      if (moveResult.length === 0) {
        console.info("moveItem success");
      } else {
        for (let i = 0; i < moveResult.length; i++) {
          console.error("errCode" + moveResult[i].errCode);
          console.error("errMsg" + moveResult[i].errMsg);
          console.error("sourceUri" + moveResult[i].sourceUri);
          console.error("destUri" + moveResult[i].destUri);
        }
      }
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("moveItem failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

```TypeScript
import { BusinessError } from '@ohos.base';
// A built-in storage directory is used as an example.
// In the sample code, sourceFile indicates the file (directory) in the Download directory to copy, destFile indicates the destination directory in the Download directory, and URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
let destUri: string = "file://docs/storage/Users/currentUser/Download/test";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.moveItem(sourceUri, destUri, true, async (err: BusinessError, moveResult: Array<fileAccess.MoveResult>) => {
      if (err) {
        console.error("moveItem failed, errCode:" + err.code + ", errMessage:" + err.message);
      }
      if (moveResult.length === 0) {
        console.info("moveItem success");
      } else {
        for (let i = 0; i < moveResult.length; i++) {
          console.error("errCode" + moveResult[i].errCode);
          console.error("errMsg" + moveResult[i].errMsg);
          console.error("sourceUri" + moveResult[i].sourceUri);
          console.error("destUri" + moveResult[i].destUri);
        }
      }
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("moveItem failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## moveItem

```TypeScript
moveItem(sourceUri: string, destUri: string, callback: AsyncCallback<Array<MoveResult>>): void
```

Moves a file or directory. This API uses an asynchronous callback to return the result. Currently, this API does not support move of files or directories across devices.

**Since:** 11

**Deprecated since:** 23

**Substitutes:** moveFile(src: string, dest: string, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to move. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[MoveResult](arkts-corefile-fileaccess-moveresult-i-sys.md)&gt;&gt; | Yes | Callback invoked to return the result. If the operation is successful, no information is returned. If the operation fails, a **MoveResult** array is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [moveItem](#moveitem)

## moveItem

```TypeScript
moveItem(sourceUri: string, destUri: string, force: boolean, callback: AsyncCallback<Array<MoveResult>>): void
```

Moves a file or directory. This API uses an asynchronous callback to return the result. You can forcibly overwrite the file with the same name in the destination directory. Currently, this API does not support move of files or directories across devices.

**Since:** 11

**Deprecated since:** 23

**Substitutes:** moveFile(src: string, dest: string, mode: number, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| sourceUri | string | Yes | URI of the source file or directory to move. |
| destUri | string | Yes | URI of the destination directory, to which the file or directory is moved. |
| force | boolean | Yes | Whether to forcibly overwrite the file with the same name. The value **true** means to overwrite the file forcibly; the value **false** means the opposite. The default value is **false**. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[MoveResult](arkts-corefile-fileaccess-moveresult-i-sys.md)&gt;&gt; | Yes | Callback invoked to return the result. If the operation is successful, no information is returned. If the operation fails, a **MoveResult** array is returned. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed, usually the result returned by VerifyAccessToken. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed, application which is not a system application uses system API. |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900030 | File name too long |
| 13900042 | Unknown error |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [moveItem](#moveitem)

## openFile

```TypeScript
openFile(uri: string, flags: OPENFLAGS) : Promise<number>
```

Opens a file. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** open(path: string, mode?: number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the path of the file to open. |
| flags | [OPENFLAGS](arkts-corefile-fileaccess-openflags-e-sys.md) | Yes | Indicate options of opening a file. The default value is read-only. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Returns the file descriptor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function openFile01() {
  // A built-in storage directory is used as an example.
  // In the sample code, targetUri indicates a file in the Download directory. The URI is the URI in fileInfo.
  // You can use the URI obtained.
  let targetUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let fd = await fileAccessHelper.openFile(targetUri, fileAccess.OPENFLAGS.READ);
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("openFile failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, targetUri indicates a file in the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let targetUri: string = "file://docs/storage/Users/currentUser/Download/1.txt";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.openFile(targetUri, fileAccess.OPENFLAGS.READ, (err: BusinessError, fd: number) => {
      if (err) {
        console.error("Failed to openFile in async, errCode:" + err.code + ", errMessage:" + err.message);
      }
      console.info("openFile success, fd: " + fd);
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("openFile failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## openFile

```TypeScript
openFile(uri: string, flags: OPENFLAGS, callback: AsyncCallback<number>): void
```

Opens a file. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** open(path: string, callback: AsyncCallback&lt;File&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the path of the file to open. |
| flags | [OPENFLAGS](arkts-corefile-fileaccess-openflags-e-sys.md) | Yes | Indicate options of opening a file. The default value is read-only. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes | The callback is used to return the file descriptor. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [openFile](#openfile)

## query

```TypeScript
query(uri: string, metaJson: string) : Promise<string>
```

Queries the attribute information about a file or directory based on a URI. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** stat(file: string | number)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | File or directory URI obtained from [FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md). |
| metaJson | string | Yes | Attribute [FILEKEY](arkts-corefile-fileaccess-filekey-e-sys.md) to query. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Promise used to return a JSON string that contains the file attribute and the value obtained. |

**Examples**

```TypeScript
import { BusinessError } from '@ohos.base';
async function getQuery01() {
  let imageFileRelativePath: string = "/storage/Users/currentUser/Download/queryTest/image/01.jpg";
  let jsonStrSingleRelativepath: string = JSON.stringify({ [fileAccess.FileKey.RELATIVE_PATH]: "" });
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let fileInfo = await fileAccessHelper.getFileInfoFromRelativePath(imageFileRelativePath);
      let queryResult = await fileAccessHelper.query(fileInfo.uri, jsonStrSingleRelativepath);
      console.info("query_file_single faf query, queryResult.relative_path: " + JSON.parse(queryResult).relative_path);
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("query_file_single faf query failed, error.code :" + error.code + ", errorMessage :" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@ohos.base';
async function getQuery02() {
  let imageFileRelativePath: string = "/storage/Users/currentUser/Download/queryTest/image/01.jpg";
  let jsonStrSingleRelativepath: string = JSON.stringify({ [fileAccess.FileKey.RELATIVE_PATH]: "" });
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let fileInfo = await fileAccessHelper.getFileInfoFromRelativePath(imageFileRelativePath);
      fileAccessHelper.query(fileInfo.uri, jsonStrSingleRelativepath, (err: BusinessError, queryResult: string) => {
        if (err) {
          console.error(`query_file_single faf query Failed, code is ${err.code}, message is ${err.message}`);
          return;
        }
        console.info("query_file_single faf query, queryResult.relative_path: " + JSON.parse(queryResult).relative_path);
      })
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("query_file_single faf query failed, error.code :" + error.code + ", errorMessage :" + error.message);
  }
}
```

## query

```TypeScript
query(uri: string, metaJson: string, callback: AsyncCallback<string>) : void
```

Queries the attribute information about a file or directory based on a URI. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** stat(file: string | number, callback: AsyncCallback&lt;Stat&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | File or directory URI obtained from [FileInfo](arkts-corefile-fileaccess-fileinfo-i-sys.md). |
| metaJson | string | Yes | Attribute [FILEKEY](arkts-corefile-fileaccess-filekey-e-sys.md) to query. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | Callback used to return a JSON string that contains the file attribute and the value obtained. |

**Examples**

See [query](#query)

## registerObserver

```TypeScript
registerObserver(uri: string, notifyForDescendants: boolean, callback: Callback<NotifyMessage>): void
```

Registers a callback to listen for a URI. URIs and callbacks can be in many-to-many relationships. You are advised to use one callback to listen for one URI.

**Since:** 10

**Deprecated since:** 23

**Substitutes:** createWatcher

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file or directory. |
| notifyForDescendants | boolean | Yes | Whether to observe changes of the files in the directory. The value **true** means to observe changes of the files in the directory; the value **false** means the opposite. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NotifyMessage](arkts-corefile-fileaccess-notifymessage-i-sys.md)&gt; | Yes | Callback invoked to return the notification. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14300002 | Invalid uri |

## rename

```TypeScript
rename(uri: string, displayName: string) : Promise<string>
```

Renames a file or directory. This API uses a promise to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** rename(oldPath: string, newPath: string)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the selected file or directory. |
| displayName | string | Yes | Indicates the new directory or file name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | Returns a URI representing the new file or directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
async function renameFile01() {
  // A built-in storage directory is used as an example.
  // In the sample code, sourceDir indicates a file in the Download directory. The URI is the URI in fileInfo.
  // You can use the URI obtained.
  let sourceDir: string = "file://docs/storage/Users/currentUser/Download/1.txt";
  // Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
  let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
  try {
    if (fileAccessHelper != undefined) {
      let DestDir = await fileAccessHelper.rename(sourceDir, "testDir");
      console.info("rename success, DestDir: " + JSON.stringify(DestDir));
    }
  } catch (err) {
    let error: BusinessError = err as BusinessError;
    console.error("rename failed, errCode:" + error.code + ", errMessage:" + error.message);
  }
}
```

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';
// A built-in storage directory is used as an example.
// In the sample code, sourceDir indicates a file in the Download directory. The URI is the URI in fileInfo.
// You can use the URI obtained.
let sourceDir: string = "file://docs/storage/Users/currentUser/Download/1.txt";
// Obtain fileAccessHelper by referring to the sample code of fileAccess.createFileAccessHelper.
let fileAccessHelper : fileAccess.FileAccessHelper|undefined;
try {
  if (fileAccessHelper != undefined) {
    fileAccessHelper.rename(sourceDir, "testDir", (err: BusinessError, DestDir: string) => {
      if (err) {
        console.error("Failed to rename in async, errCode:" + err.code + ", errMessage:" + err.message);
      }
      console.info("rename success, DestDir: " + JSON.stringify(DestDir));
    });
  }
} catch (err) {
  let error: BusinessError = err as BusinessError;
  console.error("rename failed, errCode:" + error.code + ", errMessage:" + error.message);
}
```

## rename

```TypeScript
rename(uri: string, displayName: string, callback: AsyncCallback<string>): void
```

Renames a file or directory. This API uses an asynchronous callback to return the result.

**Since:** 9

**Deprecated since:** 23

**Substitutes:** rename(oldPath: string, newPath: string, callback: AsyncCallback&lt;void&gt;)

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | Indicates the selected file or directory. |
| displayName | string | Yes | Indicates the new directory or file name. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;string&gt; | Yes | The callback is used to return a URI representing the new file or directory. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 13900001 | Operation not permitted |
| 13900002 | No such file or directory |
| 13900004 | Interrupted system call |
| 13900006 | No such device or address |
| 13900008 | Bad file descriptor |
| 13900011 | Out of memory |
| 13900012 | Permission denied |
| 13900013 | Bad address |
| 13900014 | Device or resource busy |
| 13900015 | File exists |
| 13900017 | No such device |
| 13900018 | Not a directory |
| 13900019 | Is a directory |
| 13900020 | Invalid argument |
| 13900022 | Too many open files |
| 13900023 | Text file busy |
| 13900024 | File too large |
| 13900025 | No space left on device |
| 13900027 | Read-only file system |
| 13900029 | Resource deadlock would occur |
| 13900030 | File name too long |
| 13900033 | Too many symbolic links encountered |
| 13900034 | Operation would block |
| 13900038 | Value too large for defined data type |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |
| 14000001 | Invalid display name |
| 14000002 | Invalid uri |
| 14000003 | Invalid file extension |
| 14000004 | File has been put into trash bin |
| 14300001 | IPC error |
| 14300002 | Invalid uri |
| 14300003 | Fail to get fileextension info |
| 14300004 | Get wrong result |

**Examples**

See [rename](#rename)

## unregisterObserver

```TypeScript
unregisterObserver(uri: string, callback?: Callback<NotifyMessage>): void
```

Unregisters a callback that is used to listen for the specified URI.

**Since:** 10

**Deprecated since:** 23

**Required permissions:** ohos.permission.FILE_ACCESS_MANAGER

**System capability:** SystemCapability.FileManagement.UserFileService

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uri | string | Yes | URI of the file or directory. |
| callback | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-callback-i.md)&lt;[NotifyMessage](arkts-corefile-fileaccess-notifymessage-i-sys.md)&gt; | No | Callback to unregister. If this parameter is not specified, all callbacks of the specified URI will be unregistered. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| 14300002 | Invalid uri |
