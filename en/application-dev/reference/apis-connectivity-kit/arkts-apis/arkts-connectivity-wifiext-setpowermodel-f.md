# setPowerModel

## Modules to Import

```TypeScript
import { wifiext } from '@kit.ConnectivityKit';
```

## setPowerModel

```TypeScript
function setPowerModel(model: PowerModel): boolean
```

Sets the power model.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [setPowerMode](arkts-connectivity-wifimanagerext-setpowermode-f.md)

**Required permissions:** ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

<!--Device-wifiext-function setPowerModel(model: PowerModel): boolean--><!--Device-wifiext-function setPowerModel(model: PowerModel): boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| model | [PowerModel](arkts-connectivity-wifiext-powermodel-e.md) | Yes | Power model to set. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns **true** if the operation is successful; returns **false** otherwise. |
