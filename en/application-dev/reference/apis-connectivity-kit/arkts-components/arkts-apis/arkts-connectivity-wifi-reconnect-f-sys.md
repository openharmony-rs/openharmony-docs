# reconnect (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## reconnect

```TypeScript
function reconnect(): boolean
```

Re-connects to current network.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [reconnect](arkts-connectivity-wifimanager-reconnect-f-sys.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | `true` if the Wi-Fi network is re-connect successfully. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.reconnect();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
