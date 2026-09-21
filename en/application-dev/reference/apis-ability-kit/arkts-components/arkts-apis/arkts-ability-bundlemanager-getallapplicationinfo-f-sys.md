# getAllApplicationInfo (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(appFlags: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

Obtains all the application information in the system based on the given application flags. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_INSTALLED_BUNDLE_LIST

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appFlags | number | Yes | Type of the application information to obtain. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the array of application information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;

try {
  bundleManager.getAllApplicationInfo(appFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAllApplicationInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', message);
}
```


<a id="getallapplicationinfo-1"></a>

## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(appFlags: number,
    userId: number, callback: AsyncCallback<Array<ApplicationInfo>>): void
```

Obtains all the application information in the system based on the given application flags and user ID. This API uses an asynchronous callback to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_INSTALLED_BUNDLE_LIST

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appFlags | number | Yes | Type of the application information to obtain. |
| userId | number | Yes | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the array of application information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;
let userId = 100;

try {
  bundleManager.getAllApplicationInfo(appFlags, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'getAllApplicationInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed: %{public}s', message);
}
```


<a id="getallapplicationinfo-2"></a>

## getAllApplicationInfo

```TypeScript
function getAllApplicationInfo(appFlags: number, userId?: number): Promise<Array<ApplicationInfo>>
```

Obtains all the application information in the system based on the given application flags and user ID. This API uses a promise to return the result.

**Since:** 9

**Required permissions:** ohos.permission.GET_INSTALLED_BUNDLE_LIST

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| appFlags | number | Yes | Type of the application information to obtain. |
| userId | number | No | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller. The value must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[ApplicationInfo](arkts-ability-bundlemanager-applicationinfo-t.md)&gt;&gt; | Promise used to return the array of application information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified user ID is not found. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';

let appFlags = bundleManager.ApplicationFlag.GET_APPLICATION_INFO_DEFAULT;

try {
  bundleManager.getAllApplicationInfo(appFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'getAllApplicationInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'getAllApplicationInfo failed. Cause: %{public}s', message);
}
```
