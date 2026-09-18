# removeDevice (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## removeDevice

```TypeScript
function removeDevice(id: number): boolean
```

Deletes a Wi-Fi network with a specified ID.

<p>After a Wi-Fi network is deleted, its configuration will be deleted from the list of Wi-Fi configurations. If the Wi-Fi network is being connected, the connection will be interrupted. The application can only delete Wi-Fi networks it has created.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** removeDeviceConfig

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| id | number | Yes | Indicates the ID of the Wi-Fi network, which can be obtained using the addDeviceConfig or getLinkedInfo method. |

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Returns `true` if the Wi-Fi network is deleted successfully, returns `false` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let id = 0;
    wifi.removeDevice(id);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
