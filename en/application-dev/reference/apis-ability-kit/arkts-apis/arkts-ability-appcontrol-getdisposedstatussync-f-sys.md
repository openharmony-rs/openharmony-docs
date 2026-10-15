# getDisposedStatusSync (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getDisposedStatusSync

```TypeScript
function getDisposedStatusSync(appId: string): Want
```

Obtains the disposed status of an application. This API returns the result synchronously. If the operation is successful, the disposed status of the application is returned. If the operation fails, an error message is returned.

**Since:** 10

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

<!--Device-appControl-function getDisposedStatusSync(appId: string): Want--><!--Device-appControl-function getDisposedStatusSync(appId: string): Want-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | appId of the application to be queried. <br> appId is the unique identifier of the application, determined by the application bundle name and signature information. For details about how to obtain it, see [obtain the appId of an application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information). |

**Return value:**

| Type | Description |
| --- | --- |
| [Want](arkts-ability-app-ability-want-want-c.md) | Disposed status. |

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
import { Want } from '@kit.AbilityKit';

let appId: string = "com.example.myapplication_xxxxx";
let want: Want;

try {
  want = appControl.getDisposedStatusSync(appId);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedStatusSync failed ' + message);
}
```

<!--DelEnd-->
