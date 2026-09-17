# bindDevice

## Modules to Import

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## bindDevice

```TypeScript
function bindDevice(deviceAddress: PartnerDeviceAddress, deviceCapability: DeviceCapability,
    businessCapability: BusinessCapability, partnerAgentExtensionAbilityName: string): Promise<void>
```

Bind the partner device. After successfully binding the device, if the device meets the discovery requirements, the [PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md) of the application will be launched.  
- If the [supportBR](arkts-connectivity-partneragent-devicecapability-i.md#supportbr) in the capability variable is set to true,  
the application's ability will be launched when the device is connected via Bluetooth.  
- If the [supportBleAdvertiser](arkts-connectivity-partneragent-devicecapability-i.md#supportbleadvertiser) in the capability variable is set to true,  
the application's ability will be launched when the device is detected via Bluetooth scanning.

Note: The device must be paired first.

**Since:** 23

**Required permissions:** ohos.permission.ACCESS_BLUETOOTH

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| deviceAddress | [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | Yes | The address of partner device. |
| deviceCapability | [DeviceCapability](arkts-connectivity-partneragent-devicecapability-i.md) | Yes | The capability of partner device. |
| businessCapability | [BusinessCapability](arkts-connectivity-partneragent-businesscapability-i.md) | Yes | The business capability of application. |
| partnerAgentExtensionAbilityName | string | Yes | The name of PartnerAgentExtensionAbility. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;void&gt; | Promise used to return the result. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [34900003](../errorcode-fusionConnectivity.md#34900003-device-not-paired) | The device is not paired. |
| [34900004](../errorcode-fusionConnectivity.md#34900004-device-address-registered) | The device has already been bound to the PartnerAgentExtensionAbility. |
| [34900005](../errorcode-fusionConnectivity.md#34900005-bluetooth-disabled) | Bluetooth disabled. |
| [34900099](../errorcode-fusionConnectivity.md#34900099-operation-failed) | Internal error. |
