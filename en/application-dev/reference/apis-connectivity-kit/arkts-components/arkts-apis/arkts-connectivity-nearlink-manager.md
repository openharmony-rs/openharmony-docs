# @ohos.nearlink.manager(Basic NearLink Management Capability)

This module provides basic NearLink management capabilities, including enabling or disabling NearLink, obtaining the MAC address of the local device, and setting the connection mode.

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLocalName](arkts-connectivity-manager-getlocalname-f.md) | Queries the NearLink name on the local device. |
| [getPairedDevices](arkts-connectivity-manager-getpaireddevices-f.md) | Obtains the devices paired with the current device. |
| [getState](arkts-connectivity-manager-getstate-f.md) | Queries the NearLink status. |
| [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) | Checks whether the current device supports NearLink. |
| [offStateChange](arkts-connectivity-manager-offstatechange-f.md) | Unsubscribes from the NearLink status change event. This API uses an asynchronous callback to return the result. |
| [onStateChange](arkts-connectivity-manager-onstatechange-f.md) | Subscribes to the NearLink status change event. This API uses an asynchronous callback to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [disable](arkts-connectivity-manager-disable-f-sys.md) | Disables NearLink. |
| [enable](arkts-connectivity-manager-enable-f-sys.md) | Enables NearLink. |
| [factoryReset](arkts-connectivity-manager-factoryreset-f-sys.md) | Restores a device to its factory settings. This API uses a promise to return the result. |
| [getLocalAddress](arkts-connectivity-manager-getlocaladdress-f-sys.md) | Queries the MAC address of the local device. |
| [setConnectionMode](arkts-connectivity-manager-setconnectionmode-f-sys.md) | Sets the connection mode. This API uses a promise to return the result. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md) | Enumerated the NearLink statuses. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [ConnectionMode](arkts-connectivity-manager-connectionmode-e-sys.md) | Enumerates the connection modes. |
<!--DelEnd-->
