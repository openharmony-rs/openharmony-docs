# deletePersistentGroup (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## deletePersistentGroup

```TypeScript
function deletePersistentGroup(netId: number): boolean
```

Deletes the persistent P2P group with the specified network ID.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** deletePersistentP2pGroup

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.P2P

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netId | number | Yes |  |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let netId = 0;
    wifi.deletePersistentGroup(netId);    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
