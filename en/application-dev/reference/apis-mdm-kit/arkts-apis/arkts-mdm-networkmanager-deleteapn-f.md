# deleteApn

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## deleteApn

```TypeScript
function deleteApn(admin: Want, apnId: string): void
```

Deletes the APN. This API is suitable for enterprise mobile network configuration management scenarios, such as removing invalid APN configurations, adjusting mobile network access point settings, and preventing the use of incorrect APN configurations. It helps enterprises maintain correct mobile network configurations and ensure that devices connect to mobile networks through the appropriate access points.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_APN

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| apnId | string | Yes | APN ID to be deleted. After the setting, the system will remove the APN configuration, and the corresponding access point will no longer be available. You can obatin the device APN information via [networkManager.queryApn](arkts-mdm-networkmanager-queryapn-f.md). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnId: string = "1"; // Replace it as required.
try {
  networkManager.deleteApn(wantTemp, apnId);
  console.info(`Succeeded in deleting apn.`);
} catch (err) {
  console.error(`Failed to delete apn. Code: ${err.code}, message: ${err.message}`);
}
```
