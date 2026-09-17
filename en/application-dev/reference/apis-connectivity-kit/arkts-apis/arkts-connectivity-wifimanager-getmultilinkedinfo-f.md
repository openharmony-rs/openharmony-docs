# getMultiLinkedInfo

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getMultiLinkedInfo

```TypeScript
function getMultiLinkedInfo(): Array<WifiLinkedInfo>
```

Obtain multiple Wi-Fi connection information when Wi-Fi linked in MLO(Muti-Link Operation) state. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid.

**Since:** 18

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md)&gt; | Returns Wi-Fi multiple link information. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta-disabled) | Wi-Fi STA disabled. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let linkedInfo = wifiManager.getMultiLinkedInfo();
    console.info("linkedInfo:" + JSON.stringify(linkedInfo));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
