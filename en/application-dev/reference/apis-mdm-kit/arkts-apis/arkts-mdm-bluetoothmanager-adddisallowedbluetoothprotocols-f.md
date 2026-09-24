# addDisallowedBluetoothProtocols

## Modules to Import

```TypeScript
import { bluetoothManager } from '@kit.MDMKit';
```

## addDisallowedBluetoothProtocols

```TypeScript
function addDisallowedBluetoothProtocols(admin: Want, accountId: number,  protocols: Array<Protocol>): void
```

Adds disallowed Bluetooth protocols. Specified users cannot use the disallowed Bluetooth protocols to send files to other devices. This API is used to disable the GATT or SPP protocol, which does not take effect for system services and system applications. When the SPP protocol is passed, both the receiving and sending functions are disabled.

**Since:** 20

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |
| protocols | Array&lt;[Protocol](arkts-mdm-bluetoothmanager-protocol-e.md)&gt; | Yes | Bluetooth protocol array, which has a maximum length of 10,000. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bluetoothManager } from '@kit.MDMKit';

// Create an EnterpriseAdminExtensionAbility component.
let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
// Define the user ID. (Replace it as required.)
let accountId: number = 100;
// Define the array of Bluetooth protocols. (Replace it as required.)
let protocols: Array<bluetoothManager.Protocol> = [bluetoothManager.Protocol.GATT, bluetoothManager.Protocol.SPP];
try {
  // Add Bluetooth protocols to the blocklist.
  bluetoothManager.addDisallowedBluetoothProtocols(wantTemp, accountId, protocols);
  console.info('Succeeded in adding disallowed bluetooth protocols policy.');
} catch (err) {
  console.error(`Failed to add disallowed bluetooth protocols. Code: ${err.code}, message: ${err.message}`);
}
```


<a id="adddisallowedbluetoothprotocols-1"></a>

## addDisallowedBluetoothProtocols

```TypeScript
function addDisallowedBluetoothProtocols(admin: Want, accountId: number, protocols: Array<Protocol>, policy: TransferPolicy): void
```

Adds disallowed Bluetooth protocols. After the setting, specified users cannot use the disallowed Bluetooth protocols based on the specified transfer policy.

> **NOTE:** 
> 
> 1. This API is used to disable the GATT or SPP protocol, which does not take effect for system services and system applications.
> 
> 2. When the SPP protocol is passed, the value of the **policy** parameter can only be
> **TransferPolicy.RECEIVE_SEND**. Otherwise, error code 9200012 will be returned.
> 
> 3. This API and [addDisallowedBluetoothProtocols&lt;sup&gt;20+&lt;/sup&gt;](arkts-mdm-bluetoothmanager-adddisallowedbluetoothprotocols-f.md) are overloaded APIs. This API adds the **policy** parameter to specify the transfer policy, enabling more fine-grained control over Bluetooth protocol disabling behavior (for example, blocking only sending, only receiving,or both sending and receiving). If both APIs are used to configure disabling policies, the policies will be combined and take effect.

**Since:** 26.0.0

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| accountId | number | Yes | User ID, which must be greater than or equal to 0. <br> You can call [getOsAccountLocalId](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-osaccount-accountmanager-i.md#getosaccountlocalid) of @ ohos.account.osAccount to obtain the ID. |
| protocols | Array&lt;[Protocol](arkts-mdm-bluetoothmanager-protocol-e.md)&gt; | Yes | Array of Bluetooth protocols to be added to the blocklist. |
| policy | [TransferPolicy](arkts-mdm-bluetoothmanager-transferpolicy-e.md) | Yes | Transfer policy, which specifies the mode for disabling Bluetooth protocols. The options are **SEND_ONLY** (sending disabled), **RECEIVE_ONLY** (receiving disabled), and **RECEIVE_SEND** (sending and receiving disabled). |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [9200012](../errorcode-enterpriseDeviceManager.md#9200012-parameter-verification-failed) | Parameter verification failed. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |

**Examples**

```TypeScript
import { Want } from '@kit.AbilityKit';
import { bluetoothManager } from '@kit.MDMKit';

// Create an EnterpriseAdminExtensionAbility component.
let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Define the user ID.
let accountId: number = 100;
// Define the Bluetooth protocol array.
let protocols: Array<bluetoothManager.Protocol> = [
  bluetoothManager.Protocol.GATT,
  bluetoothManager.Protocol.SPP,
  bluetoothManager.Protocol.OPP
];

try {
  // Add Bluetooth protocols to the blocklist and specify the transfer policy as disabling sending and receiving.
  bluetoothManager.addDisallowedBluetoothProtocols(wantTemp, accountId, protocols, bluetoothManager.TransferPolicy.RECEIVE_SEND);
  console.info('Succeeded in adding disallowed bluetooth protocols.');
} catch (err) {
  console.error(`Failed to add disallowed bluetooth protocols. Code is ${err.code}, message is ${err.message}`);
}
```
