# setAppClonePreference (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setAppClonePreference

```TypeScript
function setAppClonePreference(bundleName: string, appClonePreference: AppClonePreference): Promise<void>
```

Sets the application clone preference configuration.

**Since:** 26.0.0

**Required permissions:** ohos.permission.MANAGE_CLONE_BUNDLE_PREFERENCES

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the target application. |
| appClonePreference | [AppClonePreference](arkts-ability-bundlemanager-appclonepreference-t-sys.md) | Yes | Application clone preference configuration to set. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | The specified app index is invalid. |
| [17700094](../errorcode-bundle.md#17700094-the-specified-application-has-not-created-a-clone) | The specified bundle did not create a clone. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appClonePreference: bundleManager.AppClonePreference = {
  mode: bundleManager.AppClonePreferenceMode.CLONE_APP,
  appIndex: 1
};

try {
  bundleManager.setAppClonePreference(bundleName, appClonePreference).then(() => {
    hilog.info(0x0000, 'testTag', 'setAppClonePreference successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'setAppClonePreference failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setAppClonePreference failed. Cause: %{public}s', message);
}
```
