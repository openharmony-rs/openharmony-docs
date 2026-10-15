# getUninstallDisposedRule (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getUninstallDisposedRule

```TypeScript
function getUninstallDisposedRule(appIdentifier: string, appIndex?: number): UninstallDisposedRule
```

Obtains the uninstall disposition rule with the highest priority that has been set for a specified application or application clone.

**Since:** 15

**Required permissions:** ohos.permission.GET_DISPOSED_APP_STATUS or ohos.permission.MANAGE_DISPOSED_APP_STATUS

<!--Device-appControl-function getUninstallDisposedRule(appIdentifier: string, appIndex?: int): UninstallDisposedRule--><!--Device-appControl-function getUninstallDisposedRule(appIdentifier: string, appIndex?: int): UninstallDisposedRule-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appIdentifier | string | Yes | appIdentifier of the application whose uninstall disposition rule is to be obtained. <br> If the application does not have an appIdentifier, appId can be used instead. appId is the unique identifier of the application, determined by the application Bundle name and signature information. For details about how to obtain it, see [obtain the appId of the application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information). |
| appIndex | number | No | Index of the application clone. The default value is **0**.<br> The value **0** means to obtain the uninstallation disposed rule of the main application. A value greater than 0 means to obtain the uninstallation disposed rule of the application clone. |

**Return value:**

| Type | Description |
| --- | --- |
| [UninstallDisposedRule](arkts-ability-appcontrol-uninstalldisposedrule-i-sys.md) | Uninstallation disposed rule. |

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
  let data = appControl.getUninstallDisposedRule(appIdentifier, 1);
  console.info('getUninstallDisposedRule successfully. Data: ' + JSON.stringify(data));
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getUninstallDisposedRule failed ' + message);
}
```

<!--DelEnd-->
