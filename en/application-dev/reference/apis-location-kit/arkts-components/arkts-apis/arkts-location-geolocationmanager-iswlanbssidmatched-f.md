# isWlanBssidMatched

## Modules to Import

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';
```

## isWlanBssidMatched

```TypeScript
function isWlanBssidMatched(
      wlanBssidArray: Array<string>, rssiThreshold: number, needStartScan: boolean): Promise<boolean>
```

Check whether the WLAN scan results match the WLAN BSSID list.

**Since:** 21

**Required permissions:** ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**Atomic service API:** This API can be used in atomic services since API version 21.

**System capability:** SystemCapability.Location.Location.Core

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| wlanBssidArray | Array&lt;string&gt; | Yes | Indicates the list of WLAN BSSIDs that need to be matched. |
| rssiThreshold | number | Yes | Indicates the WLAN RSSI threshold, only matching WLAN BSSID with RSSI greater than this threshold. |
| needStartScan | boolean | Yes | Indicate whether a WLAN scan needs to be initiated. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | The promise returned by the function. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. Failed to call &#36;{geoLocationManager.isWlanBssidMatched} due to limited device capabilities. |
| [3301100](../errorcode-geoLocationManager.md#3301100-positioning-failed-because-the-location-switch-is-turned-off) | The location switch is off. |
| [3301800](../errorcode-geoLocationManager.md#3301800-failed-to-start-wi-fi-or-bluetooth-scanning) | Failed to start WiFi scanning. |

**Examples**

```TypeScript
import { geoLocationManager } from '@kit.LocationKit';

try {
  let wlanBssidArray: Array<string> = ["02:1b:32:23:ea:91", "02:1b:32:23:ea:93"];
  let rssiThreshold: number = -70;
  let needStartScan: boolean = true;
  geoLocationManager.isWlanBssidMatched(wlanBssidArray, rssiThreshold, needStartScan).then((res) => {
    console.info("Wlan Bssid Matched Result:" + res);
  })
} catch (error) {
  console.error("isWlanBssidMatched: errCode" + error.code + ", errMessage" + error.message);
}
```
