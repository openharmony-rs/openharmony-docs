# @ohos.enterprise.applicationManager (Application Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

The **applicationManager** module provides application management capabilities, including adding, removing, and obtaining the applications that are forbidden to run.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md). The [applicationManager.isAppKioskAllowed](#applicationmanagerisappkioskallowed20) API is available to all applications.
>

## Modules to Import

```ts
import { applicationManager } from '@kit.MDMKit';
```

## applicationManager.addDisallowedRunningBundlesSync

addDisallowedRunningBundlesSync(admin: Want, appIds: Array\<string>, accountId?: number): void

Adds the applications that are not allowed to run by the current or specified user. From API version 21, if the allowed application list [addallowedRunningBundles](#applicationmanageraddallowedrunningbundles21) is not empty, the prohibited application list cannot be added using this API. Otherwise, the error code 9200010 is reported.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| appIds    | Array&lt;string&gt;                                     | Yes  | IDs of the applications to add.<br>**Note**: In API version 21 and later versions, [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) can be transferred. [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) is recommended. In API version 20 and earlier versions, only [appId](../../quick-start/common_problem_of_application.md#what-is-appid) can be transferred.|
| accountId | number                                                  | No  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  applicationManager.addDisallowedRunningBundlesSync(wantTemp, appIds);
  console.info('Succeeded in adding disallowed running bundles.');
} catch (err) {
  console.error(`Failed to add disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.removeDisallowedRunningBundlesSync

removeDisallowedRunningBundlesSync(admin: Want, appIds:  Array\<string>, accountId?: number): void

Removes the applications that are not allowed to run by the current user or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| appIds    | Array&lt;string&gt;                                     | Yes  | IDs of the applications to add.<br>**Note**: Starting from API version 21, elements in the array support the use of both [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier). Only the passed **appId** (or **appIdentifier**) will be removed, and the **appIdentifier** (or **appId**) of the same application will not be removed. In API version 20 and earlier versions, only **appId** can be transferred.|
| accountId | number                                                  | No  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  applicationManager.removeDisallowedRunningBundlesSync(wantTemp, appIds);
  console.info('Succeeded in removing disallowed running bundles.');
} catch (err) {
  console.error(`Failed to remove disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.getDisallowedRunningBundlesSync

getDisallowedRunningBundlesSync(admin: Want, accountId?: number): Array&lt;string>

Obtains applications that are not allowed to run by the current user or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| accountId | number                                                  | No  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

**Return value**

| Type               | Description                            |
| ------------------- | -------------------------------- |
| Array&lt;string&gt; | Applications that are not allowed to run by the current user or specified user.<br>**Note**: For API version 20 and earlier versions, the return value is the [appId](../../quick-start/common_problem_of_application.md#what-is-appid) list. In API version 21 and later versions, the return value is the [appId](../../quick-start/common_problem_of_application.md#what-is-appid) or [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) list.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<string> = applicationManager.getDisallowedRunningBundlesSync(wantTemp);
  console.info(`Succeeded in getting disallowed running bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.addAllowedRunningBundles<sup>21+</sup>

addAllowedRunningBundles(admin: Want, appIdentifiers: Array\<string>, accountId: number): void

Adds the applications that are allowed to run under specified users.

> **NOTE**
>
> 1. Most APIs provided by MDM Kit are available only to MDM applications. When using this API, add the MDM application to the application running trustlist. Otherwise, the MDM application will be prohibited from running, blocking the API call. For details about whether the API is open only to MDM applications, see the module description.
>
> 2. If the application running blocklist is not empty, this API cannot be used to add applications to the running trustlist. Otherwise, the error code 9200010 is reported. APIs related to the application running blocklist include [addDisallowedRunningBundlesSync](#applicationmanageradddisallowedrunningbundlessync)<!--Del-->, [addDisallowedRunningBundles](./js-apis-enterprise-applicationManager-sys.md#applicationmanageradddisallowedrunningbundles), [addDisallowedRunningBundles](./js-apis-enterprise-applicationManager-sys.md#applicationmanageradddisallowedrunningbundles-1), and [addDisallowedRunningBundles](./js-apis-enterprise-applicationManager-sys.md#applicationmanageradddisallowedrunningbundles-2).
>
> 3. This API only takes effect for third-party applications. System applications are not subject to this list and are allowed to run by default.<!--DelEnd-->

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| appIdentifiers    | Array&lt;string&gt;                             | Yes  | Array of [unique identifiers](../../quick-start/common_problem_of_application.md#what-is-appidentifier) of an application. You can call [bundleManager.getinstalledbundlelist](./js-apis-enterprise-bundleManager.md#bundlemanagergetinstalledbundlelist20) to obtain **bundleInfo.signatureInfo.appIdentifier**.<br>Value range:<br> - The total number of entries in this list for a single user must not exceed 200. For example, if 50 entries have been set for user 100 and none for user 101, user 100 can add 150 more entries, while user 101 can add up to 200 entries.|
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let appIdentifiers: Array<string> = ['0123456789123456789'];

try {
  applicationManager.addAllowedRunningBundles(wantTemp, appIdentifiers, 100);
  console.info('Succeeded in adding allowed running bundles.');
} catch (err) {
  console.error(`Failed to add allowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.removeAllowedRunningBundles<sup>21+</sup>

removeAllowedRunningBundles(admin: Want, appIdentifiers: Array\<string>, accountId: number): void

Removes the applications that are allowed to run by the specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| appIdentifiers    | Array&lt;string&gt;                             | Yes  | Array of [unique identifiers](../../quick-start/common_problem_of_application.md#what-is-appidentifier) of an application. You can obtain the **bundleInfo.signatureInfo.appIdentifier** by calling the [bundleManager.getinstalledbundlelist](./js-apis-enterprise-bundleManager.md#bundlemanagergetinstalledbundlelist20) API. Value range: The array length cannot exceed 200.|
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let appIdentifiers: Array<string> = ['0123456789123456789'];

try {
  applicationManager.removeAllowedRunningBundles(wantTemp, appIdentifiers, 100);
  console.info('Succeeded in removing allowed running bundles.');
} catch (err) {
  console.error(`Failed to remove allowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.getAllowedRunningBundles<sup>21+</sup>

getAllowedRunningBundles(admin: Want, accountId: number): Array&lt;string>

Obtains the list of applications allowed to run by a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Return value**

| Type               | Description                            |
| ------------------- | -------------------------------- |
| Array&lt;string&gt; | List of applications allowed to run by a specified user.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<string> = applicationManager.getAllowedRunningBundles(wantTemp, 100);
  console.info(`Succeeded in getting allowed running bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed running bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.addAutoStartApps

addAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void

Adds the auto-start applications for the current user. Applications added to the auto-start list via this API cannot be manually disabled for auto-start by users on the device<!--RP4--><!--RP4End-->. However, they can be removed from the auto-start list using the [removeAutoStartApps](#applicationmanagerremoveautostartapps) API.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: For API version 20 and earlier versions, this API can be properly called on PCs/2-in-1 devices and does not work on other devices. This API can be used on phones, tablets, PCs/2-in-1 devices since API version 21.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |
| autoStartApps | Array\<[Want](../apis-ability-kit/js-apis-app-ability-want.md)> | Yes  | Array of auto-start applications. The maximum array length is 10. For example, if there are already 5 applications in the list, a maximum of 5 more can be added via this API. **Want** must contain **bundleName** and **abilityName**.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let autoStartApps: Array<Want> = [
  {
    // Replace it as required.
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EnterpriseAdminAbility'
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps);
  console.info('Succeeded in adding auto start applications.');
} catch(err) {
  console.error(`Failed to add auto start applications. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.removeAutoStartApps

removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>): void

Removes the auto-start applications for the current user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: For API version 20 and earlier versions, this API can be properly called on PCs/2-in-1 devices and does not work on other devices. This API can be used on phones, tablets, PCs/2-in-1 devices since API version 21.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description            |
| ------------- | ------------------------------------------------------------ | ---- | ---------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.  |
| autoStartApps | Array\<[Want](../apis-ability-kit/js-apis-app-ability-want.md)> | Yes  | Array of auto-start applications. **Want** must contain **bundleName** and **abilityName**.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let autoStartApps: Array<Want> = [
  {
    // Replace it as required.
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EnterpriseAdminAbility'
  }
];

try {
  applicationManager.removeAutoStartApps(wantTemp, autoStartApps);
  console.info('Succeeded in removing auto start applications.');
} catch(err) {
  console.error(`Failed to remove auto start applications. Code: ${err.code}, message: ${err.message}`);
}
```
## applicationManager.removeAutoStartApps<sup>20+</sup>

removeAutoStartApps(admin: Want, autoStartApps: Array\<Want>, accountId: number): void

Removes the specified application from the auto-start application list of a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: For API version 20 and earlier versions, this API can be properly called on PCs/2-in-1 devices and does not work on other devices. This API can be used on phones, tablets, PCs/2-in-1 devices since API version 21.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description            |
| ------------- | ------------------------------------------------------------ | ---- | ---------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.  |
| autoStartApps | Array\<[Want](../apis-ability-kit/js-apis-app-ability-want.md)> | Yes  | Array of auto-start applications. **Want** must contain **bundleName** and **abilityName**.|
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
 
let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let autoStartApps: Array<Want> = [
  // Replace it as required.
  {
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EnterpriseAdminAbility'
  }
];

try {
  applicationManager.removeAutoStartApps(wantTemp, autoStartApps, 100);
  console.info('Succeeded in removing auto start applications.');
} catch(err) {
  console.error(`Failed to remove auto start applications. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.getAutoStartApps

getAutoStartApps(admin: Want): Array\<Want>

Checks the auto-start applications for the current user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: For API version 20 and earlier versions, this API can be properly called on PCs/2-in-1 devices and does not work on other devices. This API can be used on phones, tablets, PCs/2-in-1 devices since API version 21.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.|

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| Array\<[Want](../apis-ability-kit/js-apis-app-ability-want.md)> | List of the auto-start applications obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let res: Array<Want> = applicationManager.getAutoStartApps(wantTemp);
  console.info(`Succeeded in adding auto start apps: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to auto start apps. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.addAutoStartApps<sup>20+</sup>

addAutoStartApps(admin: Want, autoStartApps: Array\<Want>, accountId: number, disallowModify: boolean): void

Adds a list of applications that automatically start upon system startup for a specified user, and sets whether to forbid the user to manually cancel the automatic startup of applications.<br>Applications can be added to the auto-start list via this API and the [addAutoStartApps](#applicationmanageraddautostartapps) API. Settings from both APIs can take effect simultaneously. For a single user, the auto-start list supports a maximum of 10 applications. For example, if there are already 3 applications in the current list, a maximum of 7 more can be added for the user via this API.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: For API version 20 and earlier versions, this API can be properly called on PCs/2-in-1 devices and does not work on other devices. This API can be used on phones, tablets, PCs/2-in-1 devices since API version 21.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |
| autoStartApps | Array\<[Want](../apis-ability-kit/js-apis-app-ability-want.md)> | Yes  | Array of auto-start applications. The array can contain a maximum of 10 applications. **Want** must contain **bundleName** and **abilityName**.|
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|
| disallowModify | boolean | Yes  | Whether to disable the user from manually disabling automatic application startup. The value **true** indicates that auto-start is disabled, and the value **false** indicates the opposite.<!--RP1--><!--RP1End-->|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let autoStartApps: Array<Want> = [
  // Replace it as required.
  {
    bundleName: 'com.example.autoStartApplication',
    abilityName: 'EnterpriseAdminAbility'
  }
];

try {
  applicationManager.addAutoStartApps(wantTemp, autoStartApps, 100, true);
  console.info('Succeeded in adding auto start applications and set disllowModify.');
} catch(err) {
  console.error(`Failed to add auto start applications and set disallowModify. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.getAutoStartApps<sup>20+</sup>

getAutoStartApps(admin: Want, accountId: number): Array\<Want>

Checks the auto-start applications for the specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: For API version 20 and earlier versions, this API can be properly called on PCs/2-in-1 devices and does not work on other devices. This API can be used on phones, tablets, PCs/2-in-1 devices since API version 21.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.|
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| Array\<[Want](../apis-ability-kit/js-apis-app-ability-want.md)> | List of the auto-start applications obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let res: Array<Want> = applicationManager.getAutoStartApps(wantTemp, 100);
  console.info(`Succeeded in getting auto start apps: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to get auto start apps. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.isModifyAutoStartAppsDisallowed<sup>20+</sup>

isModifyAutoStartAppsDisallowed(admin: Want, autoStartApp: Want, accountId: number): boolean

Checks whether the auto-start of an application is disabled for the specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: For API version 20 and earlier versions, this API can be properly called on PCs/2-in-1 devices and does not work on other devices. This API can be used on phones, tablets, PCs/2-in-1 devices since API version 21.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.|
| autoStartApp | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | Auto-start applications to add. **Want** must contain **bundleName** and **abilityName**.|
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| boolean | Whether to disable the user from disabling automatic application startup. The value **true** indicates that auto-start is disabled, and the value **false** indicates the opposite.<!--PR1--><!--PR1End-->|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let autoStartApp: Want = {
  // Replace it as required.
  bundleName: 'com.example.autoStartApplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let res: boolean = applicationManager.isModifyAutoStartAppsDisallowed(wantTemp, autoStartApp, 100);
  console.info(`Succeeded in getting disallow modify auto start app: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to get disallow modify auto start app. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.addKeepAliveApps<sup>14+</sup>

addKeepAliveApps(admin: Want, bundleNames: Array\<string>, accountId: number): void

Adds applications to the keep-alive list; once added, the application processes will be kept alive automatically. After the device is powered on or the application is killed, the system will proactively restart these application processes. <!--RP7--><!--RP7End-->Applications added to the keep-alive list via this API cannot be manually removed from keep-alive status by users on the device<!--RP6--><!--RP6End-->. However, they can be removed from the keep-alive list using the [removeKeepAliveApps](#applicationmanagerremovekeepaliveapps14) API. If applications are disallowed to run by calling [addDisallowedRunningBundlesSync](#applicationmanageradddisallowedrunningbundlessync), they cannot be kept alive. Otherwise, error code 9200010 will be reported.
**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| bundleNames    | Array&lt;string&gt;                                     | Yes  | Array of application bundle names, which specifies the applications to be kept alive. A maximum of 5 applications are supported.<!--RP5--><!--RP5End-->                                    |
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured. |
| 9201005  | Add keep alive applications failed. |
| 201  | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100);
  console.info('Succeeded in adding keep alive apps.');
} catch (err) {
  console.error(`Failed to add keep alive apps. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.addKeepAliveApps<sup>20+</sup>

addKeepAliveApps(admin: Want, bundleNames: Array\<string>, accountId: number, disallowModify: boolean): void

Adds applications to the keep-alive list; once added, the application processes will be kept alive automatically. You can also set whether to disable manual keep-alive cancellation. After the device is powered on or the application is killed, the system will proactively restart these application processes.<br>Applications can be added to the keep-alive list via this API and the [addKeepAliveApps](#applicationmanageraddkeepaliveapps14) API. Settings from both APIs can take effect simultaneously. For a single user, the keep-alive list supports a maximum of 5 applications. For example, if there are already 3 applications in the current list, a maximum of 2 more can be added for the user via this API.<br>If applications are disallowed to run by calling [addDisallowedRunningBundlesSync](#applicationmanageradddisallowedrunningbundlessync), they cannot be kept alive. Otherwise, error code 9200010 will be reported.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| bundleNames    | Array&lt;string&gt;                                     | Yes  | Array of application bundle names, which specifies the applications to be kept alive. A maximum of 5 applications are supported.<br>Applications must be installed under user 1 (a user who supports single-instance running of third-party applications) and have integrated [background services](../../application-models/app-service-extension-ability.md#implementing-a-background-service)<!--RP3--><!--RP3End-->. Otherwise, the error code 9201005 will be reported. |
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|
| disallowModify | boolean | Yes  | Whether to forbid users to manually cancel the keep-alive status. The value **true** indicates that users are not allowed to manually cancel the keep-alive status, and the value **false** indicates the opposite.<!--RP2--><!--RP2End--> |

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200010  | A conflict policy has been configured. |
| 9201005  | Add keep alive applications failed. |
| 201  | Permission verification failed.The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace it as required.
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.addKeepAliveApps(wantTemp, bundleNames, 100, true);
  console.info('Succeeded in adding keep alive apps and set disallowModify.');
} catch (err) {
  console.error(`Failed to add keep alive apps and set disallowModify. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.removeKeepAliveApps<sup>14+</sup>

removeKeepAliveApps(admin: Want, bundleNames: Array\<string>, accountId: number): void

Removes a specified application from the keep-alive list.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API takes effect only on PCs/2-in-1 devices and does not work on other devices.

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| bundleNames    | Array&lt;string&gt;                                     | Yes  | Application bundle name array, which specifies the applications to be kept alive. A maximum of five applications are supported.                                  |
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201  | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let bundleNames: Array<string> = ['com.example.myapplication'];

try {
  applicationManager.removeKeepAliveApps(wantTemp, bundleNames, 100);
  console.info('Succeeded in removing keep alive apps.');
} catch (err) {
  console.error(`Failed to remove keep alive apps. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.getKeepAliveApps<sup>14+</sup>

getKeepAliveApps(admin: Want, accountId: number): Array&lt;string>

Obtains the bundle name of the keep-alive application.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API takes effect only on PCs/2-in-1 devices and does not work on other devices.

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Return value**

| Type               | Description                            |
| ------------------- | -------------------------------- |
| Array&lt;string&gt; | Bundle name of the application kept alive for the specified user.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201  | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<string> = applicationManager.getKeepAliveApps(wantTemp, 100);
  console.info('Succeeded in getting keep alive apps.');
} catch (err) {
  console.error(`Failed to get keep alive apps. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.isModifyKeepAliveAppsDisallowed<sup>20+</sup>

isModifyKeepAliveAppsDisallowed(admin: Want, accountId: number, bundleName: string): boolean

Checks whether the application is forbidden to cancel the keep-alive status.
**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API takes effect only on PCs/2-in-1 devices and does not work on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.|
| accountId | number                                                  | Yes  | Account ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|
| bundleName | string | Yes| Bundle name.|

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| boolean | Whether to forbid users to manually cancel the keep-alive status. The value **true** indicates that users are not allowed to manually cancel the keep-alive status, and the value **false** indicates the opposite.<!--RP2--><!--RP2End-->|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace it as required.
let keepAliveApp: string = 'com.example.keepAliveApplication';

try {
  let res: boolean = applicationManager.isModifyKeepAliveAppsDisallowed(wantTemp, 100, keepAliveApp);
  console.info(`Succeeded in getting disallow modify keep alive app: ${JSON.stringify(res)}`);
} catch(err) {
  console.error(`Failed to get disallow modify keep alive app. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.clearUpApplicationData<sup>20+</sup>

clearUpApplicationData(admin: Want, bundleName: string, appIndex: number, accountId: number): void

Clears all application data.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.


**Parameters**

| Name    | Type                                                   | Mandatory| Description                                                        |
| ---------  | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| bundleName | string                                                  | Yes  | Bundle name of the application whose data needs to be cleared.|
| appIndex | number                                                    | Yes  | Index of the application clone. The value is an integer greater than or equal to 0.<br> You can call [getAppCloneIdentity](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetappcloneidentity14) of @ohos.bundle.bundleManager to obtain the index.|
| accountId | number                                                   | Yes  | Account ID. The value is an integer greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201  | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { applicationManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let bundleName: string = 'com.example.exampleapplication';

try {
  // Replace it as required.
  applicationManager.clearUpApplicationData(wantTemp, bundleName, 0, 100);
  console.info('Succeeded in clearing up application data.');
} catch (err) {
  console.error(`Failed to clear up application data. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.setAllowedKioskApps<sup>20+</sup>

setAllowedKioskApps(admin: Want, appIdentifiers: Array&lt;string&gt;): void

Sets applications allowed to run in kiosk mode.

Kiosk mode is a system-level runtime mode that restricts a device to a single application or a set of applications. It controls the lock screen, status bar, gestures, and key features to prevent users from launching other applications or performing other operations on the device.

**Required permissions**: ohos.permission.ENTERPRISE_SET_KIOSK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                              |
| appIdentifiers | Array&lt;string&gt;                                   | Yes  | Array of [unique identifiers](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) of an application. You can call the [bundleManager.getBundleInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfo14-2) API to obtain the **bundleInfo.signatureInfo.appIdentifier**. In case of repeated configuration, the newly configured array will overwrite the old one, with a maximum limit of 200 entries.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201  | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { applicationManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.edmtest',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace it as required.
  let appIdentifiers: Array<string> = ['6917****3569'];
  applicationManager.setAllowedKioskApps(wantTemp, appIdentifiers);
  console.info('Succeeded in setting allowed kiosk apps.');
} catch (err) {
  console.error(`Failed to set allowed kiosk apps. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.getAllowedKioskApps<sup>20+</sup>

getAllowedKioskApps(admin: Want): Array&lt;string&gt;

Obtains the applications allowed to run in kiosk mode.

**Required permissions**: ohos.permission.ENTERPRISE_SET_KIOSK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.                                      |

**Return value**

| Type               | Description                            |
| ------------------- | -------------------------------- |
| Array&lt;string&gt; | List of [unique identifiers](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) of an application that can run in kiosk mode.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201  | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { applicationManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.edmtest',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let appIdentifiers: Array<string> = applicationManager.getAllowedKioskApps(wantTemp);
  console.info(`Succeeded in getting allowed kiosk apps, appIdentifiers: ${JSON.stringify(appIdentifiers)}`);
} catch (err) {
  console.error(`Failed to get allowed kiosk apps. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.isAppKioskAllowed<sup>20+</sup>

isAppKioskAllowed(appIdentifier: string): boolean

Checks whether an application is allowed to run in kiosk mode.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| appIdentifier | string                                                 | Yes  | [Unique identifiers](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md#signatureinfo) of an application. You can call the [bundleManager.getBundleInfo](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfo14-2) API to obtain the **bundleInfo.signatureInfo.appIdentifier**.                                      |

**Return value**

| Type               | Description                            |
| ------------------- | -------------------------------- |
| boolean    | The value **true** means the application can run in kiosk mode; the value **false** means the opposite.|

**Example**

```ts
import { applicationManager } from '@kit.MDMKit';

try {
  // Replace it as required.
  let isAllowed: boolean = applicationManager.isAppKioskAllowed('6917****3569');
  console.info(`Succeeded in querying if the app is allowed kiosk, isAllowed: ${isAllowed}`);
} catch (err) {
  console.error(`Failed to query if the app is allowed kiosk. Code is ${err.code}, message is ${err.message}`);
}
```

## applicationManager.setKioskFeatures<sup>20+</sup>

setKioskFeatures(admin: Want, features: Array\<KioskFeature>): void

Sets the features of kiosk mode. When [kiosk mode is activated](../apis-ability-kit/js-apis-app-ability-kioskManager.md#kioskmanagerenterkioskmode), the system disables capabilities such as the notification center, control panel, and recent tasks panel by default. This API can be used to disable or restore some capabilities.

**Required permissions**: ohos.permission.ENTERPRISE_SET_KIOSK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                  |
| ------------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.        |
| features | Array&lt;[KioskFeature](#kioskfeature20)&gt;           | Yes  | Features of kiosk mode.<br> If an empty array is passed, the system will clear all previously configured features and restore kiosk mode to its default state, where capabilities such as the notification center, control panel, and recent tasks panel are disabled.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. | 
| 9200012  | Parameter verification failed.                          |
| 201      | Permission verification failed.The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { applicationManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let kioskFeatures: Array<applicationManager.KioskFeature> = [];
kioskFeatures.push(applicationManager.KioskFeature.ALLOW_NOTIFICATION_CENTER);
kioskFeatures.push(applicationManager.KioskFeature.ALLOW_CONTROL_CENTER);
try {
  applicationManager.setKioskFeatures(wantTemp, kioskFeatures);
  console.info('Succeeded in setting kiosk feature.');
} catch (err) {
  console.error(`Failed to set kiosk feature. Code is ${err.code}, message is ${err.message}`);
}
```

## KioskFeature<sup>20+</sup>

Defines the features of the kiosk mode.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

| Name                       | Value | Description   |
| ----------------------------| ----| ------------------------------- |
| ALLOW_NOTIFICATION_CENTER   | 1   | Allow access to the notification center.|
| ALLOW_CONTROL_CENTER        | 2   | Allow access to the control panel.|

## applicationManager.addUserNonStopApps<sup>22+</sup>

addUserNonStopApps(admin: Want, applicationInstances: Array&lt;common.ApplicationInstance&gt;): void

Adds applications to the non-stoppable application list for a specified user. This policy only applies to installed applications. If the parameter list contains uninstalled applications, error code 9200012 will be returned. If an application in the list is uninstalled after the policy is set, the uninstalled application will be removed from the list.
Adding an application that already exists in the list will return success, but the application will not be added repeatedly to the policy list.
<br>Non-stoppable applications cannot be closed by swiping up in the task center. After a user taps the application name in **Settings** > **Apps & services** to go to the details page, the forcible stop button is unavailable.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be called on phones and tablets but has no effect on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |
| applicationInstances | Array&lt;[common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance)&gt; | Yes  | Array of non-stoppable applications. A maximum of 10 applications can be added to the non-stoppable application list. This limit is not divided among users. Specifically, the total number of such applications added by all users cannot exceed 10. For example, if there are already 3 applications in the current list, a maximum of 7 more can be added for a specified user via this API.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let applicationInstances: Array<common.ApplicationInstance> = [
  // Replace it as required.
  {
    appIdentifier: '0123456789123456789',
    accountId: 100,
    appIndex: 0
  }
];

try {
  applicationManager.addUserNonStopApps(wantTemp, applicationInstances);
  console.info('Succeeded in adding UserNonStop applications.');
} catch(err) {
  console.error(`Failed to add UserNonStop applications. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.removeUserNonStopApps<sup>22+</sup>

removeUserNonStopApps(admin: Want, applicationInstances: Array&lt;common.ApplicationInstance&gt;): void

Removes the non-stoppable application list for a specified user. If the parameter list includes uninstalled applications, the removal will still succeed. Installed applications will be removed from the list, while uninstalled ones will not impact the removal process.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be called on phones and tablets but has no effect on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |
| applicationInstances | Array&lt;[common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance)&gt; | Yes  | Array of non-stoppable applications.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let applicationInstances: Array<common.ApplicationInstance> = [
  // Replace it as required.
  {
    appIdentifier: '0123456789123456789',
    accountId: 100,
    appIndex: 0
  }
];

try {
  applicationManager.removeUserNonStopApps(wantTemp, applicationInstances);
  console.info('Succeeded in removing UserNonStop applications.');
} catch(err) {
  console.error(`Failed to remove UserNonStop applications. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.getUserNonStopApps<sup>22+</sup>

getUserNonStopApps(admin: Want): Array&lt;common.ApplicationInstance&gt;

Obtains the non-stoppable application list of all users on the current device.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be called on phones and tablets but has no effect on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| Array&lt;[common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance)&gt; | Array of non-stoppable applications.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<common.ApplicationInstance> = applicationManager.getUserNonStopApps(wantTemp);
  console.info(`Succeeded in getting UserNonStop applications, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get UserNonStop applications. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.addFreezeExemptedApps<sup>22+</sup>

addFreezeExemptedApps(admin: Want, applicationInstances: Array&lt;common.ApplicationInstance&gt;): void

Adds applications to the background freeze-exempt application list for a specified user. This policy applies only to installed applications. If the parameter list contains uninstalled applications, error code 9200012 will be returned. If an application in the list is uninstalled after the policy is set, the uninstalled application will be removed from the list.
Adding an application that already exists in the list will return success, but the application will not be added repeatedly to the policy list.
<br>Freezing operations include suspending the target application, and managing software resource agents, hardware resource agents, and high-power consumption.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be called on phones and tablets but has no effect on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |
| applicationInstances | Array&lt;[common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance)&gt; | Yes  | Array of the background freeze-exempt application list. A maximum of 10 applications can be added to the list. This limit is not divided among users. Specifically, the total number of such applications added by all users cannot exceed 10. For example, if there are already 3 applications in the current list, a maximum of 7 more can be added for a specified user via this API.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let applicationInstances: Array<common.ApplicationInstance> = [
  // Replace it as required.
  {
    appIdentifier: '0123456789123456789',
    accountId: 100,
    appIndex: 0
  }
];

try {
  applicationManager.addFreezeExemptedApps(wantTemp, applicationInstances);
  console.info('Succeeded in adding FreezeExempted applications.');
} catch(err) {
  console.error(`Failed to add FreezeExempted applications. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.removeFreezeExemptedApps<sup>22+</sup>

removeFreezeExemptedApps(admin: Want, applicationInstances: Array&lt;common.ApplicationInstance&gt;): void

Removes the background freeze-exempt application list for a specified user. If the parameter list includes uninstalled applications, the removal will still succeed. Installed applications will be removed from the list, while uninstalled ones will not impact the removal process.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be called on phones and tablets but has no effect on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |
| applicationInstances | Array&lt;[common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance)&gt; | Yes  | Array of the background freeze-exempt application list.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let applicationInstances: Array<common.ApplicationInstance> = [
  // Replace it as required.
  {
    appIdentifier: '0123456789123456789',
    accountId: 100,
    appIndex: 0
  }
];

try {
  applicationManager.removeFreezeExemptedApps(wantTemp, applicationInstances);
  console.info('Succeeded in removing FreezeExempted applications.');
} catch(err) {
  console.error(`Failed to remove FreezeExempted applications. Code: ${err.code}, message: ${err.message}`);
}
```

## applicationManager.getFreezeExemptedApps<sup>22+</sup>

getFreezeExemptedApps(admin: Want): Array&lt;common.ApplicationInstance&gt;

Obtains the background freeze-exempt application list of all users on the current device.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be called on phones and tablets but has no effect on other devices.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name       | Type                                                        | Mandatory| Description                                  |
| ------------- | ------------------------------------------------------------ | ---- | -------------------------------------- |
| admin         | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility.                        |

**Return value**

| Type                                                        | Description                |
| ------------------------------------------------------------ | -------------------- |
| Array&lt;[common.ApplicationInstance](./js-apis-enterprise-common.md#applicationinstance)&gt; | Array of the background freeze-exempt application list.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { applicationManager, common } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<common.ApplicationInstance> = applicationManager.getFreezeExemptedApps(wantTemp);
  console.info(`Succeeded in getting FreezeExempted applications, result : ${JSON.stringify(result)}`);
} catch(err) {
  console.error(`Failed to get FreezeExempted applications. Code: ${err.code}, message: ${err.message}`);
}
```
