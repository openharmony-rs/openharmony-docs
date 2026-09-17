# activeSim

## Modules to Import

```TypeScript
import { telephonyManager } from '@kit.MDMKit';
```

## activeSim

```TypeScript
function activeSim(admin: Want, slotId: number): void
```

Activates the SIM card in the specified slot. In scenarios where a SIM card is inserted but not yet activated, this API can be used to activate the SIM card without requiring manual user action. After the SIM card is activated, it can be used for communication. To successfully call this API, the SIM card must be inserted and airplane mode must be turned off.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_TELEPHONY

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| slotId | number | Yes | Slot ID. Currently, only single-slot and dual-slot devices are supported. The value can be **0** or **1**, where **0** indicates slot 1 and **1** indicates slot 2. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [9201017](../errorcode-enterpriseDeviceManager.md#9201017-failed-to-enable-or-disable-the-sim-card) | SIM card activation or deactivation failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [203](../../errorcode-universal.md#203-system-function-prohibited-by-enterprise-management-policies) | This function is prohibited by enterprise management policies. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call the API due to limited device capabilities. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { telephonyManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace the values as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Set the ID of the slot to be activated.
let slotId: number = 0;
try {
  // Activate the SIM card in the specified slot.
  telephonyManager.activeSim(wantTemp, slotId);
  console.info(`success to active SIM`);
} catch (err) {
  console.error(`Failed to active SIM. Code: ${err.code}, message: ${err.message}`);
}
```
