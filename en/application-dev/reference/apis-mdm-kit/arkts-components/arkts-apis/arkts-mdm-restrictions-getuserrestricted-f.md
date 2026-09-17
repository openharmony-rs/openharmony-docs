# getUserRestricted

## Modules to Import

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## getUserRestricted

```TypeScript
function getUserRestricted(admin: Want, settingsItem: string): boolean
```

Obtains the disabled status of a setting item.

**Since:** 20

**Deprecated since:** 26.0.0

**Substitutes:** [getUserRestricted](arkts-mdm-restrictions-getuserrestricted-f.md)(admin: Want, settingsItem: SettingsForDevice)

**Required permissions:** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| settingsItem | string | Yes | Setting item.<br>- **setEthernetIp**: Ethernet IP address configuration, currently supported only on PCs/2-in-1 devices. <br>- **setDeviceName**: device name configuration, currently supported only on PCs/2-in-1 devices, smartphones, and tablets. When it is disabled, the device name cannot be modified in the following settings: **About**, **Bluetooth**, and **More connectivity options**   > **NearLink** on PCs/2-in-1 devices, and **About**, **Bluetooth**, and **Personal hotspot** on smartphones and tablets. <br>- **setBiometricsAndScreenLock**: screen lock password configuration, currently supported only on PCs/2-in- 1 devices, smartphones, and tablets. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Disabled status of the specified setting item. The value **true** means the item is disabled; the value **false** means the opposite. |

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
  // Replace input parameters with actual values.
  let result: boolean = restrictions.getUserRestricted(wantTemp, 'setEthernetIp');
  console.info('Succeeded in getting user restricted');
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}
```

```TypeScript
import { restrictions } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: boolean = restrictions.getUserRestricted(wantTemp, restrictions.SettingsForDevice.SET_APN);
  console.info(`Succeeded in getting user restricted: ${result}`);
} catch (err) {
  console.error(`Failed to get user restricted. Code is ${err.code}, message is ${err.message}`);
}
```


## getUserRestricted

```TypeScript
function getUserRestricted(admin: Want | null, settingsItem: SettingsForDevice): boolean
```

Obtains the disabled status of the specified device setting item.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_SET_USER_RESTRICTION

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) &#124; null | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the. EnterpriseAdminExtensionAbility and the bundle name of the application.<br>If the device has multiple MDM applications, you can pass **admin** to query the corresponding policies. If **null** is passed, the policies that actually take effect on the device are returned. |
| settingsItem | [SettingsForDevice](arkts-mdm-restrictions-settingsfordevice-e.md) | Yes | Device setting item to be queried. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Disabled status of the specified device setting item. The value **true** means the item is disabled; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

See [getUserRestricted](#getuserrestricted)
