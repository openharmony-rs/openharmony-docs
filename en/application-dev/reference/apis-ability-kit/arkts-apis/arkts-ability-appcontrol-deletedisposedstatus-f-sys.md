# deleteDisposedStatus (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

<a id="deletedisposedstatus1"></a>

## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void
```

Deletes the disposed status for an application. This API uses an asynchronous callback to return the result. If the operation is successful, **null** is returned. If the operation fails, an error message is returned.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void--><!--Device-appControl-function deleteDisposedStatus(appId: string, callback: AsyncCallback<void>): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | appId or appIdentifier of the application whose disposition status is to be deleted. A disposition status set using appId can only be deleted using appId, and the same applies to one set using appIdentifier.<br>**Note:** <br> appId is the unique identifier of the application, determined by the application bundle name and signature information. For details about how to obtain it, see [obtain the appId of the application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information). <br> [appIdentifier](../../../reference/apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) is also the unique identifier of the application. For detailed information, see [what is appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier). For details about how to obtain it, see [obtain the appIdentifier of the application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appidentifier-from-application-information). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback function. If the disposition status is deleted successfully, err returns null; otherwise, the callback function returns a specific error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-appid-is-an-empty-string) | The specified app ID is empty string. |

<!--Del-->
**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";
try {
  appControl.deleteDisposedStatus(appId, (error: BusinessError, data) => {
    if (error) {
      console.error('deleteDisposedStatus failed ' + error.message);
      return;
    }
    console.info('deleteDisposedStatus success');
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}
```

<!--DelEnd-->


<a id="deletedisposedstatus2"></a>

## deleteDisposedStatus

```TypeScript
function deleteDisposedStatus(appId: string): Promise<void>
```

Deletes the disposition status of an application. This API uses a promise to return the result. null is returned on success, and the corresponding error message is returned on failure.

**Since:** 9

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function deleteDisposedStatus(appId: string): Promise<void>--><!--Device-appControl-function deleteDisposedStatus(appId: string): Promise<void>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | appId or appIdentifier of the application whose disposition status is to be deleted. The disposition status set using appId can only be deleted using appId, and the same applies to the disposition status set using appIdentifier.<br>**NOTE:** <br> appId is the application's unique identifier, determined by the application Bundle name and signature information. For how to obtain it, see [obtain the appId of the application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information). <br> [appIdentifier](../../../reference/apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) is also the application's unique identifier. For detailed information, refer to [what is appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier). For how to obtain it, see [obtain the appIdentifier of the application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appidentifier-from-application-information). |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-appid-is-an-empty-string) | The specified app ID is empty string. |

<!--Del-->
**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";

try {
  appControl.deleteDisposedStatus(appId)
    .then(() => {
      console.info('deleteDisposedStatus success');
    }).catch((error: BusinessError) => {
    let message = (error as BusinessError).message;
    console.error('deleteDisposedStatus failed ' + message);
  });
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteDisposedStatus failed ' + message);
}
```

<!--DelEnd-->
