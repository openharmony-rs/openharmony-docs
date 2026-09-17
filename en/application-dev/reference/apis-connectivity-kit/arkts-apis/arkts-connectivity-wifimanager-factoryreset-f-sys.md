# factoryReset (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## factoryReset

```TypeScript
function factoryReset(): void
```

Reset all saved device configure.

**Since:** 11

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  wifiManager.factoryReset();
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
