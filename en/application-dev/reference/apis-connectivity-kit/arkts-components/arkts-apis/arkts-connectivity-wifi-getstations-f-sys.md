# getStations (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getStations

```TypeScript
function getStations(): Array<StationInfo>
```

Obtains the list of clients that are connected to a Wi-Fi hotspot.

<p>This method can only be used on a device that serves as a Wi-Fi hotspot.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** getHotspotStations

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.MANAGE_WIFI_HOTSPOT

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[StationInfo](arkts-connectivity-wifi-stationinfo-i-sys.md)&gt; | Returns the list of clients that are connected to the Wi-Fi hotspot. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let stations = wifi.getStations();
    console.info("result:" + JSON.stringify(stations));        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
