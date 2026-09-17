# isHotspotDualBandSupported (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## isHotspotDualBandSupported

```TypeScript
function isHotspotDualBandSupported(): boolean
```

Checks whether a device serving as a Wi-Fi hotspot supports both the 2.4 GHz and 5 GHz Wi-Fi.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isHotspotDualBandSupported](arkts-connectivity-wifimanager-ishotspotdualbandsupported-f-sys.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the method is called successfully, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let ret = wifi.isHotspotDualBandSupported();
    console.info("result:" + ret);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
