# reassociate (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## reassociate

```TypeScript
function reassociate(): boolean
```

Re-associate to current network.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [reassociate](arkts-connectivity-wifimanager-reassociate-f-sys.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | `true` if the Wi-Fi network is re-associate successfully. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.reassociate();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
