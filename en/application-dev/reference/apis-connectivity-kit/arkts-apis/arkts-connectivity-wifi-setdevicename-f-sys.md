# setDeviceName (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## setDeviceName

```TypeScript
function setDeviceName(devName: string): boolean
```

Sets the name of the Wi-Fi P2P device.

**Since:** 8

**Deprecated since:** 9

**Substitutes:** setP2pDeviceName

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.P2P

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| devName | string | Yes | Indicates the name to be set. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the operation is successful, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let name = "****";
    wifi.setDeviceName(name);    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
