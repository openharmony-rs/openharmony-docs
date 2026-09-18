# @ohos.nearlink.constant(NearLink Common Constants)

This module provides definitions of common constants for NearLink communication, including the device pairing status, device connection status, and device type.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { nearlinkConstant } from '@kit.ConnectivityKit';
```

## Summary

### Enums

| Name | Description |
| --- | --- |
| [AcbState](arkts-connectivity-nearlinkconstant-acbstate-e.md) | Enumerates the logical link connection states with a remote device. |
| [ConnectionState](arkts-connectivity-nearlinkconstant-connectionstate-e.md) | Enumerates the connection states with a remote device. |
| [DeviceClass](arkts-connectivity-nearlinkconstant-deviceclass-e.md) | Enumerates the device types. |
| [PairingState](arkts-connectivity-nearlinkconstant-pairingstate-e.md) | Enumerates the pairing states with a remote device. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ConnectionInterval](arkts-connectivity-nearlinkconstant-connectioninterval-e-sys.md) | Enumerates the connection intervals. A smaller interval indicates a lower latency, higher throughput, but higher power consumption. A larger interval indicates lower power consumption but higher latency. The high-speed mode is suitable for scenarios that require high throughput and low latency, while the low-speed mode is suitable for scenarios that are sensitive to power consumption. |
<!--DelEnd-->
