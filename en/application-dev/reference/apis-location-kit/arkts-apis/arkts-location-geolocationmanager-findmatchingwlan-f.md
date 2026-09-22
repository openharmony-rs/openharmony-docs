# findMatchingWlan

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## findMatchingWlan

```TypeScript
function findMatchingWlan(
      wlanBssidArray: Array<string>, rssiThreshold: number, needStartScan: boolean): Promise<Array<MatchingWlanInfo>>
```

Check whether the WLAN scan results match the WLAN BSSID list, return information about the WLAN device that is successfully matched.

**Since:** 26.0.0

**Required permissions:** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**Model restriction:** This API can be used only in the stage model.

**Atomic service API:** This API can be used in atomic services since API version 26.0.0.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wlanBssidArray | Array&lt;string&gt; | Yes | Indicates the list of WLAN BSSIDs that need to be matched. |
| rssiThreshold | number | Yes | Indicates the WLAN RSSI threshold, only matches WLAN BSSIDs with RSSI greater than this threshold. |
| needStartScan | boolean | Yes | Indicates whether a WLAN scan needs to be initiated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[MatchingWlanInfo](arkts-location-geolocationmanager-matchingwlaninfo-i.md)&gt;&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call ${geoLocationManager.findMatchingWlan} due to limited device capabilities. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301800](../errorcode-geoLocationManager.md#3301800-failed-to-start-wi-fi-or-bluetooth-scanning) | Failed to start WLAN scanning. |
