# @ohos.logLibrary (Log Library) (System API)

<!--Kit: Performance Analysis Kit-->
<!--Subsystem: HiviewDFX-->
<!--Owner: @BruceZong-->
<!--Designer: @tangyyan-->
<!--Tester: @gcw_KuLfPSbe-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=0af997246107d09b2a367d4231ebe4a7139f8fdb translatedAt=2026-11-16T01:13:33.037Z pushedAt=2026-11-20T07:28:38.917Z nl=1 -->

This module provides APIs such as list, copy, move, and remove to query, copy, move, and delete system DFX log files.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
> - The APIs provided by this module are system APIs.

## Modules to Import

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
```

## LogEntry

Defines a **LogEntry** object.

**System capability**: SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API**: This is a system API.

| Name| Type| Read-Only| Optional| Description|
| -------- | -------- | -------- | -------- | -------- |
| name | string | No| No| Log file name. |
| mtime | number | No| No | Time of the last modification to the file. The value is the number of seconds elapsed since 00:00:00 on January 1, 1970.|
| size | number | No| No | File size, in bytes.|

## logLibrary.list

list(logType: string): LogEntry[]

Obtains the list of log files of the specified type in synchronous mode. This API accepts objects of the string type as input parameters and returns a list log files of the specified type.

Usage scenario: The application needs to obtain the list of log files of a specific type during problem locating or log analysis. After the list is obtained, it can be used with APIs such as copy, move, and remove to perform log operations, such as log archiving and cleanup.

**Required permission**: ohos.permission.READ_HIVIEW_SYSTEM

**System capability**: SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API**: This is a system API.

**Parameters**

| Name   | Type                     | Mandatory| Description                                                        |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | Yes | Log type string. The value must be a system-registered log type (for example, "HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"). The API returns error code 401 when the value is out of range. |

**Return value**

| Type               | Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| [LogEntry](#logentry)[] | Array of log file objects, containing all log files of the specified type. Each **LogEntry** object contains the file name (**name**), modification time (**mtime**), and file size (**size**) information, which can be used for subsequent copy, move, or delete operations. |

**Error codes**

For details about the error codes, see [Log Library Error Codes](errorcode-loglibrary-sys.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied.  |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |

**Example**

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('HILOG');
  // do something here.
} catch (error) {
  console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

## logLibrary.copy

copy(logType: string, logName: string, dest: string): Promise&lt;void&gt;

Copies the specified file of the specified log type to the target application directory. After the call is successful, a new log file will be created in the target directory, and the original file remains unchanged. This API uses a promise to return the result.

Usage scenario: When the application needs to back up logs or upload logs to a server, it can copy the log file to the application directory.

**Required permission**: ohos.permission.READ_HIVIEW_SYSTEM

**System capability**: SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API**: This is a system API.

**Parameters**

| Name   | Type                   | Mandatory| Description|
| --------- | ----------------------- | ---- | --------------- |
| logType | string | Yes | Log type string. The value range is as follows: it must be a system-registered log type (for example, "HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"). If the value is out of range, error code 401 is returned. |
| logName | string | Yes | Log file name. You must first call the logLibrary.list method to query the log file list, select the file to operate on, and use the LogEntry.name field as the parameter value. If an empty string, a non-existent file name, or an invalid file name is passed, error code 21300001 is returned. |
| dest | string | Yes | Target directory. A relative directory name must be filled in, and only valid directory name characters are supported. After the dest string is passed, the log file will be saved to the "hiview/\<dest>" folder under the application cache path, that is, "../cache/hiview/\<dest>". Multiple levels of directories can be filled in.<br>If an empty string is passed, the file will be saved to the root directory, that is, the hiview folder under the application cache path. If an invalid directory name is passed, error code 401 is returned. |

**Return value**

| Type               | Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise object. When resolved, no return value indicates a successful copy; when rejected, it throws a BusinessError object indicating a copy failure. |

**Error codes**

For details about the error codes, see [Log Library Error Codes](errorcode-loglibrary-sys.md).

| ID| Error Message|
| -------- | ---------------------------------------------------------------- |
| 201 | Permission denied.  |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exist.  |

**Example**

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logFiles = logLibrary.list('HILOG');
  if (logFiles.length > 0) {
    logLibrary.copy('HILOG', logFiles[0].name, ''
    ).then(
      (copyResult) => {
        // do something here.
      }
    ).catch(
      (err: BusinessError) => {
        // do something here.
      }
    )
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

## logLibrary.copy

copy(logType: string, logName: string, dest: string, callback: AsyncCallback&lt;void&gt;): void

Copies the specified file of the specified log type to the target application directory. After the call is successful, a new log file will be created in the target directory, and the original file remains unchanged. This API uses an asynchronous callback to return the result.

Usage scenario: when the application needs to back up logs or upload logs to a server, it can copy the log file to the application directory.

**Required permission**: ohos.permission.READ_HIVIEW_SYSTEM

**System capability**: SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API**: This is a system API.

**Parameters**

| Name   | Type                     | Mandatory| Description                                                        |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | Yes | Log type string. The value range is as follows: it must be a system-registered log type (for example, "HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"). If the value is out of range, error code 401 is returned. |
| logName | string | Yes | Log file name. You must first use the logLibrary.list method to query the log file list, select the file to operate on, and use the LogEntry.name field as the parameter value. If an empty string, a non-existent file name, or an invalid file name is passed, error code 21300001 is returned. |
| dest | string | Yes | Target directory. A relative directory name must be filled in, and only valid directory name characters are supported. After the dest string is passed, the log file will be saved to the "hiview/\<dest>" folder under the application cache path, that is, "../cache/hiview/\<dest>". Multiple levels of directories can be filled in.<br>If an empty string is passed, the file will be saved to the root directory, that is, the hiview folder under the application cache path. If an invalid directory name is passed, error code 401 is returned. |
| callback  | AsyncCallback&lt;void&gt; | Yes | Callback used to receive the operation result. Callback parameter: the first parameter is an error object (BusinessError type, null on success). On success, err is null. On failure, obtain the error code through err.code and the error description through err.message. For the meaning of the error code, see the error code table below. |

**Error codes**

For details about the error codes, see [Log Library Error Codes](errorcode-loglibrary-sys.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied.  |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exist.  |

**Example**

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('HILOG');
  if (logFiles.length > 0) {
    logLibrary.copy('HILOG', logFiles[0].name, 'dir1', (error, copyResult) => {
      if (error) {
        console.error(`Failed to copy log file. Code: ${error.code}, message: ${error.message}`);
      } else {
        // copy success.
      }
    });
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

## logLibrary.move

move(logType: string, logName: string, dest: string): Promise&lt;void&gt;

Moves the specified file of the specified log type to the target application directory. After the call is successful, the original file will be deleted, and a new log file will be created in the target directory. This API uses a promise to return the result.

Usage scenario: When the application needs to archive or organize logs, it can move the log file to the specified directory.

**Required permission**: ohos.permission.WRITE_HIVIEW_SYSTEM

**System capability**: SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API**: This is a system API.

**Parameters**

| Name   | Type                   | Mandatory| Description|
| --------- | ----------------------- | ---- | --------------- |
| logType | string | Yes | Log type string. The value range is as follows: it must be a system-registered log type (for example, "HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"). It returns error code 401 when the value is out of range. |
| logName | string | Yes | Log file name. You must first use the logLibrary.list method to query the log file list, select the file to operate on, and use the LogEntry.name field as the parameter value. It returns error code 21300001 when an empty string, a non-existent file name, or an invalid file name is passed. |
| dest | string | Yes | Target directory. A relative directory name must be filled in, and only valid directory name characters are supported. After the dest string is passed, the log file will be saved to the "hiview/\<dest>" folder under the application cache path, that is, "../cache/hiview/\<dest>". Multiple levels of directories can be filled in.<br>If an empty string is passed, it will be saved to the root directory, that is, the hiview folder under the application cache path. It returns error code 401 when an invalid directory name is passed. |

**Return value**

| Type               | Description                                                        |
| ------------------- | ------------------------------------------------------------ |
| Promise&lt;void&gt; | Promise object. Resolving with no return value indicates a successful move, and rejecting throws a **BusinessError** object indicating a move failure. |

**Error codes**

For details about the error codes, see [Log Library Error Codes](errorcode-loglibrary-sys.md).

| ID| Error Message|
| -------- | ---------------------------------------------------------------- |
| 201 | Permission denied.  |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exist.  |

**Example**

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';
import { BusinessError } from '@kit.BasicServicesKit';

try {
  let logFiles = logLibrary.list('FAULTLOG');
  if (logFiles.length > 0) {
    logLibrary.move('FAULTLOG', logFiles[0].name, ''
    ).then(
      (val) => {
        // do something here.
      }
    ).catch(
      (err: BusinessError) => {
        // do something here.
      }
    )
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

## logLibrary.move

move(logType: string, logName: string, dest: string, callback: AsyncCallback&lt;void&gt;): void

Moves the specified file of the specified log type to the target application directory. After the call is successful, the original file will be deleted, and a new log file will be created in the target directory. This API uses an asynchronous callback to return the result.

Usage scenario: When the application needs to archive or organize logs, it can move the log file to the specified directory.

**Required permission**: ohos.permission.WRITE_HIVIEW_SYSTEM

**System capability**: SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API**: This is a system API.

**Parameters**

| Name   | Type                     | Mandatory| Description                                                        |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | Yes | Log type string. The value must be a system-registered log type (for example, "HILOG", "FAULTLOG", "BETACLUB", or "REMOTELOG"). If the value is out of range, error code 401 is returned. |
| logName | string | Yes   | Log file name. You must first call the logLibrary.list method to query the log file list, select the file to operate on, and use the LogEntry.name field as the parameter value. If an empty string, a non-existent file name, or an invalid file name is passed, error code 21300001 is returned. |
| dest | string | Yes   | Target directory. A relative directory name must be filled in, and only valid directory name characters are supported. After the dest string is passed, the log file will be saved to the "hiview/\<dest>" folder under the application cache path, that is, "../cache/hiview/\<dest>". Multiple levels of directories can be filled in.<br>If an empty string is passed, the file will be saved to the root directory, that is, the hiview folder under the application cache path. If an invalid directory name is passed, error code 401 is returned. |
| callback  | AsyncCallback&lt;void&gt; | Yes | Callback function used to receive the operation result. Callback parameter: the first parameter is an error object (of the BusinessError type, null on success). On success, err is null; on failure, obtain the error code through err.code and the error description through err.message. For the meaning of the error code, see the error code table below. |

**Error codes**

For details about the error codes, see [Log Library Error Codes](errorcode-loglibrary-sys.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied.  |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exist.  |

**Example**

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('FAULTLOG');
  if (logFiles.length > 0) {
    logLibrary.move('FAULTLOG', logFiles[0].name, 'dir1/dir2', (error, moveResult) => {
      if (error) {
        console.error(`Failed to move log file. Code: ${error.code}, message: ${error.message}`);
      } else {
        // move success.
      }
    });
  }
} catch (error) {
    console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```

