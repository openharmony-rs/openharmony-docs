# setDisallowedPolicy

## Modules to Import

```TypeScript
import { restrictions } from '@kit.MDMKit';
```

## setDisallowedPolicy

```TypeScript
function setDisallowedPolicy(admin: Want, feature: string, disallow: boolean): void
```

Disallows a feature.

> **NOTE:** 
> 
> This API applies a device-level restriction policy that affects all users of the device. To set a restriction
> policy for a specific user, use the
> [setDisallowedPolicyForAccount](arkts-mdm-restrictions-setdisallowedpolicyforaccount-f.md) API.

**Since:** 12

**Deprecated since:** 26.0.0

**Substitutes:** [setDisallowedPolicy](#setdisallowedpolicy-1)(admin: Want, feature: FeatureForDevice, disallow: boolean)

**Required permissions:** 
- API version 20 and later: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS or ohos.permission.ENTERPRISE_MANAGE_NETWORK
- API versions 15 to 19: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS
- API versions 12 to 14: ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| feature | string | Yes | For features that can be set, see Table 1. <br> **Note:** Since API version 15, applications granted with the ohos.permission.PERSONAL_MANAGE_RESTRICTIONS permission and activated as the [BDA](../../../mdm/mdm-kit-term.md#byod-device-admin-bdabyod) via [startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md) can use this API to set the following features: bluetooth, hdc, microphone, usb, wifi, tethering, and camera. Since API version 26.0.0, this API can also be used to set the mtpServer feature. |
| disallow | boolean | Yes | Whether to disallow the feature. The value **true** means to disallow the feature; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [9200013](../errorcode-enterpriseDeviceManager.md#9200013-control-not-immediately-effective) | The enterprise management policy has been successfully set, but the function has not taken effect in real time.<br>**Applicable version:** 21 and later |

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
  // Replace parameters with actual values.
  restrictions.setDisallowedPolicy(wantTemp, 'printer', true);
  console.info('Succeeded in setting printer disabled');
} catch (err) {
  console.error(`Failed to set printer disabled. Code is ${err.code}, message is ${err.message}`);
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
  restrictions.setDisallowedPolicy(wantTemp, restrictions.FeatureForDevice.WIFI_P2P, true);
  console.info('Succeeded in setting Wi-Fi P2P disabled');
} catch (err) {
  console.error(`Failed to set Wi-Fi P2P disabled. Code is ${err.code}, message is ${err.message}`);
}
```


## setDisallowedPolicy

```TypeScript
function setDisallowedPolicy(admin: Want, feature: FeatureForDevice, disallow: boolean): void
```

Enables or disables a specified device feature. Once disabled, the feature cannot be used.

**Since:** 24

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_RESTRICTIONS or ohos.permission.PERSONAL_MANAGE_RESTRICTIONS

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| feature | [FeatureForDevice](arkts-mdm-restrictions-featurefordevice-e.md) | Yes | Device feature to be enabled or disabled. <br> **Note:** An application granted with the ohos.permission.PERSONAL_MANAGE_RESTRICTIONS permission and activated as the [BDA](../../../mdm/mdm-kit-term.md#byod-device-admin-bdabyod) via [startAdminProvision](arkts-mdm-adminmanager-startadminprovision-f.md) can use this API to set the [FeatureForDevice.WIFI_P2P](arkts-mdm-restrictions-featurefordevice-e.md) feature. |
| disallow | boolean | Yes | Whether to disallow the feature. The value **true** means to disallow the feature; the value **false** means the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [9200013](../errorcode-enterpriseDeviceManager.md#9200013-control-not-immediately-effective) | The enterprise management policy has been successfully set, but the function has not taken effect in real time. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

See [setDisallowedPolicy](#setdisallowedpolicy)
