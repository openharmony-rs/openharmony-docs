# setApplicationEnabled (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, appIndex: number, isEnabled: boolean): Promise<void>
```

Enables or disables an application or an application clone. This API uses a promise to return the result.

**Since:** 12

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| appIndex | number | Yes | Index of the application clone.<br> The value **0** means to enable or disable the main application. A value greater than 0 means to enable or disable the application clone. |
| isEnabled | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |

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
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | AppIndex not in valid range. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.setApplicationEnabled(bundleName, 1, false).then(() => {
    hilog.info(0x0000, "testTag", "setApplicationEnabled successfully.");
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', message);
}
```


<a id="setapplicationenabled-1"></a>

## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, appIndex: number, isEnabled: boolean, killProcess: boolean): Promise<void>
```

Sets the enabled or disabled state of a specified application or application clone, and controls whether to exit the application process when the application is disabled. This API uses a promise to return the result.

**Since:** 26.0.0

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name of the application. |
| appIndex | number | Yes | Application index. The value is an integer ranging from 0 to 5. The value 0 indicates the main application, and the values 1 to 5 indicate the application clone indexes. |
| isEnabled | boolean | Yes | Whether to enable the application. The value true indicates that the application is enabled, and false indicates that the application is disabled. |
| killProcess | boolean | Yes | Whether to exit the application process when the application is disabled. The value true indicates that the application process exits when the application is disabled, and false indicates that the application process does not exit when the application is disabled. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied. Non-system APP calling system API. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundle is not found. |
| [17700061](../errorcode-bundle.md#17700061-appindex-for-a-clone-is-invalid) | The specified app index is invalid. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

// Replace with the application bundle name, application index, and whether to enable the application and whether to exit the application process when the application is disabled.
let bundleName: string = 'com.example.myapplication';
let appIndex: number = 0;
let isEnabled: boolean = true;
let killProcess: boolean = false;

try {
  bundleManager.setApplicationEnabled(bundleName, appIndex, isEnabled, killProcess)
    .then(() => {
      hilog.info(0x0000, 'testTag', 'setApplicationEnabled successfully');
    })
    .catch((err: BusinessError) => {
      hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', err.message);
    });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', message);
}
```


<a id="setapplicationenabled-2"></a>

## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, isEnabled: boolean, callback: AsyncCallback<void>): void
```

Enables or disables an application. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| isEnabled | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.setApplicationEnabled(bundleName, false, err => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'setApplicationEnabled successfully.');
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', message);
}
```


<a id="setapplicationenabled-3"></a>

## setApplicationEnabled

```TypeScript
function setApplicationEnabled(bundleName: string, isEnabled: boolean): Promise<void>
```

Enables or disables an application. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.CHANGE_ABILITY_ENABLED_STATE

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| isEnabled | boolean | Yes | Whether to enable the application. **true** to enable, **false** otherwise. |

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

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = "com.ohos.myapplication";

try {
  bundleManager.setApplicationEnabled(bundleName, false).then(() => {
    hilog.info(0x0000, "testTag", "setApplicationEnabled successfully.");
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'setApplicationEnabled failed: %{public}s', message);
}
```
