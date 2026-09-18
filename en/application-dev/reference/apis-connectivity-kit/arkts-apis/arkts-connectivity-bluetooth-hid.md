# @ohos.bluetooth.hid

Provides methods to accessing bluetooth HID(Human Interface Device)-related capabilities.

**Since:** 10

**System capability:** SystemCapability.Communication.Bluetooth.Core

## Modules to Import

```TypeScript
import { hid } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [createHidDeviceProfile](arkts-connectivity-hid-createhiddeviceprofile-f.md) | Creates the instance of HID device profile. |
| [createHidHostProfile](arkts-connectivity-hid-createhidhostprofile-f.md) | create the instance of hid profile. |

### Interfaces

| Name | Description |
| --- | --- |
| [GetReportData](arkts-connectivity-hid-getreportdata-i.md) | Describe the GET_REPORT data is received from remote host. |
| [HidDeviceProfile](arkts-connectivity-hid-hiddeviceprofile-i.md) | Manager HID device profile. |
| [HidDeviceQos](arkts-connectivity-hid-hiddeviceqos-i.md) | Represents the Quality of Service (QoS) settings for a bluetooth hid device application. |
| [HidDeviceSdp](arkts-connectivity-hid-hiddevicesdp-i.md) | Describe the HID device capability fields of this endpoint being queried. |
| [InterruptData](arkts-connectivity-hid-interruptdata-i.md) | Describe the interrupt data is received from remote host. |
| [ProtocolData](arkts-connectivity-hid-protocoldata-i.md) | Describe the protocol data is received from remote host. |
| [SetReportData](arkts-connectivity-hid-setreportdata-i.md) | Describe the SET_REPORT data is received from remote host. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [HidHostProfile](arkts-connectivity-hid-hidhostprofile-i-sys.md) | Manager hid host profile. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ErrorReason](arkts-connectivity-hid-errorreason-e.md) | Describe the error reason. |
| [ProtocolType](arkts-connectivity-hid-protocoltype-e.md) | Describe the protocol type. |
| [ReportType](arkts-connectivity-hid-reporttype-e.md) | Describe the report type. |
| [ServiceType](arkts-connectivity-hid-servicetype-e.md) | Describe the l2cap service type. |
| [Subclass](arkts-connectivity-hid-subclass-e.md) | Describe the subclass. |

### Types

| Name | Description |
| --- | --- |
| [BaseProfile](arkts-connectivity-hid-baseprofile-t.md) | Base interface of profile. |
| [BluetoothAddress](arkts-connectivity-hid-bluetoothaddress-t.md) | Bluetooth device address. |
