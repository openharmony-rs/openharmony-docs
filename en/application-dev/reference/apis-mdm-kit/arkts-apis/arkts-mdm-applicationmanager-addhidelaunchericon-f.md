# addHideLauncherIcon

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addHideLauncherIcon

```TypeScript
function addHideLauncherIcon(admin: Want, bundleNames: Array<string>): void
```

Adds applications to the home screen icon hide list.

> **NOTE:** 
> 
> 1. This API can only hide home screen icons for applications of the current user. Hiding application widgets are not supported.
> 
> 2. If a hidden application has clones, the clones are hidden synchronously.
> 
> 3. Not all applications on the home screen can be added to the hidden list. Otherwise, all applications will still be displayed on the home screen.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleNames | Array&lt;string&gt; | Yes | Application bundle name array, which specifies the applications to be hidden. A maximum of 500 applications are supported. |

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
import { applicationManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Replace it as required.
let bundleNames: Array<string> = ['com.example.test'];
try {
  applicationManager.addHideLauncherIcon(wantTemp, bundleNames);
  console.info('Succeeded in adding hide launcher icon.');
} catch (err) {
  console.error(`Failed to add hide launcher icon. Code is ${err.code}, message is ${err.message}`);
}
```
