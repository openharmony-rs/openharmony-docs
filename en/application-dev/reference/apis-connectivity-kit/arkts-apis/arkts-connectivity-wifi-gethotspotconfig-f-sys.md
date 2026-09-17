# getHotspotConfig (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getHotspotConfig

```TypeScript
function getHotspotConfig(): HotspotConfig
```

Obtains the Wi-Fi hotspot configuration.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getHotspotConfig](arkts-connectivity-wifimanager-gethotspotconfig-f-sys.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [HotspotConfig](arkts-connectivity-wifi-hotspotconfig-i-sys.md) | Returns the configuration of an existing or enabled Wi-Fi hotspot. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let config = wifi.getHotspotConfig();
    console.info("result:" + JSON.stringify(config));        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
