# isConnected

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## isConnected

```TypeScript
function isConnected(): boolean
```

Checks whether a Wi-Fi connection has been set up.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [isConnected](arkts-connectivity-wifimanager-isconnected-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if a Wi-Fi connection has been set up, returns `false` otherwise. |
