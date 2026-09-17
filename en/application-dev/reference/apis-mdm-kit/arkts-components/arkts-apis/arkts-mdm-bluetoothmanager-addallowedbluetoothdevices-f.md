# addAllowedBluetoothDevices

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
```

## addAllowedBluetoothDevices

```TypeScript
function addAllowedBluetoothDevices(admin: Want, deviceIds: Array<string>): void
```

Adds Bluetooth devices to the trustlist. After adding devices to this list, the current device will only be allowed to connect to Bluetooth devices in the list. Since API version 22, the MAC addresses in the array must comply with the Bluetooth MAC address specifications (for example, 00:1A:2B:3C:4D:5E). Invalid MAC addresses will be removed and only valid MAC addresses will be added.

A policy conflict is reported when this API is called in the following scenarios:

1. Bluetooth has been disabled via [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md).
In this case, you can call [setDisallowedPolicy](arkts-mdm-restrictions-setdisallowedpolicy-f.md) enable Bluetooth to solve the conflict.
2. Disallowed Bluetooth devices have been added by calling [addDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-adddisallowedbluetoothdevices-f.md).
You can resolve the conflict by removing disallowed Bluetooth devices through [removeDisallowedBluetoothDevices](arkts-mdm-bluetoothmanager-removedisallowedbluetoothdevices-f.md).

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| deviceIds | Array&lt;string&gt; | Yes | MAC addresses of the Bluetooth devices to add. The maximum number of allowed Bluetooth devices is 1,000. If there are already 300 MAC addresses of the devices, only 700 more can be added. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200010](../errorcode-enterpriseDeviceManager.md#9200010-policy-conflict) | A conflict policy has been configured. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

// Create an EnterpriseAdminExtensionAbility component.
let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Define the array of Bluetooth device MAC addresses. (Replace it as required.)
let deviceIds: Array<string> = ["00:1A:2B:3C:4D:5E","AA:BB:CC:DD:EE:FF"];
try {
  // Add Bluetooth devices to the trustlist.
  bluetoothManager.addAllowedBluetoothDevices(wantTemp,deviceIds);
  console.info(`Succeeded in adding allowed bluetooth devices.`);
} catch(err) {
  console.error(`Failed to add allowed bluetooth devices. Code: ${err.code}, message: ${err.message}`);
}
```
