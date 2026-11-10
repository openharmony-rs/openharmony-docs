# @ohos.file.securityLabel (Data Label)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=6c0893247bd78c129e32a38e52ccc47805b1914a translatedAt=2026-11-03T04:38:32.848Z pushedAt=2026-11-04T05:56:42.496Z nl=1 -->

This module provides functions related to file data security levels: it provides ArkTS APIs for applications to query and set file data security levels. This function helps applications implement hierarchical management and access control for files of different security levels, addressing the need for data security control and improving the data security compliance of applications.

> **NOTE**
>
> The initial APIs of this module are supported since API version 9. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { securityLabel } from '@kit.CoreFileKit';
```

## How to Use

Before using this function module to operate on files/directories, you need to obtain the app sandbox path pathDir. For how to obtain the sandbox path and how to use the related APIs, see [Application Context - Obtaining the Application File Path](../../application-models/application-context-stage.md#obtaining-application-file-paths).

## DataLevel

type DataLevel = 's0' | 's1' | 's2' | 's3' | 's4'

Represents the data security level.

**System capability**: SystemCapability.FileManagement.File.FileIO

| Type| Description|
| --- | ---------------- |
| 's0' | Data security level "S0". |
| 's1' | Data security level "S1". |
| 's2' | Data security level "S2". |
| 's3' | Data security level "S3". |
| 's4' | Data security level "S4". |

For details, see [Data Security Labels](../../database/access-control-by-device-and-data-level.md#data-security-labels).


## securityLabel.setSecurityLabel

setSecurityLabel(path:string, type:DataLevel):Promise&lt;void&gt;

Sets the data security level of a file or directory to implement hierarchical management and access control of files. This API uses a promise asynchronous callback.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name   | Type      | Mandatory| Description                                        |
| --------- | ------    | ---- | -------------------------------------------- |
| path      | string    | Yes   | App sandbox path of the file or directory.                                     |
| type      | [DataLevel](#datalevel) | Yes   | Data security level. Only supports "s0", "s1", "s2", "s3", "s4".<br>**Note**: The data security level can only be set from low to high or same level. |

**Return value**

  | Type               | Description            |
  | ------------------- | ---------------- |
  | Promise&lt;void&gt; | Promise that returns no value.|

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let filePath = pathDir + '/test.txt';
  securityLabel.setSecurityLabel(filePath, "s0").then(() => {
    console.info("Succeeded in setting security label.");
  }).catch((err: BusinessError) => {
    console.error("Failed to set security label. Code: " + err.code + ", message: " + err.message);
  });
  ```

## securityLabel.setSecurityLabel

setSecurityLabel(path:string, type:DataLevel, callback: AsyncCallback&lt;void&gt;):void

Sets the data security level of a file or directory to implement hierarchical management and access control of files. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name   | Type                     | Mandatory| Description                                        |
| --------- | ------------------------- | ---- | -------------------------------------------- |
| path      | string                    | Yes  | App sandbox path of the file or directory.                                      |
| type      | [DataLevel](#datalevel)   | Yes  | Data security level. Only "s0", "s1", "s2", "s3", and "s4" are supported.<br>**Note**: The data security level can only be set from low to high or to the same level. |
| callback  | AsyncCallback&lt;void&gt; | Yes  | Callback used to return the result. If the data security level is set successfully, **err** is **undefined**; otherwise, **err** is an error object.                   |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let filePath = pathDir + '/test.txt';
  securityLabel.setSecurityLabel(filePath, "s0", (err: BusinessError) => {
    if (err) {
      console.error("Failed to set security label. Code: " + err.code + ", message: " + err.message);
    } else {
      console.info("Succeeded in setting security label.");
    }
  });
  ```

## securityLabel.setSecurityLabelSync

setSecurityLabelSync(path:string, type:DataLevel):void

Sets the data security level of a file or directory using a synchronous method to implement hierarchical management and access control of files.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name   | Type  | Mandatory| Description                                        |
| --------- | ------ | ---- | -------------------------------------------- |
| path      | string | Yes   | App sandbox path of the file or directory.                                      |
| type      | [DataLevel](#datalevel) | Yes   | Data security level. Only "s0", "s1", "s2", "s3", and "s4" are supported.<br>**Note**: The data security level can only be set from low to high or to the same level. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Example**

```ts
let filePath = pathDir + '/test.txt';
securityLabel.setSecurityLabelSync(filePath, "s0");
```

## securityLabel.getSecurityLabel

getSecurityLabel(path:string):Promise&lt;string&gt;

Obtains the data security level of a file or directory. If no data security level has been set, **s3** is returned by default. This API uses a promise to return the result.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name| Type  | Mandatory| Description    |
  | ------ | ------ | ---- | -------- |
  | path   | string | Yes   | App sandbox path of the file or directory.  |

**Return value**

  | Type                 | Description        |
  | --------------------- | ------------ |
  | Promise&lt;string&gt; | Promise object, which returns the data security level. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let filePath = pathDir + '/test.txt';
  securityLabel.getSecurityLabel(filePath).then((type: string) => {
    console.info("Succeeded in getting security label, Label: " + type);
  }).catch((err: BusinessError) => {
    console.error("Failed to get security label. Code: " + err.code + ", message: " + err.message);
  });
  ```

## securityLabel.getSecurityLabel

getSecurityLabel(path:string, callback:AsyncCallback&lt;string&gt;): void

Obtains the data security level of a file or directory. If no data security level has been set, **s3** is returned by default. This API uses an asynchronous callback to return the result.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

  | Name  | Type                       | Mandatory| Description                      |
  | -------- | --------------------------- | ---- | -------------------------- |
  | path     | string                      | Yes  | App sandbox path of the file or directory.                  |
  | callback | AsyncCallback&lt;string&gt; | Yes  | Callback function. When the data security level of the file or directory is obtained, err is undefined and type is the obtained data security level; otherwise, it is an error object. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Example**

  ```ts
  import { BusinessError } from '@kit.BasicServicesKit';
  let filePath = pathDir + '/test.txt';
  securityLabel.getSecurityLabel(filePath, (err: BusinessError, type: string) => {
    if (err) {
      console.error("Failed to get security label. Code: " + err.code + ", message: " + err.message);
    } else {
      console.info("Succeeded in getting security label, Label: " + type);
    }
  });
  ```

## securityLabel.getSecurityLabelSync

getSecurityLabelSync(path:string):string

Obtains the data security level of a file or directory in synchronous mode. If no data security level has been set, **s3** is returned by default.

**System capability**: SystemCapability.FileManagement.File.FileIO

**Parameters**

| Name| Type  | Mandatory| Description    |
| ------ | ------ | ---- | -------- |
| path   | string | Yes   | App sandbox path of the file or directory.  |

**Return value**

| Type  | Description        |
| ------ | ------------ |
| string | Promise used to return the data security level.|

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes).

| ID| Error Message|
| -------- | -------- |
| 13900001 | Operation not permitted |
| 13900007 | Arg list too long |
| 13900015 | File exists |
| 13900020 | Invalid argument |
| 13900025 | No space left on device |
| 13900037 | No data available |
| 13900041 | Quota exceeded |
| 13900042 | Unknown error |

**Example**

```ts
let filePath = pathDir + '/test.txt';
let type = securityLabel.getSecurityLabelSync(filePath);
console.info("Succeeded in getting security label, Label: " + type);
```
