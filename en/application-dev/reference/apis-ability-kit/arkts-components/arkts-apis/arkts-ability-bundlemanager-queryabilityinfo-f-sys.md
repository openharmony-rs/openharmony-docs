# queryAbilityInfo (System API)

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
```

## queryAbilityInfo

```TypeScript
function queryAbilityInfo(want: Want, abilityFlags: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

Obtains the ability information based on the given want and ability flags. This API uses an asynchronous callback to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want containing the bundle name to query. |
| abilityFlags | number | Yes | Type of the ability information to obtain. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AbilityInfo](arkts-ability-bundlemanager-abilityinfo-t.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the array of ability information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit query. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability is not found. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |
| [17700029](../errorcode-bundle.md#17700029-disabled-ability) | The specified ability is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', message);
}
```


<a id="queryabilityinfo-1"></a>

## queryAbilityInfo

```TypeScript
function queryAbilityInfo(want: Want, abilityFlags: number, userId: number, callback: AsyncCallback<Array<AbilityInfo>>): void
```

Obtains the ability information based on the given want, ability flags, and user ID. This API uses an asynchronous callback to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want containing the bundle name to query. |
| abilityFlags | number | Yes | Type of the ability information to obtain. |
| userId | number | Yes | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[AbilityInfo](arkts-ability-bundlemanager-abilityinfo-t.md)&gt;&gt; | Yes | [Callback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md) used to return the result. If the operation is successful, **err** is **null** and **data** is the array of ability information obtained. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit query. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified userId is invalid. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |
| [17700029](../errorcode-bundle.md#17700029-disabled-ability) | The specified ability is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags, userId, (err, data) => {
    if (err) {
      hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', err.message);
    } else {
      hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully: %{public}s', JSON.stringify(data));
    }
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed: %{public}s', message);
}
```


<a id="queryabilityinfo-2"></a>

## queryAbilityInfo

```TypeScript
function queryAbilityInfo(want: Want, abilityFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

Obtains the ability information based on the given want, ability flags, and user ID. This API uses a promise to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 9

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| want | [Want](arkts-ability-app-ability-want-want-c.md) | Yes | Want containing the bundle name to query. |
| abilityFlags | number | Yes | Type of the ability information to obtain. |
| userId | number | No | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller. The value must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AbilityInfo](arkts-ability-bundlemanager-abilityinfo-t.md)&gt;&gt; | Promise used to return the array of ability information obtained. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit query. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified userId is invalid. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |
| [17700029](../errorcode-bundle.md#17700029-disabled-ability) | The specified ability is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  });
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}
```

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let want: Want = {
  bundleName: "com.example.myapplication",
  abilityName: "EntryAbility"
};

try {
  bundleManager.queryAbilityInfo(want, abilityFlags).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}
```


<a id="queryabilityinfo-3"></a>

## queryAbilityInfo

```TypeScript
function queryAbilityInfo(wants: Array<Want>, abilityFlags: number, userId?: number): Promise<Array<AbilityInfo>>
```

Obtains the ability information based on the given want list, ability flags, and user ID. This API uses a promise to return the result.

No permission is required for obtaining the caller's own information.

**Since:** 12

**Required permissions:** ohos.permission.GET_BUNDLE_INFO_PRIVILEGED or ohos.permission.GET_BUNDLE_INFO

**System capability:** SystemCapability.BundleManager.BundleFramework.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wants | Array&lt;[Want](arkts-ability-app-ability-want-want-c.md)&gt; | Yes | List of want containing the bundle name to query. |
| abilityFlags | number | Yes | Type of the ability information to obtain. |
| userId | number | No | User ID, which can be obtained by calling [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). The default value is the user ID of the caller. The value must be greater than or equal to 0. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[AbilityInfo](arkts-ability-bundlemanager-abilityinfo-t.md)&gt;&gt; | Promise used to return an array of AbilityInfo object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission denied, non-system app called system api. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. At least one parameter(action, entity, uri or type) is required for implicit query. |
| [17700001](../errorcode-bundle.md#17700001-bundle-name-does-not-exist) | The specified bundleName is not found. |
| [17700003](../errorcode-bundle.md#17700003-ability-name-does-not-exist) | The specified ability is not found. |
| [17700004](../errorcode-bundle.md#17700004-user-id-does-not-exist) | The specified userId is invalid. |
| [17700026](../errorcode-bundle.md#17700026-bundle-disabled) | The specified bundle is disabled. |
| [17700029](../errorcode-bundle.md#17700029-disabled-ability) | The specified ability is disabled. |

**Examples**

```TypeScript
import { bundleManager } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { hilog } from '@kit.PerformanceAnalysisKit';
import { Want } from '@kit.AbilityKit';

let abilityFlags = bundleManager.AbilityFlag.GET_ABILITY_INFO_DEFAULT;
let userId = 100;
let want: Want = {
  bundleName: "com.example.myapplication1",
  abilityName: "EntryAbility"
};
let want1: Want = {
  bundleName: "com.example.myapplication2",
  abilityName: "EntryAbility"
};
let wants: Array<Want> = [want, want1];
try {
  bundleManager.queryAbilityInfo(wants, abilityFlags, userId).then((data) => {
    hilog.info(0x0000, 'testTag', 'queryAbilityInfo successfully. Data: %{public}s', JSON.stringify(data));
  }).catch((err: BusinessError) => {
    hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', err.message);
  })
} catch (err) {
  let message = (err as BusinessError).message;
  hilog.error(0x0000, 'testTag', 'queryAbilityInfo failed. Cause: %{public}s', message);
}
```
