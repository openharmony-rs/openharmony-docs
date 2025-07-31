# @ohos.enterprise.applicationManager (Application Management) (System API)

The **applicationManager** module provides application management capabilities, including adding, removing, and obtaining the applications that are forbidden to run.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 10. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs of this module can be called only by a [device administrator application](../../mdm/mdm-kit-guide.md#introduction) that is [enabled](js-apis-enterprise-adminManager-sys.md#adminmanagerenableadmin-2).
> 
> - This topic describes only the system APIs provided by the module. For details about its public APIs, see [@ohos.enterprise.applicationManager](js-apis-enterprise-applicationManager.md).

## Modules to Import

```ts
import { applicationManager } from '@kit.MDMKit';
```

## applicationManager.addDisallowedRunningBundles

addDisallowedRunningBundles(admin: Want, appIds: Array\<string>, callback: AsyncCallback&lt;void&gt;): void

Adds an application that is not allowed to run under the current user. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| appIds    | Array&lt;string&gt;                | Yes   | Application IDs.                 |
| callback | AsyncCallback&lt;void&gt;            | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |


**Example**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, (err) => {
  if (err) {
    console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in adding disallowed running bundles');
});
```

## applicationManager.addDisallowedRunningBundles

addDisallowedRunningBundles(admin: Want, appIds: Array\<string>, userId: number, callback: AsyncCallback&lt;void&gt;): void

Adds an application that is not allowed to run under the current user (specified by userId). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| appIds    | Array&lt;string&gt;                | Yes   | Application IDs.                 |
| userId     | number                             | Yes   | User ID, which must be greater than or equal to 0.|
| callback | AsyncCallback&lt;void&gt;            | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                    |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, 100, (err) => {
  if (err) {
    console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in adding disallowed running bundles');
});
```

## applicationManager.addDisallowedRunningBundles

addDisallowedRunningBundles(admin: Want, appIds: Array\<string>, userId?: number): Promise&lt;void&gt;

Adds the applications that are not allowed to run by the current or specified user. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| appIds    | Array&lt;string&gt;                | Yes   | Application IDs.                 |
| userId     | number                             | No   | User ID, which must be greater than or equal to 0.<br> - If **userId** is passed in, the applications cannot be run by the specified user.<br> - If **userId** is not passed in, the applications cannot be run by the current user.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when an application that is not allowed to run fails to be added. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                    |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.addDisallowedRunningBundles(wantTemp, appIds, 100).then(() => {
  console.info('Succeeded in adding disallowed running bundles');
}).catch((err: BusinessError) => {
  console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});
```

## applicationManager.removeDisallowedRunningBundles

removeDisallowedRunningBundles(admin: Want, appIds: Array\<string>, callback: AsyncCallback&lt;void&gt;): void

Removes an application from the applications that are not allowed to run under the current user. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| appIds    | Array&lt;string&gt;                | Yes   | Application IDs.                 |
| callback | AsyncCallback&lt;void&gt;            | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.removeDisallowedRunningBundles(wantTemp, appIds, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed running bundles');
});
```

## applicationManager.removeDisallowedRunningBundles

removeDisallowedRunningBundles(admin: Want, appIds: Array\<string>, userId: number, callback: AsyncCallback&lt;void&gt;): void

Removes an application from the applications that are not allowed to run under the current user. (specified by userId). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| appIds    | Array&lt;string&gt;                | Yes   | Application IDs.                 |
| userId     | number                             | Yes   | User ID, which must be greater than or equal to 0.|
| callback | AsyncCallback&lt;void&gt;            | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                    |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.removeDisallowedRunningBundles(wantTemp, appIds, 100, (err) => {
  if (err) {
    console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info('Succeeded in removing disallowed running bundles');
});
```

## applicationManager.removeDisallowedRunningBundles

removeDisallowedRunningBundles(admin: Want, appIds: Array\<string>, userId?: number): Promise&lt;void&gt;

Removes an application from the applications that are not allowed to run under the current or specified user. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| appIds    | Array&lt;string&gt;                | Yes   | Application IDs.                 |
| userId     | number                             | No   | User ID, which must be greater than or equal to 0.<br> - If **userId** is passed in, the applications cannot be run by the specified user.<br> - If **userId** is not passed in, the applications cannot be run by the current user.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. An error object is thrown when an application that is not allowed to run fails to be removed. |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                    |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

applicationManager.removeDisallowedRunningBundles(wantTemp, appIds, 100).then(() => {
  console.info('Succeeded in removing disallowed running bundles');
}).catch((err: BusinessError) => {
  console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});
```

## applicationManager.getDisallowedRunningBundles

getDisallowedRunningBundles(admin: Want, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Obtains the applications that are not allowed to run by the current user. This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;       | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.      |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

applicationManager.getDisallowedRunningBundles(wantTemp, (err, result) => {
  if (err) {
    console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
});
```

## applicationManager.getDisallowedRunningBundles

getDisallowedRunningBundles(admin: Want, userId: number, callback: AsyncCallback&lt;Array&lt;string&gt;&gt;): void

Obtains an application from the applications that are not allowed to run by the current user (specified by userId). This API uses an asynchronous callback to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name     | Type                                      | Mandatory  | Description                      |
| -------- | ---------------------------------------- | ---- | ------------------------------- |
| admin    | [Want](../apis-ability-kit/js-apis-app-ability-want.md)     | Yes   | EnterpriseAdminExtensionAbility.           |
| userId     | number                             | Yes   | User ID, which must be greater than or equal to 0.|
| callback | AsyncCallback&lt;Array&lt;string&gt;&gt;       | Yes   | Callback invoked to return the result. If the operation is successful, **err** is **null**. Otherwise, **err** is an error object.      |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                      |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

applicationManager.getDisallowedRunningBundles(wantTemp, 100, (err, result) => {
  if (err) {
    console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
    return;
  }
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
});
```

## applicationManager.getDisallowedRunningBundles

getDisallowedRunningBundles(admin: Want, userId?: number): Promise&lt;Array&lt;string&gt;&gt;

Obtains applications that are not allowed to run by the current user or a specified user. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_SET_APP_RUNNING_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager



**Parameters**

| Name  | Type                                 | Mandatory  | Description     |
| ----- | ----------------------------------- | ---- | ------- |
| admin | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes   | EnterpriseAdminExtensionAbility.|
| userId     | number                             | No   | User ID, which must be greater than or equal to 0.<br> - If **userId** is passed in, the applications cannot be run by the specified user.<br> - If **userId** is not passed in, the applications cannot be run by the current user.|

**Return value**

| Type                  | Description                     |
| --------------------- | ------------------------- |
| Promise&lt;Array&lt;string&gt;&gt; | Promise used to return the applications that are not allowed to run by the current user or a specified user.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                                    |
| ------- | ---------------------------------------------------------------------------- |
| 9200001 | The application is not an administrator application of the device.            |
| 9200002 | The administrator application does not have permission to manage the device. |
| 201 | Permission verification failed. The application does not have the permission required to call the API. |
| 202 | Permission verification failed. A non-system application calls a system API. |
| 401 | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  bundleName: 'com.example.myapplication',
  abilityName: 'EntryAbility',
};

applicationManager.getDisallowedRunningBundles(wantTemp, 100).then((result) => {
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
}).catch((err: BusinessError) => {
  console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
});
```
