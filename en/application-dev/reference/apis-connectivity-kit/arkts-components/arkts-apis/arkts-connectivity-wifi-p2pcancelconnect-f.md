# p2pCancelConnect

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## p2pCancelConnect

```TypeScript
function p2pCancelConnect(): boolean
```

Canceling a P2P connection.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** [p2pCancelConnect](arkts-connectivity-wifimanager-p2pcancelconnect-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.p2pCancelConnect();  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
