# getSignalLevel

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getSignalLevel

```TypeScript
function getSignalLevel(rssi: number, band: number): number
```

Calculates the Wi-Fi signal level based on the RSSI and frequency band.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getSignalLevel(rssi: number, band: number): number--><!--Device-wifi-function getSignalLevel(rssi: number, band: number): number-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rssi | number | Yes | RSSI of the hotspot, in dBm. |
| band | number | Yes | Frequency band of the Wi-Fi access point. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Signal level obtained. The value range is [0, 4]. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let rssi = 0;
  let band = 0;
  let level = wifi.getSignalLevel(rssi, band);
  console.info("level:" + JSON.stringify(level));
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
