# deleteUninstallDisposedRule (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## deleteUninstallDisposedRule

```TypeScript
function deleteUninstallDisposedRule(appIdentifier: string, appIndex?: number): void
```

Deletes an uninstallation disposed rule for an application or an application clone.

**Since:** 15

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function deleteUninstallDisposedRule(appIdentifier: string, appIndex?: int): void--><!--Device-appControl-function deleteUninstallDisposedRule(appIdentifier: string, appIndex?: int): void-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appIdentifier | string | Yes | appIdentifier of the application whose uninstall disposition rule is to be deleted. <br> If the application does not have an appIdentifier, appId can be used instead. appId is the unique identifier of the application, determined by the application Bundle name and signature information. For how to obtain it, see [Obtaining the appId of an Application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information). |
| appIndex | number | No | Index of the application clone. The default value is **0**.<br> The value **0** means to delete the uninstallation disposed rule of the main application. A value greater than 0 means to delete the uninstallation disposed rule of the application clone. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex is not in the valid range. |
| [17700074](../errorcode-bundle.md#17700074-invalid-appidentifier) | The specified appIdentifier is invalid. |

<!--Del-->
**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appIdentifier = "com.example.myapplication_xxxxx";

try {
  appControl.deleteUninstallDisposedRule(appIdentifier, 1);
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('deleteUninstallDisposedRule failed ' + message);
}
```

<!--DelEnd-->
