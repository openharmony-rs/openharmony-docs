# disconnect

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## disconnect

```TypeScript
function disconnect(): void
```

Disconnect connection between sta and Wi-Fi hotspot.

**Since:** 15

**Required permissions:** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION)

**System capability:** SystemCapability.Communication.WiFi.STA

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
    wifiManager.disconnect();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
