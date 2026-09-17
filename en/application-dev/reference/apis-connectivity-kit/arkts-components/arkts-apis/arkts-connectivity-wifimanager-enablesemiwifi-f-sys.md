# enableSemiWifi (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## enableSemiWifi

```TypeScript
function enableSemiWifi(): void
```

Enable semi - Wifi.

**Since:** 12

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |
| [2501004](../errorcode-wifi.md#2501004-failed-to-close-the-service) | Operation failed because the service is being opened. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.enableSemiWifi();
  } catch(error) {
    console.error("failed:" + JSON.stringify(error));
  }
```
