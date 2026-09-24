# setUserRestriction

## Modules to Import

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## setUserRestriction

```TypeScript
function setUserRestriction(admin: Want, settingsItem: string, restricted: boolean): void
```

Sets restrictions on user behaviors.

**Since:** 20

**Deprecated since:** 26.0.0

**Substitutes:** [setUserRestriction](#setuserrestriction-1)(admin: Want, settingsItem: SettingsForDevice, restricted: boolean)

**Required permissions:** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| settingsItem | string | Yes | Behavior name. Only the following values are supported. If other values are passed, an error will be reported.<br>- **setApn**: APN configuration, currently supported only on smartphones and tablets. <br>- **powerLongPress**: capability to open the power menu by long-pressing the power button. Currently, only smartphones and tablets are supported. <br>- **setEthernetIp**: Ethernet IP address configuration, currently supported only on PCs/2-in-1 devices. <br>- **setDeviceName**: device name configuration, currently supported only on PCs/2-in-1 devices, smartphones, and tablets. When it is disabled, the device name cannot be modified in the following settings: **About**, **Bluetooth**, and **More connectivity options**   > **NearLink** on PCs/2-in-1 devices, and **About**, **Bluetooth**, and **Personal hotspot** on smartphones and tablets. <br>- **setBiometricsAndScreenLock**: screen lock password configuration, currently supported only on PCs/2-in- 1 devices, smartphones, and tablets. |
| restricted | boolean | Yes | Whether to disable the action. The value **true** means to disable the action, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { restrictions } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  restrictions.setUserRestriction(wantTemp, 'setApn', true);
  console.info('Succeeded in restricting from setting apn');
} catch (err) {
  console.error(`Failed to restrict from setting apn. Code is ${err.code}, message is ${err.message}`);
}
```


<a id="setuserrestriction-1"></a>

## setUserRestriction

```TypeScript
function setUserRestriction(admin: Want, settingsItem: SettingsForDevice, restricted: boolean): void
```

Restricts users from modifying specified device setting items.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| settingsItem | [SettingsForDevice](arkts-mdm-restrictions-settingsfordevice-e.md) | Yes | Device setting items to be restricted from modification. |
| restricted | boolean | Yes | The value **true** means to disable the action, and **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  restrictions.setUserRestriction(wantTemp, restrictions.SettingsForDevice.SET_APN, true);
  console.info('Succeeded in restricting from setting apn');
} catch (err) {
  console.error(`Failed to restrict from setting apn. Code is ${err.code}, message is ${err.message}`);
}
```
