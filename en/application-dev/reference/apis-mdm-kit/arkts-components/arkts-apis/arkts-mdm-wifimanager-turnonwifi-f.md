# turnOnWifi

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.MDMKit';
```

## turnOnWifi

```TypeScript
function turnOnWifi(admin: Want, isForce: boolean): void
```

Enables Wi-Fi. This API is applicable to enterprise device remote management scenarios, such as administrators remotely enabling Wi-Fi on employee devices, or ensuring that Wi-Fi is turned on when specific policies are enforced.

In the following scenario, attempting to enable Wi-Fi using this API will fail, and a message indicating that the system function is disabled will be returned:

​Wi-Fi has been disabled via [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md). In this case, you must call [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) to enable Wi-Fi.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_WIFI

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| isForce | boolean | Yes | Whether to forcibly enable Wi-Fi. <br>The value **true** means to forcibly enable Wi-Fi. Once enabled, it cannot be disabled manually. You must call [turnOffWifi](arkts-mdm-wifimanager-turnoffwifi-f.md) instead. The value **false** means the opposite and the Wi-Fi can be disabled manually. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { wifiManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  wifiManager.turnOnWifi(wantTemp, true);
  console.info(`Succeeded in turning on Wi-Fi.`);
} catch (err) {
  console.error(`Failed to turn on Wi-Fi. Code: ${err.code}, message: ${err.message}`);
}
```
