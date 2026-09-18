# addDockApp

## Modules to Import

```TypeScript
import { applicationManager } from '@kit.MDMKit';
```

## addDockApp

```TypeScript
function addDockApp(admin: Want, bundleName: string, abilityName: string, index?: number): void
```

Adds an application to the bottom shortcut bar of a PC/2-in-1 device based on the location index. Then users can tap the application icon in the shortcut bar to directly launch the application. The application icon is the default icon displayed on the home screen.

> **NOTE:** 
> 
> 1. If location 0 or 1 is already occupied by the application center or task center, adding an application to that location returns error code 9201019. If that location is occupied by another app, the addition succeeds.
> 
> 2. The following applications cannot be added to the shortcut bar using this API: Application Center, Task Center, Files, and Recycle Bin.
> 
> 3. Only applications with an entry (that is, an icon) can be added.
> 
> 4. Only the shortcut bar of the current user can be configured. Each user's shortcut bar can contain a maximum of 100 applications.
> 
> 5. When a new application is inserted into an occupied location, the new application will directly take that location, and the original application along with all subsequent applications will shift back by one location.
> 
> 6. If the **index** parameter is not passed or the passed value is greater than the number of applications in the shortcut bar, the new application is added to the end of the shortcut bar by default.
> 
> 7. After an application is added to the shortcut bar using this API, users can manually remove the application or adjust its position.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APPLICATION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| bundleName | string | Yes | Bundle name of the application. |
| abilityName | string | Yes | Ability name of the application. Only the application entry ability is supported. |
| index | number | No | Location index of the application in the shortcut bar. The value range is [0, 100). The default value is 99.<br>Value range: [0,100). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200015](../errorcode-enterpriseDeviceManager.md#9200015-component-not-exist) | The ability does not exist. |
| [9201013](../errorcode-enterpriseDeviceManager.md#9201013-number-of-applications-in-dock-reaches-maximum) | The number of applications in the Dock has reached the maximum. |
| [9201014](../errorcode-enterpriseDeviceManager.md#9201014-specified-application-already-in-docker) | The application is already in the Dock. |
| [9201015](../errorcode-enterpriseDeviceManager.md#9201015-specified-application-not-installed) | The application is not installed. |
| [9201018](../errorcode-enterpriseDeviceManager.md#9201018-specified-application-inoperable) | The application is inoperable. |
| [9201019](../errorcode-enterpriseDeviceManager.md#9201019-specified-location-inoperable) | The location is inoperable. |
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
  applicationManager.addDockApp(wantTemp, bundleName, abilityName, 3);
  console.info('Succeeded in adding dock app.');
} catch(err) {
  console.error(`Failed to add dock app. Code: ${err.code}, message: ${err.message}`);
}
```
