# addHiddenSettingsMenu

## Modules to Import

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## addHiddenSettingsMenu

```TypeScript
function addHiddenSettingsMenu(admin: Want, menusToHidden: Array<SettingsMenu>): void
```

Adds a setting item to the hidden setting item list of the current user. Then the setting item is hidden in the current user's settings menu and cannot be found in settings search. Even if the setting item is located through some means, it cannot be opened when tapped. The settings take effect immediately after the API is called. The Settings application does not need to be restarted.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| menusToHidden | Array&lt;[SettingsMenu](arkts-mdm-devicesettings-settingsmenu-e.md)&gt; | Yes | Hidden setting item list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9200016](../errorcode-enterpriseDeviceManager.md#9200016-service-timeout) | Service timeout. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let menusToHidden: Array<deviceSettings.SettingsMenu> = [
  // Replace or add items as needed.
  deviceSettings.SettingsMenu.ACCOUNT_ID,
  deviceSettings.SettingsMenu.WIFI,
]

try {
  deviceSettings.addHiddenSettingsMenu(wantTemp, menusToHidden);
  console.info('Succeeded in adding hidden settings menu.');
} catch (err) {
  console.error(`Failed to add hidden settings menu. Code: ${err.code}, message: ${err.message}`);
}
```
