# removeDockApp

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## removeDockApp

```TypeScript
function removeDockApp(admin: Want, bundleName: string, abilityName: string): void
```

Removes an application from the shortcut bar.

> **NOTE:** 
> 
> The following applications cannot be removed from the shortcut bar using this API: Application Center, Task
> Center, Files, and Recycle Bin. Otherwise, error code 9201018 will be reported.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleName | string | Yes | Bundle name of the application. |
| abilityName | string | Yes | Ability name of the application. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9201016](../errorcode-enterpriseDeviceManager.md#9201016-specified-application-not-in-dock) | The application has not been added to the Dock. |
| [9201018](../errorcode-enterpriseDeviceManager.md#9201018-specified-application-inoperable) | The application is inoperable. |
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

try {
  // Replace it as required.
  let bundleName: string = 'com.example.exampleapplication';
  let abilityName: string = 'EntryAbility';
  applicationManager.removeDockApp(wantTemp, bundleName, abilityName);
  console.info('Succeeded in removing dock app.');
} catch(err) {
  console.error(`Failed to remove dock app. Code: ${err.code}, message: ${err.message}`);
}
```
