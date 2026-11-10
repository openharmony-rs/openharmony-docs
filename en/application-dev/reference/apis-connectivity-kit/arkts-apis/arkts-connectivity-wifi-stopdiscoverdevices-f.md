# stopDiscoverDevices

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## stopDiscoverDevices

```TypeScript
function stopDiscoverDevices(): boolean
```

Stops discovering devices.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** stopDiscoverP2pDevices

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function stopDiscoverDevices(): boolean--><!--Device-wifi-function stopDiscoverDevices(): boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the device discovery is stopped successfully. **true** if the operation is successful; **false** otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.stopDiscoverDevices();  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
