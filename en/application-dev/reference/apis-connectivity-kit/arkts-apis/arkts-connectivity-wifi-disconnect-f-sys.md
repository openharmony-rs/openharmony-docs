# disconnect (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## disconnect

```TypeScript
function disconnect(): boolean
```

Disconnect Wi-Fi network.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [disconnect](arkts-connectivity-wifimanager-disconnect-f.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` for disconnecting network success, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.disconnect();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
