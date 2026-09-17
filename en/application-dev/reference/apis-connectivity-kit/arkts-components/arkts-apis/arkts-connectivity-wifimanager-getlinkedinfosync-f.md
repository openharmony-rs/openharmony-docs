# getLinkedInfoSync

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getLinkedInfoSync

```TypeScript
function getLinkedInfoSync(): WifiLinkedInfo
```

Obtain connection information about the Wi-Fi connection.this apireturns the result syncchronously. If does't have the permission of ohos.permission.GET_WIFI_PEERS_MAC, return random bssid.

**Since:** 18

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| [WifiLinkedInfo](arkts-connectivity-wifimanager-wifilinkedinfo-i.md) | Returns Wi-Fi linked information. |

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
    let linkInfo = wifiManager.getLinkedInfoSync();
    console.info("get linked info:" + JSON.stringify(linkInfo));
  } catch(error) {
    console.error("get linked info failed:" + JSON.stringify(error));
  }
```
