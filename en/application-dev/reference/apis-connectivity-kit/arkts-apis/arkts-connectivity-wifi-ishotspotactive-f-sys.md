# isHotspotActive (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## isHotspotActive

```TypeScript
function isHotspotActive(): boolean
```

Checks whether Wi-Fi hotspot is active on a device.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isHotspotActive](arkts-connectivity-wifimanager-ishotspotactive-f-sys.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if Wi-Fi hotspot is enabled, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let ret = wifi.isHotspotActive();
    console.info("result:" + ret);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
