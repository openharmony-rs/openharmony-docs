# setValueForAccount

## Modules to Import

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## setValueForAccount

```TypeScript
function setValueForAccount(admin: Want, item: SettingsItem, accountId: number, value: string): void
```

Sets the device policy for a specified user. This API allows you to set a specific parameter for a given user, such as setting the device name for user 100.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| item | [SettingsItem](arkts-mdm-devicesettings-settingsitem-e.md) | Yes | Type of the policy to set. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |
| value | string | Yes | Policy type value. <br>When **item** is set to [SettingsItem.DEVICE_NAME](arkts-mdm-devicesettings-settingsitem-e.md), **value** indicates the device name, which is a character string. The string length ranges from 1 to 100. Only the device name of the current user can be set. If the device name of another user is set, error code 9200012 is returned. <br>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](arkts-mdm-devicesettings-settingsitem-e.md), this API can be called properly on phones and tablets but returns error code 801 on other devices. Only the three-button navigation of the current user can be set. Setting other users' three-button navigation does not take effect. The **value** parameter indicates the three-button navigation switch state. <br>- **'0'**: Three-button navigation is enabled. (If the Kiosk mode has been entered via [enterKioskMode](../../apis-ability-kit/arkts-apis/arkts-ability-kioskmanager-enterkioskmode-f.md), the display of three-button navigation requires that the bottom gesture is enabled. Specifically, three-button navigation is displayed only when both the three-button navigation switch and the bottom gesture switch are enabled. The bottom gesture can be enabled or disabled using the [applicationManager.setKioskFeatures](arkts-mdm-applicationmanager-setkioskfeatures-f.md) API.) <br>- **'1'**: Three-button navigation is disabled. |

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
import { deviceSettings } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace with actual values.
  let accountId = 100;
  let deviceName: string = "deviceName"
  deviceSettings.setValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId, deviceName);
  console.info('Succeeded in setting device name.');
} catch (err) {
  console.error(`Failed to set device name. Code: ${err.code}, message: ${err.message}`);
}
```
