# setHotspotConfig (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## setHotspotConfig

```TypeScript
function setHotspotConfig(config: HotspotConfig): boolean
```

Sets the hotspot for a device.

<p>Only OPEN and WPA2 PSK hotspot can be configured.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [setHotspotConfig](arkts-connectivity-wifimanager-sethotspotconfig-f-sys.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [HotspotConfig](arkts-connectivity-wifi-hotspotconfig-i-sys.md) | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the method is called successfully, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let config:wifi.HotspotConfig = {
        ssid: "****",
        securityType: 3,
        band: 0,
        preSharedKey: "****",
        maxConn: 0
    }
    let ret = wifi.setHotspotConfig(config);
    console.info("result:" + ret);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
