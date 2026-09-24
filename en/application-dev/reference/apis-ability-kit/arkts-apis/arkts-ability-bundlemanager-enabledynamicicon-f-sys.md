# enableDynamicIcon (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## enableDynamicIcon

```TypeScript
function enableDynamicIcon(bundleName: string, moduleName: string): Promise<void>
```

Enables the dynamic icon based on the given bundle name and module name. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.ACCESS_DYNAMIC_ICON

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name based on which the dynamic icon is to be enabled. |
| moduleName | string | Yes | Module name based on which the dynamic icon is to be enabled. |

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
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified moduleName is not found. |
| [17700304](../errorcode-bundle.md#17700304-failed-to-enable-the-dynamic-icon) | Failed to enable the dynamic icon. |
| [17700307](../errorcode-bundle.md#17700307-dynamic-icon-does-not-take-effect-because-of-a-custom-theme) | Dynamic icons cannot take effect due to existing custom themes.<br>**Applicable version:** 20 and later |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let moduleName: string = 'moduleTest';

try {
  bundleManager.enableDynamicIcon(bundleName, moduleName).then((data) => {
    hilog.info(0x0000, 'testTag', 'enableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', message);
}
```


<a id="enabledynamicicon-1"></a>

## enableDynamicIcon

```TypeScript
function enableDynamicIcon(bundleName: string, moduleName: string, option?: BundleOptions): Promise<void>
```

Enables the dynamic icon based on the given bundle name, module name, and bundle options. This API uses a promise to return the result.

To enable the dynamic icon for the current user, you must request the ohos.permission.ACCESS_DYNAMIC_ICON permission.

To enable the dynamic icon for another user, you must request the ohos.permission.ACCESS_DYNAMIC_ICON and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS permissions.

**Since:** 20

**Required permissions:** ohos.permission.ACCESS_DYNAMIC_ICON or (ohos.permission.ACCESS_DYNAMIC_ICON and ohos.permission.INTERACT_ACROSS_LOCAL_ACCOUNTS)

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name based on which the dynamic icon is to be enabled. |
| moduleName | string | Yes | Module name based on which the dynamic icon is to be enabled. |
| option | [BundleOptions](arkts-ability-bundle-bundleoptions-i.md) | No | User and application clone index based on which the dynamic icon is to be enabled. By default, the dynamic icon is enabled for all users and all application clones. |

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
| [17700002](../errorcode-bundle.md#17700002-module-name-does-not-exist) | The specified moduleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range. |
| [17700304](../errorcode-bundle.md#17700304-failed-to-enable-the-dynamic-icon) | Failed to enable the dynamic icon. |
| [17700307](../errorcode-bundle.md#17700307-dynamic-icon-does-not-take-effect-because-of-a-custom-theme) | Dynamic icons cannot take effect due to existing custom themes. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName: string = 'com.ohos.demo';
let moduleName: string = 'moduleTest';
let option: bundleManager.BundleOptions = { 'userId': 100, 'appIndex': 0 };

try {
  bundleManager.enableDynamicIcon(bundleName, moduleName, option).then(() => {
    hilog.info(0x0000, 'testTag', 'enableDynamicIcon successfully');
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'enableDynamicIcon failed. Cause: %{public}s', message);
}
```
