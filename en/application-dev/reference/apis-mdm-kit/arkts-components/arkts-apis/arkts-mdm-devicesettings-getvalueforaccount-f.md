# getValueForAccount

## Modules to Import

```TypeScript
import { deviceSettings } from '@kit.MDMKit';
```

## getValueForAccount

```TypeScript
function getValueForAccount(admin: Want, item: SettingsItem, accountId: number): string
```

Obtains the device policy of a specified user. This API allows you to obtain a specific parameter of a given user, such as obtaining the device name of user 100.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_SETTINGS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| item | [SettingsItem](arkts-mdm-devicesettings-settingsitem-e.md) | Yes | Type of the policy to set. The following policy types are supported: **DEVICE_NAME** (device name) and **FLOATING_NAVIGATION** (three-button navigation). |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br>**accountId** can be obtained via APIs such as [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid). |

**Return value:**

| Type | Description |
| --- | --- |
| string | Policy type value. <br>When **item** is set to [SettingsItem.DEVICE_NAME](arkts-mdm-devicesettings-settingsitem-e.md), this API returns the device name of the current user. If the device name of another user is queried, error code 9200012 is returned. <br>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](arkts-mdm-devicesettings-settingsitem-e.md), this API returns the three-key navigation switch state for the specified user. <br>When **item** is set to [SettingsItem.FLOATING_NAVIGATION](arkts-mdm-devicesettings-settingsitem-e.md), this API can be called properly on phones and tablets but returns error code 801 on other devices. |

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
  let result: string = deviceSettings.getValueForAccount(wantTemp, deviceSettings.SettingsItem.DEVICE_NAME, accountId);
  console.info(`Succeeded in getting device name, result : ${result}`);
} catch (err) {
  console.error(`Failed to get device name. Code: ${err.code}, message: ${err.message}`);
}
```
