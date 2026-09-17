# setInstallLocalEnterpriseAppEnabledForAccount

## Modules to Import

```TypeScript
import { systemManager } from '@kit.MDMKit';
```

## setInstallLocalEnterpriseAppEnabledForAccount

```TypeScript
function setInstallLocalEnterpriseAppEnabledForAccount(admin: Want, isEnable: boolean, accountId: number): void
```

Sets whether local installation of enterprise applications is supported for a specified user. After the policy of supporting local enterprise application installation is delivered to a PC/2-in-1 enterprise device that has the local installation capability, the user can double-click an enterprise application installation package on the desktop or in the Files application to install it.

Only enterprise applications signed with the **enterprise_normal** or **enterprise_mdm** signature type are supported.

> **NOTE:** 
> 
> A PC/2-in-1 enterprise device supports local installation of enterprise applications for the current user if any
> of the following conditions is met:
> 
> 1. The offline installer has been enabled by calling [setInstallLocalEnterpriseAppEnabled](arkts-mdm-systemmanager-setinstalllocalenterpriseappenabled-f.md).
> 
> 2. Local installation of enterprise applications is enabled for the current user by calling this API.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SYSTEM

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| isEnable | boolean | Yes | Whether local installation of enterprise applications is supported. The value **true** indicates that the local installation of enterprise applications is supported, and the value **false** indicates the opposite. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { systemManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace with actual values.
let isEnable: boolean = true;
let accountId: number = 100;
try {
  systemManager.setInstallLocalEnterpriseAppEnabledForAccount(wantTemp, isEnable, accountId);
  console.info('Succeeded in setting InstallLocalEnterpriseAppEnabledForAccount.');
} catch (err) {
  console.error(`Failed to set installLocalEnterpriseAppEnabledForAccount. Code is ${err.code}, message is ${err.message}`);
}
```
