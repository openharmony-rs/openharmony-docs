# connectToNetwork (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## connectToNetwork

```TypeScript
function connectToNetwork(networkId: number): boolean
```

Connects to Wi-Fi network.

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [connectToNetwork](arkts-connectivity-wifimanager-connecttonetwork-f.md)

**Required permissions:** ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | number | Yes | ID of the connected network. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the network connection is successful, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let networkId = 0;
    wifi.connectToNetwork(networkId);
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
