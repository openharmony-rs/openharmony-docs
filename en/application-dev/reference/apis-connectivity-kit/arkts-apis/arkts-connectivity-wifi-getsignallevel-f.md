# getSignalLevel

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getSignalLevel

```TypeScript
function getSignalLevel(rssi: number, band: number): number
```

Calculates the Wi-Fi signal level based on the Wi-Fi RSSI and frequency band.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| rssi | number | Yes | Indicates the Wi-Fi RSSI. |
| band | number | Yes | Indicates the Wi-Fi frequency band. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns Wi-Fi signal level ranging from 0 to 4. |

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
