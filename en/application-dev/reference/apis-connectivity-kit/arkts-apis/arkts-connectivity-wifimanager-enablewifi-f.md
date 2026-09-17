# enableWifi

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## enableWifi

```TypeScript
function enableWifi(): void
```

Enable Wi-Fi.

**Since:** 15

**Required permissions:** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION)

**System capability:** SystemCapability.Communication.WiFi.STA

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |
| [2501003](../errorcode-wifi.md#2501003-failed-to-open-the-service) | Operation failed because the service is being closed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  try {
    wifiManager.enableWifi();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
