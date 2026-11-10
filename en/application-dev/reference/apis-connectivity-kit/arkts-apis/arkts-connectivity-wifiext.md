# @ohos.wifiext(WLAN Extension)

This module provides Wi-Fi extension APIs for non-universal products.

> **NOTE:** 
> 
> The APIs provided by this module are no longer maintained since API version 9. You are advised to use
> [@ohos.wifiManagerExt (WLAN Extension)](arkts-connectivity-wifimanagerext.md).

**Since:** 8

<!--Device-unnamed-declare namespace wifiext--><!--Device-unnamed-declare namespace wifiext-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

## Modules to Import

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [disableHotspot](arkts-connectivity-wifiext-disablehotspot-f.md#disablehotspot-1) | Disables the Wi-Fi hotspot. |
| [enableHotspot](arkts-connectivity-wifiext-enablehotspot-f.md#enablehotspot-1) | Enables the Wi-Fi hotspot. |
| [getPowerModel](arkts-connectivity-wifiext-getpowermodel-f.md#getpowermodel-1) | Obtains the current power model. This API uses a promise to return the result. |
| [getPowerModel](arkts-connectivity-wifiext-getpowermodel-f.md#getpowermodel-2) | Obtains the current power model. This API uses an asynchronous callback to return the result. |
| [getSupportedPowerModel](arkts-connectivity-wifiext-getsupportedpowermodel-f.md#getsupportedpowermodel-1) | Obtains the supported power models. This API uses a promise to return the result. |
| [getSupportedPowerModel](arkts-connectivity-wifiext-getsupportedpowermodel-f.md#getsupportedpowermodel-2) | Obtains the supported power models. This API uses an asynchronous callback to return the result. |
| [setPowerModel](arkts-connectivity-wifiext-setpowermodel-f.md#setpowermodel-1) | Sets the power model. |

### Enums

| Name | Description |
| --- | --- |
| [PowerModel](arkts-connectivity-wifiext-powermodel-e.md) | Enumerates the power models. |
