# addDisallowedUninstallBundlesSync

## Modules to Import

```TypeScript
import { bundleManager } from '@kit.MDMKit';
```

## addDisallowedUninstallBundlesSync

```TypeScript
function addDisallowedUninstallBundlesSync(admin: Want, appIds: Array<string>, accountId?: number): void
```

Adds the applications that are not allowed to be uninstalled by the current or specified user.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_SET_BUNDLE_INSTALL_POLICY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| appIds | Array&lt;string&gt; | Yes | Application IDs.<br>Value range: The total number of entries in this list for a single user must not exceed 200. For example, if user 100 already has 50 entries and user 101 has none, user 100 can add up to 150 more entries, while user 1 01 can add up to 200 entries. You are advised to configure a maximum of 50 entries at a time to prevent potential performance problems. <br>Note: From API version 21 onwards, the **appId** and **appIdentifier** of the app can be passed. **appIdentifier** is recommended. In API version 20 and earlier versions, only **appId** can be passed. |
| accountId | number | No | User ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of **@ohos.account.osAccount** to obtain the user ID. <br> - If **accountId** is passed in, this API applies to the specified user. <br> - If **accountId** is not passed in, this API applies to the current user. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
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
