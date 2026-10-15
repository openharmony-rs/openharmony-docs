# @ohos.nearlink.manager(Basic NearLink Management Capability)

This module provides basic NearLink management capabilities, including enabling or disabling NearLink, obtaining the MAC address of the local device, and setting the connection mode.

**Since:** 26.0.0

<!--Device-unnamed-declare namespace manager--><!--Device-unnamed-declare namespace manager-End-->

**System capability:** SystemCapability.Communication.NearLink.Base

## Modules to Import

```TypeScript
import { manager } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [getLocalName](arkts-connectivity-manager-getlocalname-f.md#getlocalname) | Queries the NearLink name on the local device. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [getPairedDevices](arkts-connectivity-manager-getpaireddevices-f.md#getpaireddevices) | Obtains the devices paired with the current device. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [getState](arkts-connectivity-manager-getstate-f.md#getstate) | Queries the NearLink status. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [isFrameType4Supported](arkts-connectivity-manager-isframetype4supported-f.md#isframetype4supported) | Checks whether the current device supports radio frame type 4. |
| [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md#isnearlinksupported) | Checks whether the current device supports NearLink. |
| [offStateChange](arkts-connectivity-manager-offstatechange-f.md#offstatechange) | Unsubscribes from the NearLink status change event. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [onStateChange](arkts-connectivity-manager-onstatechange-f.md#onstatechange) | Subscribes to the NearLink status change event. This API uses an asynchronous callback to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [disable](arkts-connectivity-manager-disable-f-sys.md#disable) | Disables NearLink. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [enable](arkts-connectivity-manager-enable-f-sys.md#enable) | Enables NearLink. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [enableWithOptions](arkts-connectivity-manager-enablewithoptions-f-sys.md#enablewithoptions) | Enables NearLink with the specified options. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [factoryReset](arkts-connectivity-manager-factoryreset-f-sys.md#factoryreset) | Restores a device to its factory settings. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [getLocalAddress](arkts-connectivity-manager-getlocaladdress-f-sys.md#getlocaladdress) | Queries the MAC address of the local device. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
| [setConnectionMode](arkts-connectivity-manager-setconnectionmode-f-sys.md#setconnectionmode) | Sets the connection mode. This API uses a promise to return the result. Before calling this API, you may call [isNearLinkSupported](arkts-connectivity-manager-isnearlinksupported-f.md) to check whether the device supports NearLink. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [EnableOptions](arkts-connectivity-manager-enableoptions-i-sys.md) | The options for enabling NearLink. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [NearlinkState](arkts-connectivity-manager-nearlinkstate-e.md) | Enumerates the NearLink statuses. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AutoConnectPolicy](arkts-connectivity-manager-autoconnectpolicy-e-sys.md) | Enumerates the auto-connection policies when NearLink is enabled. |
| [ConnectionMode](arkts-connectivity-manager-connectionmode-e-sys.md) | Enumerates the connection modes. |
<!--DelEnd-->
