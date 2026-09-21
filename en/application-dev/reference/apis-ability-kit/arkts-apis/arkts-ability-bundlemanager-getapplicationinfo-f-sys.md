# getApplicationInfo (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getApplicationInfo

```TypeScript
function getApplicationInfo(bundleName: string, appFlags: number, callback: AsyncCallback<ApplicationInfo>): void
```

Obtains the application information based on the given bundle name and application flags. This API uses an asynchronous callback to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| appFlags | number | Yes | Type of the application information to obtain. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the application information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_WITH_PERMISSION;

try {
  bundleManager.getApplicationInfo(bundleName, appFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getApplicationInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getApplicationInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationInfo failed: %{public}s', message);
}
```


<a id="getapplicationinfo-1"></a>

## getApplicationInfo

```TypeScript
function getApplicationInfo(bundleName: string, appFlags: number, userId: number, callback: AsyncCallback<ApplicationInfo>): void
```

Obtains the application information based on the given bundle name, application flags, and user ID. This API uses an asynchronous callback to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| appFlags | number | Yes | Type of the application information to obtain. |
| userId | number | Yes | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;[ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md)&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the application information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;
let userId = 100;

try {
  bundleManager.getApplicationInfo(bundleName, appFlags, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getApplicationInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getApplicationInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationInfo failed: %{public}s', message);
}
```


<a id="getapplicationinfo-2"></a>

## getApplicationInfo

```TypeScript
function getApplicationInfo(bundleName: string, appFlags: number, userId?: number): Promise<ApplicationInfo>
```

Obtains the application information based on the given bundle name, application flags, and user ID. This API uses a promise to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| bundleName | string | Yes | Bundle name. |
| appFlags | number | Yes | Type of the application information to obtain. |
| userId | number | No | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller. The value must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md)&gt; | Promise used to return the application information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let bundleName = 'com.example.myapplication';
let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_WITH_PERMISSION;
let userId = 100;

try {
  bundleManager.getApplicationInfo(bundleName, appFlags, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'getApplicationInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getApplicationInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getApplicationInfo failed. Cause: %{public}s', message);
}
```
