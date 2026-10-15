# getDisposedRule (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getDisposedRule

```TypeScript
function getDisposedRule(appId: string, appIndex?: number): DisposedRule
```

Obtains the disposed rule of an application or an application clone.

**Since:** 11

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

<!--Device-appControl-function getDisposedRule(appId: string, appIndex?: int): DisposedRule--><!--Device-appControl-function getDisposedRule(appId: string, appIndex?: int): DisposedRule-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appId | string | Yes | appId or appIdentifier of the application whose disposed rule is to be obtained. A disposed rule set using appId can be obtained only through appId, and the same applies to a disposed rule set using appIdentifier.<br>**Note:** <br> appId is the unique identifier of the application, determined by the application bundle name and signature information. For details about how to obtain it, see [obtaining the appId of an application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appid-from-application-information). <br> [appIdentifier](../../../reference/apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) is also the unique identifier of the application. For details, see [what is appIdentifier](../../../quick-start/common-problem-of-application.md#what-is-appidentifier). For details about how to obtain it, see [obtaining the appIdentifier of an application](../../../quick-start/common-problem-of-application.md#how-do-i-obtain-appidentifier-from-application-information). |
| appIndex | number | No | Index of the application clone. The default value is **0**.<br> The value **0** means to obtain the disposed rule of the main application. A value greater than 0 means to obtain the disposed rule of the application clone with the specified index.<br>**Since:** 12 |

**Return value:**

| Type | Description |
| --- | --- |
| [DisposedRule](arkts-ability-appcontrol-disposedrule-i-sys.md) | Disposed rule of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [17700005](../errorcode-bundle.md#17700005-appid-is-an-empty-string) | The specified app ID is invalid. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex is not in the valid range.<br>**Applicable version:** 12 and later |

<!--Del-->
**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let appId = "com.example.myapplication_xxxxx";

try {
  let data = appControl.getDisposedRule(appId, 1);
  console.info('getDisposedRule successfully. Data: ' + JSON.stringify(data));
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedRule failed ' + message);
}
```

<!--DelEnd-->
