# disableHotspot

## Modules to Import

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## disableHotspot

```TypeScript
function disableHotspot(): void
```

Disable Wi-Fi hotspot function. If Wi-Fi is enabled after the Wi-Fi hotspot is disabled, Wi-Fi may be re-enabled.

**Since:** 9

**Deprecated since:** 10

**Required permissions:** ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap-extension-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';

  try {
      wifiManagerExt.disableHotspot();
  }catch(error){
      console.error("failed: " + JSON.stringify(error));
  }
```
