# WakeupManager (System API)

Implements wakeup management. @typedef WakeupManager

**Since:** 12

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { intelligentVoice } from '@kit.BasicServicesKit';
```

## clearUserData

```TypeScript
clearUserData(): Promise<void>
```

Clears user data.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (wakeupManager != null) {
  (wakeupManager as intelligentVoice.WakeupManager).clearUserData().then(() => {
    console.info(`Succeeded in clearing user data.`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to clear user data, Code:${err.code}, message:${err.message}`);
  });
}
```

## enrollWithWakeupFilesForResult

```TypeScript
enrollWithWakeupFilesForResult(wakeupFiles: Array<WakeupSourceFile>, wakeupInfo: string): Promise<EnrollResult>
```

Enrolls with wakeup files for result. This method uses a promise to return the enroll result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wakeupFiles | Array&lt;[WakeupSourceFile](arkts-basicservices-intelligentvoice-wakeupsourcefile-i-sys.md)&gt; | Yes | the wakeup source files needed. |
| wakeupInfo | string | Yes | wakeup information. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[EnrollResult](arkts-basicservices-intelligentvoice-enrollresult-e-sys.md)&gt; | the promise used to return the enroll result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700101](../errorcode-intelligentVoice.md#22700101-insufficient-memory) | No memory. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

let filesInfo: Array<intelligentVoice.WakeupSourceFile> = [];
filesInfo[0] = {filePath: "", fileContent: new ArrayBuffer(100)};
let wakeupInfo: string = "version: 123"

if (wakeupManager != null) {
  (wakeupManager as intelligentVoice.WakeupManager).enrollWithWakeupFilesForResult(
    filesInfo, wakeupInfo).then(
    (data: intelligentVoice.EnrollResult) => {
      let param: intelligentVoice.EnrollResult = data;
      console.info(`Succeeded in enrolling with wakeup files for result, param:${param}`);
    }).catch((err: BusinessError) => {
    console.error(`Failed to enroll with wakeup files for result, Code:${err.code}, message:${err.message}`);
  });
}
```

## getParameter

```TypeScript
getParameter(key: string): Promise<string>
```

Obtains the value of an intelligent voice parameter. This method uses a promise to return the query result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | the key of the intelligent voice parameter whose value is to be obtained. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;string&gt; | the promise used to return the value of the intelligent voice parameter. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (wakeupManager != null) {
  (wakeupManager as intelligentVoice.WakeupManager).getParameter('isEnrolled').then((data: string) => {
    let param: string = data;
    console.info(`Succeeded in getting parameter, param:${param}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get parameter, Code:${err.code}, message:${err.message}`);
  });
}
```

## getUploadFiles

```TypeScript
getUploadFiles (maxCount: number): Promise<Array<UploadFile>>
```

Obtains files needed to upload. This method uses a promise to return the files needed to upload.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| maxCount | number | Yes | the maximum count of upload files. The maxCount should be greater than 0 and smaller than 101 |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[UploadFile](arkts-basicservices-intelligentvoice-uploadfile-i-sys.md)&gt;&gt; | the promise used to return the upload files. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [22700101](../errorcode-intelligentVoice.md#22700101-insufficient-memory) | No memory. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (wakeupManager != null) {
  (wakeupManager as intelligentVoice.WakeupManager).getUploadFiles(2).then((data: Array<intelligentVoice.UploadFile>) => {
    let param: Array<intelligentVoice.UploadFile> = data;
    console.info(`Succeeded in getting upload files, param:${param}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get upload files, Code:${err.code}, message:${err.message}`);
  });
}
```

## getWakeupSourceFiles

```TypeScript
getWakeupSourceFiles(): Promise<Array<WakeupSourceFile>>
```

Obtains wakeup source files. This method uses a promise to return the wakeup source files.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WakeupSourceFile](arkts-basicservices-intelligentvoice-wakeupsourcefile-i-sys.md)&gt;&gt; | the promise used to return the wakeup source files. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [22700101](../errorcode-intelligentVoice.md#22700101-insufficient-memory) | No memory. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (wakeupManager != null) {
  (wakeupManager as intelligentVoice.WakeupManager).getWakeupSourceFiles().then(
    (data: Array<intelligentVoice.WakeupSourceFile>) => {
    let param: Array<intelligentVoice.WakeupSourceFile> = data;
    console.info(`Succeeded in getting wakeup source files, param:${param}`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to get wakeup source files, Code:${err.code}, message:${err.message}`);
  });
}
```

## setParameter

```TypeScript
setParameter(key: string, value: string): Promise<void>
```

Sets an intelligent voice parameter. This method uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.MANAGE_INTELLIGENT_VOICE

**System capability:** SystemCapability.AI.IntelligentVoice.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| key | string | Yes | the key of the intelligent voice parameter to set. |
| value | string | Yes | the value of the intelligent voice parameter to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | the promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Not system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [22700102](../errorcode-intelligentVoice.md#22700102-invalid-parameter) | Invalid parameter. |
| [22700107](../errorcode-intelligentVoice.md#22700107-system-error) | System error. |

**Examples**

```TypeScript
import { BusinessError } from '@kit.BasicServicesKit';

if (wakeupManager != null) {
  (wakeupManager as intelligentVoice.WakeupManager).setParameter('wakeup_phrase', 'xiaohuaxiaohua').then(() => {
    console.info(`Succeeded in setting parameter`);
  }).catch((err: BusinessError) => {
    console.error(`Failed to set parameter, Code:${err.code}, message:${err.message}`);
  });
}
```
