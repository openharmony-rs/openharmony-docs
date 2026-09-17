# startDiscoverDevices

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## startDiscoverDevices

```TypeScript
function startDiscoverDevices(): boolean
```

Discover Wi-Fi P2P devices.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** startDiscoverP2pDevices

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.startDiscoverDevices();  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
