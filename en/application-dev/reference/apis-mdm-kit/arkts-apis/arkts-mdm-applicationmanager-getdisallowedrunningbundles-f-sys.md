# getDisallowedRunningBundles (System API)

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## getDisallowedRunningBundles

```TypeScript
function getDisallowedRunningBundles(admin: Want, callback: AsyncCallback<Array<string>>): void
```

Obtains applications that are not allowed to run by the current user. This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to obtain the applications that are not allowed to run. If the operation is successful, **err** is **null**; otherwise, **err** is an error object.<br>Note: For API version 20 and earlier versions, the return value is the **appId** list. In API version 21 and later versions, the return value is the **appId** or **appIdentifier** list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

applicationManager.getDisallowedRunningBundles(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
});
```


<a id="getdisallowedrunningbundles-1"></a>

## getDisallowedRunningBundles

```TypeScript
function getDisallowedRunningBundles(admin: Want, userId: number, callback: AsyncCallback<Array<string>>): void
```

Obtains an application from the applications that are not allowed to run by the current user (specified by **userId**). This API uses an asynchronous callback to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| userId | number | Yes | User ID, which must be greater than or equal to 0. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;string&gt;&gt; | Yes | Callback used to obtain the applications that are not allowed to run. If the operation is successful, **err** is **null**; otherwise, **err** is an error object.<br>Note: For API version 20 and earlier versions, the return value is the **appId** list. In API version 21 and later versions, the return value is the **appId** or **appIdentifier** list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

applicationManager.getDisallowedRunningBundles(wantTemp, 100, (err, result) => {
  if (err) {
    console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
});
```


<a id="getdisallowedrunningbundles-2"></a>

## getDisallowedRunningBundles

```TypeScript
function getDisallowedRunningBundles(admin: Want, userId?: number): Promise<Array<string>>
```

Obtains applications that are not allowed to run under the current user or a specified user. This API uses a promise to return the result.

**Since:** 10

**Deprecated since:** 26.0.0

**Substitutes:** [getDisallowedRunningBundlesSync](arkts-mdm-applicationmanager-getdisallowedrunningbundlessync-f.md)

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| userId | number | No | User ID, which must be greater than or equal to 0.<br> - If **userId** is passed in, the applications cannot be run by the specified user. <br> - If **userId** is not passed in, the applications cannot be run by the current user. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the applications that are not allowed to run by the current user or specified user.<br>Note: For API version 20 and earlier versions, the return value is the **appId** list. In API version 21 and later versions, the return value is the **appId** or **appIdentifier** list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

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

applicationManager.getDisallowedRunningBundles(wantTemp, 100).then((result) => {
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});
```
