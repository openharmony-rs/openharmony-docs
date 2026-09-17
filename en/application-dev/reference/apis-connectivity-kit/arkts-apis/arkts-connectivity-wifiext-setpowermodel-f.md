# setPowerModel

## Modules to Import

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## setPowerModel

```TypeScript
function setPowerModel(model: PowerModel): boolean
```

Set the current Wi-Fi power mode.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setPowerMode](arkts-connectivity-wifimanagerext-setpowermode-f.md)

**Required permissions:** ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| model | [PowerModel](arkts-connectivity-wifiext-powermodel-e.md) | Yes | model indicates model file description to be loaded. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the Wi-Fi is active; returns `false` otherwise. |
