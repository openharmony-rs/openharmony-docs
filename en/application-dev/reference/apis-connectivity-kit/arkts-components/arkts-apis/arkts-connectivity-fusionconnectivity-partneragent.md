# @ohos.FusionConnectivity.partnerAgent

Provides APIs for managing partner agents.

@namespace partnerAgent

**Since:** 23

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.FusionConnectivity.Core

## Modules to Import

```TypeScript
import { partnerAgent } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [bindDevice](arkts-connectivity-partneragent-binddevice-f.md) | Bind the partner device. After successfully binding the device, if the device meets the discovery requirements, the [PartnerAgentExtensionAbility](arkts-connectivity-fusionconnectivity-partneragentextensionability-partneragentextensionability-c.md) of the application will be launched.  - If the [supportBR](arkts-connectivity-partneragent-devicecapability-i.md#supportbr) in the capability variable is set to true,  the application's ability will be launched when the device is connected via Bluetooth.  - If the [supportBleAdvertiser](arkts-connectivity-partneragent-devicecapability-i.md#supportbleadvertiser) in the capability variable is set to true,  the application's ability will be launched when the device is detected via Bluetooth scanning. |
| [getBoundDevices](arkts-connectivity-partneragent-getbounddevices-f.md) | Gets the list of addresses of the bound partner device for this application. |
| [isDeviceBound](arkts-connectivity-partneragent-isdevicebound-f.md) | Checks whether a device is bound to this application. |
| [isDeviceControlEnabled](arkts-connectivity-partneragent-isdevicecontrolenabled-f.md) | Checks whether device control is enabled. |
| [isPartnerAgentSupported](arkts-connectivity-partneragent-ispartneragentsupported-f.md) | Checks whether the current device supports the partner agent feature. |
| [unbindDevice](arkts-connectivity-partneragent-unbinddevice-f.md) | Unbinds a partner device. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [disableDeviceControl](arkts-connectivity-partneragent-disabledevicecontrol-f-sys.md) | Disables device control for a bound device. |
| [enableDeviceControl](arkts-connectivity-partneragent-enabledevicecontrol-f-sys.md) | Enables device control for a bound device. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [BusinessCapability](arkts-connectivity-partneragent-businesscapability-i.md) | Describes the business capabilities of the application. |
| [DeviceCapability](arkts-connectivity-partneragent-devicecapability-i.md) | Describes the capability of a partner device. |
| [PartnerDeviceAddress](arkts-connectivity-partneragent-partnerdeviceaddress-i.md) | Describes the partner device address. |

### Enums

| Name | Description |
| --- | --- |
| [PartnerAgentExtensionAbilityDestroyReason](arkts-connectivity-partneragent-partneragentextensionabilitydestroyreason-e.md) | The enum of reasons for destroying partner agent extension ability. |