## logLibrary.remove

remove(logType: string, logName: string): void

Deletes log files of the specified type in synchronous mode.

Usage scenario: When the application needs to clean up expired logs or free up storage space, it can delete log files that are no longer needed.

**Required permission**: ohos.permission.WRITE_HIVIEW_SYSTEM

**System capability**: SystemCapability.HiviewDFX.Hiview.LogLibrary

**System API**: This is a system API.

**Parameters**

| Name   | Type                     | Mandatory| Description                                                        |
| --------- | ------------------------- | ---- | ------------------------------------------------------------ |
| logType | string | Yes | Log type string. The value range is as follows: it must be a system-registered log type (for example, "HILOG", "FAULTLOG", "BETACLUB", "REMOTELOG"). Error code 401 is returned when the value is out of range. |
| logName | string | Yes | Log file name. You must first call the **logLibrary.list** method to query the log file list, select the file to operate on, and use the LogEntry.name field as the parameter value. Error code 21300001 is returned when an empty string, a non-existent file name, or an invalid file name is passed. |

**Error codes**

For details about the error codes, see [Log Library Error Codes](errorcode-loglibrary-sys.md).

| ID| Error Message|
| ------- | ----------------------------------------------------------------- |
| 201 | Permission denied.  |
| 202 | Permission denied, non-system app called system api. |
| 401 | Invalid argument. Possible causes:<br>1. Mandatory parameters are left unspecified.<br>2. Incorrect parameter types.<br>3. Parameter verification failed. |
| 21300001 | Source file does not exist.  |

**Example**

```ts
import { logLibrary } from '@kit.PerformanceAnalysisKit';

try {
  let logFiles = logLibrary.list('FAULTLOG');
  if (logFiles.length > 0) {
    logLibrary.remove('FAULTLOG', logFiles[0].name);
  }
} catch (error) {
  console.error(`Failed to call logLibrary API. Code: ${error?.code}, message: ${error?.message}`);
}
```