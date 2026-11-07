# @ohos.file.environment (Directory Environment Capability)
<!--Kit: Core File Kit-->
<!--Subsystem: FileManagement-->
<!--Owner: @bao-yangyang; @maokelong95-->
<!--Designer: @Hun_Dun-->
<!--Tester: @zsyztt; @yue-ye2; @juxiaopang-->
<!--Adviser: @jinqiuheng-->
<!-- md-trans-meta sourceCommit=da2307b538d266f657e5c5a774d7aee48442267e translatedAt=2026-11-04T04:18:05.689Z pushedAt=2026-11-04T10:12:33.468Z nl=1 -->

This module provides user environment directory capabilities, used to obtain the sandbox paths of the user's download directory, desktop directory, and document directory. The three methods above are respectively applicable to scenarios of obtaining different types of user directories, and developers can select the corresponding directory type as needed.

> **NOTE**
>
> The initial APIs of this module are supported since API version 11. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { Environment } from '@kit.CoreFileKit';
```

## Environment.getUserDownloadDir

getUserDownloadDir(): string

Obtains the sandbox path of the current user's download directory.

**Required permissions**:

- API version 12+: NA
- API version 11: ohos.permission.READ_WRITE_DOWNLOAD_DIRECTORY

**System capability**: SystemCapability.FileManagement.File.Environment.FolderObtain

**Device behavior differences**
- Since API version 26.0.0, this API can be called on PCs, 2-in-1 devices, and tablets only. If it is called on other device types, error code 801 is returned.
- Before API version 26.0.0, this API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**Return value**

| Type                 | Description                 |
| --------------------- |---------------------|
| string | Return the sandbox path of the current user's download directory. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message      |
|----------| --------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken.<br>Applicable version: 11|
| 801      | Capability not supported. |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getUserDownloadDirExample() {
  try {
    let path = Environment.getUserDownloadDir();
    console.info(`Succeeded in getUserDownloadDir, path is ${path}`);
  } catch (err) {
    console.error(`Failed to getUserDownloadDir. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## Environment.getUserDesktopDir

getUserDesktopDir(): string

Obtains the sandbox path of the current user's desktop directory.

**Required permissions**:

- API version 12+: NA
- API version 11: ohos.permission.READ_WRITE_DESKTOP_DIRECTORY

**System capability**: SystemCapability.FileManagement.File.Environment.FolderObtain

**Device behavior differences**
- Since API version 26.0.0, this API can be called on PCs, 2-in-1 devices, and tablets only. If it is called on other device types, error code 801 is returned.
- Before API version 26.0.0, this API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**Return value**

| Type                 | Description                 |
| --------------------- |---------------------|
| string | Return Current user's desktop directory sandbox path. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message      |
|----------| --------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken.<br>Applicable version: 11|
| 801      | Capability not supported. |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getUserDesktopDirExample() {
  try {
    let path = Environment.getUserDesktopDir();
    console.info(`Succeeded in getUserDesktopDir, path is ${path}`);
  } catch (err) {
    console.error(`Failed to getUserDesktopDir. Code: ${err.code}, message: ${err.message}`);
  }
}
```

## Environment.getUserDocumentDir

getUserDocumentDir(): string

Obtains the sandbox path of the current user's document directory.

**Required permissions**:

- API version 12+: NA
- API version 11: ohos.permission.READ_WRITE_DOCUMENTS_DIRECTORY

**System capability**: SystemCapability.FileManagement.File.Environment.FolderObtain

**Device behavior differences**
- Since API version 26.0.0, this API can be called on PCs, 2-in-1 devices, and tablets only. If it is called on other device types, error code 801 is returned.
- Before API version 26.0.0, this API can be properly called on PCs/2-in-1 devices. If it is called on other devices, error code 801 is returned.

**Return value**

| Type                 | Description                 |
| --------------------- |---------------------|
| string | Returns the sandbox path of the current user's document directory. |

**Error codes**

For details about the error codes, see [Basic File IO Error Codes](errorcode-filemanagement.md#basic-file-io-error-codes) and [Universal Error Codes](../errorcode-universal.md).

| ID   | Error Message      |
|----------| --------- |
| 201 | Permission verification failed, usually the result returned by VerifyAccessToken.<br>Applicable version: 11|
| 801      | Capability not supported. |
| 13900042 | Unknown error. |

**Example**

```ts
import { BusinessError } from '@kit.BasicServicesKit';

function getUserDocumentDirExample() {
  try {
    let path = Environment.getUserDocumentDir();
    console.info(`Succeeded in getUserDocumentDir, path is ${path}`);
  } catch (err) {
    console.error(`Failed to getUserDocumentDir. Code: ${err.code}, message: ${err.message}`);
  }
}
```