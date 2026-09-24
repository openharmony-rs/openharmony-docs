# addDisallowedRunningBundles (System API)

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addDisallowedRunningBundles

```TypeScript
function addDisallowedRunningBundles(admin: Want, appIds: Array<string>, callback: AsyncCallback<void>): void
```

Adds the applications that are not allowed to run under the current user. This API uses an asynchronous callback to return the result. From API version 21, if the allowed application list [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the prohibited application list cannot be added using this API. Otherwise, the error code 9200010 is reported.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appIds | Array&lt;string&gt; | Yes | Application IDs.<br>Note: From API version 21 onwards, the **appId** and **appIdentifier** of the app can be passed. **appIdentifier** is recommended. In API version 20 and earlier versions, only **appId** can be passed. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured.<br>**Applicable version:** 21 and later |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, (err) => {
  if (err) {
    console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in adding disallowed running bundles');
});
```


<a id="adddisallowedrunningbundles-1"></a>

## addDisallowedRunningBundles

```TypeScript
function addDisallowedRunningBundles(admin: Want, appIds: Array<string>, userId: number, callback: AsyncCallback<void>): void
```

Adds the applications that are not allowed to run under a specified user (specified by **userId**). This API uses an asynchronous callback to return the result. From API version 21, if the allowed application list [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the prohibited application list cannot be added using this API. Otherwise, the error code 9200010 is reported.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appIds | Array&lt;string&gt; | Yes | Application IDs.<br>Note: From API version 21 onwards, the **appId** and **appIdentifier** of the app can be passed. **appIdentifier** is recommended. In API version 20 and earlier versions, only **appId** can be passed. |
| userId | number | Yes | User ID, which must be greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;void&gt; | Yes | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured.<br>**Applicable version:** 21 and later |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, 100, (err) => {
  if (err) {
    console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in adding disallowed running bundles');
});
```


<a id="adddisallowedrunningbundles-2"></a>

## addDisallowedRunningBundles

```TypeScript
function addDisallowedRunningBundles(admin: Want, appIds: Array<string>, userId?: number): Promise<void>
```

Adds the applications that are not allowed to run by the current or specified user. This API uses a promise to return the result. From API version 21, if the allowed application list [addAllowedRunningBundles](arkts-mdm-applicationmanager-addallowedrunningbundles-f.md) is not empty, the prohibited application list cannot be added using this API. Otherwise, the error code 9200010 is reported.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [addDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-adddisallowedrunningbundlessync-f.md)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appIds | Array&lt;string&gt; | Yes | Application IDs.<br>Note: From API version 21 onwards, the **appId** and **appIdentifier** of the app can be passed. **appIdentifier** is recommended. In API version 20 and earlier versions, only **appId** can be passed. |
| userId | number | No | User ID, which must be greater than or equal to 0.<br> - If **userId** is passed in, the applications cannot be run by the specified user. <br> - If **userId** is not passed in, the applications cannot be run by the current user. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when an application that is not allowed to run fails to be added. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured.<br>**Applicable version:** 21 and later |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, 100).then(() => {
  console.info('Succeeded in adding disallowed running bundles');
}).catch((err: BusinessError) => {
  console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});
```
