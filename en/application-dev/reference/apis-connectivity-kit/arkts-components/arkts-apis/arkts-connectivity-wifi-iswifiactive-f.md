# isWifiActive

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## isWifiActive

```TypeScript
function isWifiActive(): boolean
```

Queries the Wi-Fi status

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the Wi-Fi is active, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let isWifiActive = wifi.isWifiActive();
  console.info("isWifiActive:" + isWifiActive);
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
