# disableWifi (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## disableWifi

```TypeScript
function disableWifi(): boolean
```

Disables Wi-Fi.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [disableWifi](arkts-connectivity-wifimanager-disablewifi-f.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.disableWifi();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
