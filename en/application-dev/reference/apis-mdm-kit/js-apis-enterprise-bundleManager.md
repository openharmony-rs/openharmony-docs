# @ohos.enterprise.bundleManager (Bundle Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

The **bundleManager** module provides APIs for bundle management, including adding, obtaining, and removing a list of bundles that are allowed to install.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).

## Modules to Import

```ts
import { bundleManager } from '@kit.MDMKit';
```

## bundleManager.addAllowedInstallBundlesSync

addAllowedInstallBundlesSync(admin: Want, appIds: Array&lt;string&gt;, accountId?: number): void

Adds the applications that can be installed by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| appIds    | Array&lt;string&gt;                                     | Yes  | Application IDs.<br>**Note**: In API version 21 and later versions, [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) can be transferred. [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) is recommended. In API version 20 and earlier versions, only [appId](../../quick-start/common_problem_of_application.md#what-is-appid) can be transferred.|
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  bundleManager.addAllowedInstallBundlesSync(wantTemp, appIds, 100);
  console.info('Succeeded in adding allowed install bundles.');
} catch (err) {
  console.error(`Failed to add allowed install bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.removeAllowedInstallBundlesSync

removeAllowedInstallBundlesSync(admin: Want, appIds: Array&lt;string&gt;, accountId?: number): void

Removes the applications that can be installed by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| appIds    | Array&lt;string&gt;                                     | Yes  | Application IDs.<br>**Note**: Starting from API version 21, elements in the array support the use of both [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier). Only the passed **appId** (or **appIdentifier**) will be removed, and the **appIdentifier** (or **appId**) of the same application will not be removed. In API version 20 and earlier versions, only **appId** can be transferred.      |
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  bundleManager.removeAllowedInstallBundlesSync(wantTemp, appIds, 100);
  console.info('Succeeded in removing allowed install bundles.');
} catch (err) {
  console.error(`Failed to remove allowed install bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.getAllowedInstallBundlesSync

getAllowedInstallBundlesSync(admin: Want, accountId?: number): Array&lt;string&gt;

Obtains the applications that can be installed by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

**Return value**

| Type               | Description                          |
| ------------------- | ------------------------------ |
| Array&lt;string&gt; | Array of applications that can be installed by the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<string> = bundleManager.getAllowedInstallBundlesSync(wantTemp, 100);
  console.info(`Succeeded in getting allowed install bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed install bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.addDisallowedInstallBundlesSync

addDisallowedInstallBundlesSync(admin: Want, appIds: Array&lt;string&gt;, accountId?: number): void

Adds the applications that are not allowed to be installed by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| appIds    | Array&lt;string&gt;                                     | Yes  | Application IDs.<br>**Note**: In API version 21 and later versions, [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) can be transferred. [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) is recommended. In API version 20 and earlier versions, only [appId](../../quick-start/common_problem_of_application.md#what-is-appid) can be transferred.|
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  bundleManager.addDisallowedInstallBundlesSync(wantTemp, appIds, 100);
  console.info('Succeeded in adding disallowed install bundles.');
} catch (err) {
  console.error(`Failed to add disallowed install bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.removeDisallowedInstallBundlesSync

removeDisallowedInstallBundlesSync(admin: Want, appIds: Array&lt;string&gt;, accountId?: number): void

Removes the applications that cannot be installed by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| appIds    | Array&lt;string&gt;                                     | Yes  | Application IDs.<br>**Note**: Starting from API version 21, elements in the array support the use of both [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier). Only the passed **appId** (or **appIdentifier**) will be removed, and the **appIdentifier** (or **appId**) of the same application will not be removed. In API version 20 and earlier versions, only **appId** can be transferred.              |
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  bundleManager.removeDisallowedInstallBundlesSync(wantTemp, appIds, 100)
  console.info('Succeeded in removing disallowed install bundles.');
} catch (err) {
  console.error(`Failed to remove disallowed install bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.getDisallowedInstallBundlesSync

getDisallowedInstallBundlesSync(admin: Want, accountId?: number): Array&lt;string&gt;

Obtains the applications that cannot be installed by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

**Return value**

| Type               | Description                          |
| ------------------- | ------------------------------ |
| Array&lt;string&gt; | Array of applications that cannot be installed by the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: Array<string> = bundleManager.getDisallowedInstallBundlesSync(wantTemp, 100);
  console.info(`Succeeded in getting disallowed install bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed install bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.addDisallowedUninstallBundlesSync

addDisallowedUninstallBundlesSync(admin: Want, appIds: Array&lt;string&gt;, accountId?: number): void

Adds the applications that are not allowed to be uninstalled by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| appIds    | Array&lt;string&gt;                                     | Yes  | Application IDs.<br>**Note**: In API version 21 and later versions, [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) can be transferred. [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier) is recommended. In API version 20 and earlier versions, only [appId](../../quick-start/common_problem_of_application.md#what-is-appid) can be transferred.|
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  // Replace parameters with actual values.
  bundleManager.addDisallowedUninstallBundlesSync(wantTemp, appIds, 100);
  console.info('Succeeded in adding disallowed uninstall bundles.');
} catch (err) {
  console.error(`Failed to add disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.removeDisallowedUninstallBundlesSync

removeDisallowedUninstallBundlesSync(admin: Want, appIds: Array&lt;string&gt;, accountId?: number): void

Removes the applications that cannot be uninstalled by the current or specified user through the specified device administrator application.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| appIds    | Array&lt;string&gt;                                     | Yes  | Application IDs.<br>**Note**: Starting from API version 21, elements in the array support the use of both [appId](../../quick-start/common_problem_of_application.md#what-is-appid) and [appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier). Only the passed **appId** (or **appIdentifier**) will be removed, and the **appIdentifier** (or **appId**) of the same application will not be removed. In API version 20 and earlier versions, only **appId** can be transferred.                  |
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let appIds: Array<string> = ['com.example.******_******/******5t5CoBM='];

try {
  // Replace parameters with actual values.
  bundleManager.removeDisallowedUninstallBundlesSync(wantTemp, appIds, 100);
  console.info('Succeeded in removing disallowed uninstall bundles.');
} catch (err) {
  console.error(`Failed to remove disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.getDisallowedUninstallBundlesSync

getDisallowedUninstallBundlesSync(admin: Want, accountId?: number): Array&lt;string&gt;

Obtains the bundles that cannot be uninstalled by the current or specified user.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                   | Mandatory| Description                                                        |
| --------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| accountId | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.<br> - If **accountId** is passed in, this API applies to the specified user.<br> - If **accountId** is not passed in, this API applies to the current user.|

**Return value**

| Type               | Description                          |
| ------------------- | ------------------------------ |
| Array&lt;string&gt; | Array of bundles that cannot be uninstalled by the user.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: Array<String> = bundleManager.getDisallowedUninstallBundlesSync(wantTemp, 100);
  console.info(`Succeeded in getting disallowed uninstall bundles, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get disallowed uninstall bundles. Code is ${err.code}, message is ${err.message}`);
}
```

## bundleManager.uninstall

uninstall(admin: Want, bundleName: string, userId?: number, isKeepData?: boolean): Promise&lt;void&gt;

Uninstalls an application of the current or specified user. The **isKeepData** parameter specifies whether to retain the bundle data. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name    | Type                                                   | Mandatory| Description                                                        |
| ---------- | ------------------------------------------------------- | ---- | ------------------------------------------------------------ |
| admin      | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                              |
| bundleName | string                                                  | Yes  | Bundle name of an application.                                                      |
| userId     | number                                                  | No  | User ID, which must be greater than or equal to 0.<br> - If **userId** is passed in, this API applies to the specified user.<br> - If **userId** is not passed in, this API applies to the current user.|
| isKeepData | boolean                                                 | No  | Whether to retain the bundle data. The value **true** means to retain the bundle data; the value **false** means the opposite.             |

**Return value**

| Type               | Description                                                 |
| ------------------- | ----------------------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. An error object will be thrown if the application fails to be uninstalled.|

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
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace parameters with actual values.
bundleManager.uninstall(wantTemp, 'bundleName', 100, true).then(() => {
  console.info('Succeeded in uninstalling bundles.');
}).catch((err: BusinessError) => {
  console.error(`Failed to uninstall bundles. Code is ${err.code}, message is ${err.message}`);
});
```

## bundleManager.install

install(admin: Want, hapFilePaths: Array\<string>, installParam?: InstallParam): Promise\<void>

Installs specified applications. This API uses a promise to return the result.<br>This API can be used to install only applications of the **enterprise_mdm** (MDM application) or **enterprise_normal** (common enterprise application) distribution type. You can call the [getBundleInfoForSelf](../apis-ability-kit/js-apis-bundleManager.md#bundlemanagergetbundleinfoforself) API to query the [BundleInfo](../apis-ability-kit/js-apis-bundleManager-bundleInfo.md) of an application, where **BundleInfo.appInfo.appDistributionType** indicates the distribution type.
> **NOTE**
> 
> This API is time-consuming. Subsequent calls to other synchronous APIs in the application main thread must wait for the asynchronous return of this API.

**Required permissions**: ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                  |
| ------------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.        |
| hapFilePaths | Array\<string>                                          | Yes  | Applications to install.|
| installParam | [InstallParam](#installparam)                           | No  | Application installation parameters.      |

**Return value**

| Type               | Description                                                   |
| ------------------- | ------------------------------------------------------- |
| Promise&lt;void&gt; | Promise that returns no value. If the operation fails, an error object will be thrown.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9201002  | Failed to install the application.                           |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Install the application for the current user.
let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let hapFilePaths: Array<string> = ['/data/storage/el2/base/haps/entry/testinstall/ExtensionTest.hap'];

bundleManager.install(wantTemp, hapFilePaths).then(() => {
  console.info('Succeeded in installing bundles.');
}).catch((err: BusinessError) => {
  console.error(`Failed to install bundles. Code is ${err.code}, message is ${err.message}`);
});
```

```ts
import { bundleManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

// Install the application for all users.
let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let hapFilePaths: Array<string> = ['/data/storage/el2/base/haps/entry/testinstall/ExtensionTest.hap'];
const params: Record<string, string> = {
  'ohos.bms.param.enterpriseForAllUser': 'true'
};
let installParam: bundleManager.InstallParam = {
  // Replace with actual values.
  userId: 100,
  installFlag: 0,
  parameters: params
};
bundleManager.install(wantTemp, hapFilePaths, installParam).then(() => {
  console.info('Succeeded in installing bundles.');
}).catch((err: BusinessError) => {
  console.error(`Failed to install bundles. Code is ${err.code}, message is ${err.message}`);
});
```

## bundleManager.getInstalledBundleList<sup>20+</sup>

getInstalledBundleList(admin: Want, accountId: number): Promise\<Array\<BundleInfo>>

Obtains the applications installed by a specified user on a device. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                  |
| ------------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.        |
| accountId    | number                                                  | Yes  | User ID. The value is a positive integer greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the user ID.|

**Return value**

| Type               | Description                                                   |
| ------------------- | ------------------------------------------------------- |
| Promise&lt;Array&lt;[BundleInfo](#bundleinfo20)&gt;&gt; | Promise used to return the bundle information of the installed application.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let accountId: number = 100;
bundleManager.getInstalledBundleList(wantTemp, accountId).then((result) => {
  console.info('Succeeded in getting installed bundle list.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle list. Code is ${err.code}, message is ${err.message}`);
});
```

## bundleManager.getInstalledBundleList<sup>23+</sup>

getInstalledBundleList(admin: Want, accountId: number, bundleInfoGetFlag: number): Promise\<Array\<BundleInfo>>

Obtains the list of applications installed by a specified user based on the specified **bundleInfoGetFlag**. This API uses a promise to return the result.

**Required permissions**: ohos.permission.ENTERPRISE_GET_ALL_BUNDLE_INFO

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                  |
| ------------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.        |
| accountId    | number                                                  | Yes  | User ID. The value is a positive integer greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of @ohos.account.osAccount to obtain the user ID.|
| [bundleInfoGetFlag](js-apis-enterprise-bundleManager.md#bundleinfogetflag23)    | number              | Yes  | Type of the bundle information to obtain.|

**Return value**

| Type               | Description                                                   |
| ------------------- | ------------------------------------------------------- |
| Promise&lt;Array&lt;[BundleInfo](#bundleinfo20)&gt;&gt; | Promise used to return the bundle information of the installed application.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let accountId: number = 100;
let bundleInfoGetFlag: number = bundleManager.BundleInfoGetFlag.WITH_APPLICATION_INFO
  | bundleManager.BundleInfoGetFlag.WITH_SIGNATURE_INFO;
bundleManager.getInstalledBundleList(wantTemp, accountId, bundleInfoGetFlag).then((result) => {
  console.info('Succeeded in getting installed bundle list.');
}).catch((err: BusinessError) => {
  console.error(`Failed to get installed bundle list. Code is ${err.code}, message is ${err.message}`);
});
```

## InstallParam

Defines the parameters for application installation.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name                    | Type                  | Read-Only| Optional| Description                                                        |
| ------------------------ | ---------------------- | ---- | ---- | ------------------------------------------------------------ |
| userId                   | number                 | No  | Yes| User ID, which must be greater than or equal to 0. The default value is the user ID of the caller.   |
| installFlag              | number                 | No  | Yes|Installation flag.<br> - **0**: initial installation.<br>- **1**: overwrite installation.<br>- **2**: installation-free.<br>Default value: **0**|
| parameters<sup>19+</sup> | Record&lt;string, string&gt; | No  | Yes| Extended parameters. The default value is null. The key value can be **ohos.bms.param.enterpriseForAllUser**. If the value is **true**, the application is installed for all users.|

## bundleManager.addInstallationAllowedAppDistributionTypes<sup>20+</sup>

addInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array&lt;AppDistributionType&gt;): void

Adds the distribution type of the application that can be installed. Only applications of the distribution type that is added to [AppDistributionType](#appdistributiontype20) can be installed on the current device.<br>
For details about the distribution type of the application signing certificate, refer to the **appDistributionType** attribute in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md#applicationinfo-1).

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                      | Mandatory| Description                                                        |
| ------------ | -------------------------------------------------------    | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md)    | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| appDistributionTypes  | Array&lt;[AppDistributionType](#appdistributiontype20)&gt;  | Yes  | Distribution types of the application signing certificate.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let appDistributionTypes: Array<bundleManager.AppDistributionType> = [bundleManager.AppDistributionType.APP_GALLERY];
  bundleManager.addInstallationAllowedAppDistributionTypes(wantTemp, appDistributionTypes);
  console.info('Succeeded in adding allowed appDistributionTypes.');
} catch (err) {
  console.error(`Failed to add allowed appDistributionTypes. Code: ${err.code}, message: ${err.message}`);
}
```

## bundleManager.removeInstallationAllowedAppDistributionTypes<sup>20+</sup>

removeInstallationAllowedAppDistributionTypes(admin: Want, appDistributionTypes: Array&lt;AppDistributionType&gt;): void

Removes the distribution type of an application. If only some distribution types in the array are removed, the current device can install applications of the remaining distribution types in the array, but cannot install applications of the distribution types not included in [AppDistributionType](#appdistributiontype20).<br>
For details about the distribution type of the application signing certificate, refer to the **appDistributionType** attribute in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md#applicationinfo-1).

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                      | Mandatory| Description                                                        |
| ------------ | -------------------------------------------------------    | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md)    | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| appDistributionTypes  | Array&lt;[AppDistributionType](#appdistributiontype20)&gt;  | Yes| Distribution types of the application signing certificate.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed.                               |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let appDistributionTypes: Array<bundleManager.AppDistributionType> = [bundleManager.AppDistributionType.APP_GALLERY];
  bundleManager.removeInstallationAllowedAppDistributionTypes(wantTemp, appDistributionTypes);
  console.info('Succeeded in removing allowed appDistributionTypes.');
} catch (err) {
  console.error(`Failed to remove allowed appDistributionTypes. Code: ${err.code}, message: ${err.message}`);
}
```

## bundleManager.getInstallationAllowedAppDistributionTypes<sup>20+</sup>

getInstallationAllowedAppDistributionTypes(admin: Want): Array&lt;AppDistributionType&gt;

Obtains the distribution type of the signing certificate used by applications that can be installed.

**Required permissions**: ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                      | Mandatory| Description                                                        |
| ------------ | -------------------------------------------------------    | ---- | ------------------------------------------------------------ |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md)    | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |

**Return value**

| Type                              | Description                     |
| ---------------------------------- | ------------------------- |
| Array&lt;[AppDistributionType](#appdistributiontype20)&gt; | Distribution types of the application signing certificate.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.edmtest',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  let result: Array<bundleManager.AppDistributionType> = bundleManager.getInstallationAllowedAppDistributionTypes(wantTemp);
  console.info(`Succeeded in getting allowed appDistributionTypes. Result: ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get allowed appDistributionTypes. Code: ${err.code}, message: ${err.message}`);
}
```

## bundleManager.installMarketApps<sup>22+</sup>

installMarketApps(admin: Want, bundleNames: Array\<string>): void

Downloads and installs an application from AppGallery.
> **NOTE**
>
> After this API is successfully called, an application download task is generated on the home screen. The task is the same as that created during download from AppGallery. Upon completion of the download and installation, the installation result is returned through the [EnterpriseAdminExtensionAbility.onMarketAppInstallResult](./js-apis-EnterpriseAdminExtensionAbility.md#enterpriseadminextensionabilityonmarketappinstallresult22) callback.<!--RP1--><!--RP1End-->

**Required permissions**: ohos.permission.ENTERPRISE_INSTALL_BUNDLE

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                  |
| ------------ | ------------------------------------------------------- | ---- | ---------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.        |
| bundleNames    | Array&lt;string&gt;                                                  | Yes  | Application bundle name list. A maximum of 10 bundle names can be passed at a time. The bundle name must be the same as that on AppGallery. Otherwise, the download task cannot be created, and error code 9201002 will be reported.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 9201002  | Failed to install the application. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { bundleManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let bundleNames: Array<string> = [ 'com.huaweicloud.m' ];
try {
    bundleManager.installMarketApps(wantTemp, bundleNames);
    console.info(`Succeeded in installing market apps.`);
} catch(err) {
    console.error(`Failed to install market apps. Code: ${err.code}, message: ${err.message}`);
}
```

## AppDistributionType<sup>20+</sup>

Defines the distribution type of the application signing certificate. For details, please refer to the **appDistributionType** attribute of [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md#applicationinfo-1).

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name        | Value| Description                           |
| ----------- | -------- | ------------------------------- |
| APP_GALLERY | 1  | Application installed from AppGallery.|
| ENTERPRISE | 2  | Enterprise application.|
| ENTERPRISE_NORMAL | 3  | Common enterprise application.|
| ENTERPRISE_MDM | 4  | Enterprise MDM application.|
| INTERNALTESTING | 5  | Application under internal testing of AppGallery.|
| CROWDTESTING | 6  | Crowdtesting application.|

## BundleInfo<sup>20+</sup>

Describes the application bundle information.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name                             | Type                                                        | Read-Only| Optional| Description                                                        |
| --------------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| name                              | string                                                       | Yes  | No  | Name of the application bundle. It corresponds to the **bundleName** field in the [app.json5](../../quick-start/app-configuration-file.md) file.|
| vendor                            | string                                                       | Yes  | No  | Vendor of the application bundle. It corresponds to the **vendor** field in the [app.json5](../../quick-start/app-configuration-file.md) file.|
| versionCode                       | number                                                       | Yes  | No  | Version code of the application bundle. It corresponds to the **versionCode** field in the [app.json5](../../quick-start/app-configuration-file.md) file.|
| versionName                       | string                                                       | Yes  | No  | Version description of the application bundle. It corresponds to the **versionName** field in the [app.json5](../../quick-start/app-configuration-file.md) file.|
| minCompatibleVersionCode          | number                                                       | Yes  | No  | Minimum compatible version of the application bundle in the distributed scenario. It corresponds to the **minCompatibleVersionCode** field in the [app.json5](../../quick-start/app-configuration-file.md) file.|
| targetVersion                     | number                                                       | Yes  | No  | Target version of the application. It corresponds to the **targetAPIVersion** field in the [app.json5](../../quick-start/app-configuration-file.md) file.|
| appInfo                           | [ApplicationInfo](#applicationinfo20)                        | Yes  | No  | Application information.|
| signatureInfo                     | [SignatureInfo](#signatureinfo20)                            | Yes  | No  | Signature information of the bundle.|
| installTime                       | number                                                       | Yes  | No  | Timestamp for the installation of the application bundle. It measures the milliseconds elapsed since the Unix epoch (January 1, 1970, 08:00:00 UTC+8).|
| updateTime                        | number                                                       | Yes  | No  | Timestamp for the last update of the application bundle. It measures the milliseconds elapsed since the Unix epoch (January 1, 1970, 08:00:00 UTC+8).|
| appIndex                          | number                                                       | Yes  | No  | Index of an application clone. It takes effect only for application clones.|
| firstInstallTime                  | number                                                       | Yes  | Yes  | Timestamp for the initial installation of the application bundle. It measures the milliseconds elapsed since the Unix epoch (January 1, 1970, 08:00:00 UTC+8). For preinstalled applications, the initial installation timestamp is 1533657660000.|


## SignatureInfo<sup>20+</sup>

Describes the signature information of the bundle.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name     | Type          | Read-Only| Optional| Description                       |
| --------- | -------------- | ---- | ---- | --------------------------- |
| appId     | string         | Yes  | No  | Application ID, which is a unique identifier of the application. For details, see [What Is appId](../../quick-start/common_problem_of_application.md#what-is-appid).                |
|fingerprint| string         | Yes  | No  | Fingerprint information of the application package. It is generated by calculating the hash value of the signing certificate using the SHA-256 algorithm. This field changes when the used signing certificate changes.         |
|appIdentifier| string         | Yes  | No  | Unique ID of the application. For details, see [What Is appIdentifier](../../quick-start/common_problem_of_application.md#what-is-appidentifier).         |
|certificate| string         | Yes  | Yes  | Public key of the application certificate.          |


## ApplicationInfo<sup>20+</sup>

Defines the application information.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name                      | Type                                                        | Read-Only| Optional| Description                                                        |
| -------------------------- | ------------------------------------------------------------ | ---- | ---- | ------------------------------------------------------------ |
| name                       | string                                                       | Yes  | No  | Name of the application bundle. It corresponds to the **bundleName** field in the [app.json5](../../quick-start/app-configuration-file.md) file.                                                |
| description                | string                                                       | Yes  | No  | Description of the application. It corresponds to the **description** field in [app.json5](../../quick-start/app-configuration-file.md). For details about **description**, see the **descriptionResource** field in this table.|
| descriptionId              | number                                                       | Yes  | No  | Resource ID of the application description. It is automatically generated during compilation and build based on the description configured for the application.|
| enabled                    | boolean                                                      | Yes  | No  | Whether the application is enabled. **true** if enabled, **false** otherwise.|
| label                      | string                                                       | Yes  | No  | Application label.|
| labelId                    | number                                                       | Yes  | No  | Resource ID of the application label. It is automatically generated during compilation and build based on the label configured for the application.|
| icon                       | string                                                       | Yes  | No  | Application icon. It corresponds to the **icon** field in the [app.json5](../../quick-start/app-configuration-file.md) file. For details about **icon**, see the **iconResource** field in this table.|
| iconData<sup>23+</sup>     | string                                                       | Yes  | No  | Application icon, which is in Base64 encoding format.|
| iconId                     | number                                                       | Yes  | No  | Resource ID of the application icon. It is automatically generated during compilation and build based on the icon configured for the application.|
| process                    | string                                                       | Yes  | No  | Process name.|
| codePath                   | string                                                       | Yes  | No  | Installation directory of the application.|
| removable                  | boolean                                                      | Yes  | No  | Whether the application is removable. **true** if removable, **false** otherwise.|
| accessTokenId             | number                                                       | Yes  | No  | Access token ID of the application, which is used in the [application access control verification API](../apis-ability-kit/js-apis-abilityAccessCtrl.md#checkaccesstoken9).|
| uid                       | number                                                       | Yes  | No  | UID of the application.|
| iconResource              | [Resource](#resource20) | Yes| No| Resource information of the application icon, including the bundle name, module name, and ID of the resource.|
| labelResource             | [Resource](#resource20) | Yes| No| Resource information of the application label, including the bundle name, module name, and ID of the resource.|
| descriptionResource       | [Resource](#resource20) | Yes| No| Resource information of the application description, including the bundle name, module name, and ID of the resource.|
| appDistributionType       | string                                                       | Yes  | No  | Distribution type of the application signing certificate. For details, see the **appProvisionType** field in [ApplicationInfo](../apis-ability-kit/js-apis-bundleManager-applicationInfo.md#applicationinfo-1).|
| appProvisionType          | string                                                       | Yes  | No  | Type of the application signing certificate file. The options are **debug** and **release**.|
| systemApp          | boolean                                                       | Yes  | No  | Whether the application is a system application. **true** if it is a system application, **false** otherwise.|
| debug       | boolean                                | Yes  | No  | Whether the application is running in debug mode. **true** if in debug mode, **false** otherwise.|
| dataUnclearable       | boolean                      | Yes  | No  | Whether the application data is unclearable. The value **true** means that the application data is unclearable, and **false** means the opposite.|
| nativeLibraryPath | string                                                                     | Yes  | No  | Local library file path of the application.|
| appIndex    | number    | Yes  | No  | Index of an application clone. It takes effect only for application clones.|
| installSource    | string    | Yes  | No  | Installation source of the application. The options are as follows:<br> - **pre-installed**: The application is a preset application installed at initial device startup.<br> - **ota**: The application is a preset application added during system upgrade.<br> - **recovery**: The preset application is uninstalled and then restored.<br> - **bundleName**: The application corresponding to the bundle name is installed.<br> - **unknown**: The installation source is unknown.|
| releaseType      | string    | Yes  | No  | Release type of the SDK used for application packing. Currently, the SDK release types include Canary, Beta, and Release. Each of the Canary and Beta releases can be distinguished by a sequential number, such as Canary1, Canary2, Beta1, and Beta2. You can compare the SDK release type on which application packaging depends and the OS release type (specified by [deviceInfo.distributionOSReleaseType](../apis-basic-services-kit/js-apis-device-info.md)) to determine the compatibility.|


## Resource<sup>20+</sup>

Describes application resource information, including the bundle name, module name, and resource ID.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name        | Type    | Read-Only  | Optional |Description         |
| ---------- | ------ | ----- | ----  | ---------------|
| bundleName | string | No   | No| Bundle name of the application.|
| moduleName | string | No   | No| Module name of the application.|
| id         | number | No   | No| Resource ID.     |

## BundleInfoGetFlag<sup>23+</sup>

Enumerates the bundle flags, which indicate the type of bundle information to obtain.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

| Name                          | Value       | Description                                                        |
| --------------------------    | ---------- | ------------------------------------------------------------ |
| DEFAULT                       | 0 | Obtains the default bundle information, excluding **applicationInfo** and **signatureInfo**.|
| WITH_APPLICATION_INFO         | 1 << 0 | Obtains the default bundle information and **applicationInfo** (excluding **iconData**).|
| WITH_SIGNATURE_INFO           | 1 << 1 | Obtains the default bundle information and **signatureInfo**.|
| WITH_APPLICATION_ICON_INFO    | 1 << 2 | Obtains the default bundle information and **applicationInfo** (including **iconData**).|
