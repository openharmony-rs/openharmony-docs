# getDisposedRulesByBundle (System API)

## Modules to Import

```TypeScript
import { appControl } from '@kit.AbilityKit';
```

## getDisposedRulesByBundle

```TypeScript
function getDisposedRulesByBundle(bundleName: string): Array<DisposedRuleConfiguration>
```

Obtains all disposed rules set for a specified application bundle.

**Since:** 23

**Required permissions:** ohos.permission.MANAGE_DISPOSED_APP_STATUS or ohos.permission.GET_DISPOSED_APP_STATUS

**Model restriction:** This API can be used only in the stage model.

<!--Device-appControl-function getDisposedRulesByBundle(bundleName: string): Array<DisposedRuleConfiguration>--><!--Device-appControl-function getDisposedRulesByBundle(bundleName: string): Array<DisposedRuleConfiguration>-End-->

**System capability:** SystemCapability.BundleManager.BundleFramework.AppControl

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application bundle for which the disposed rule is set. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[DisposedRuleConfiguration](arkts-ability-appcontrol-disposedruleconfiguration-i-sys.md)&gt; | Disposed rules set for the specified application bundle. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. A non-system application is not allowed to call a system API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |

<!--Del-->
**Examples**

```TypeScript
import { appControl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let bundleName = 'com.example.myapplication';

try {
  let data = appControl.getDisposedRulesByBundle(bundleName);
  console.info('getDisposedRulesByBundle successfully. Data: ' + JSON.stringify(data));
} catch (error) {
  let message = (error as BusinessError).message;
  console.error('getDisposedRulesByBundle failed ' + message);
}
```

<!--DelEnd-->
