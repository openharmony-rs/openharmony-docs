# scan

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## scan

```TypeScript
function scan(): boolean
```

Scans Wi-Fi hotspot.

<p>This API works in asynchronous mode.</p>

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [scan](arkts-connectivity-wifimanager-scan-f.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.LOCATION

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the accessibility is succeed; returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.scan();
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
