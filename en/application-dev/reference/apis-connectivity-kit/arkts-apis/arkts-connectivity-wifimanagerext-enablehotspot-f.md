# enableHotspot

## Modules to Import

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## enableHotspot

```TypeScript
function enableHotspot(): void
```

Enables the Wi-Fi hotspot.

> **NOTE:** 
> 
> This API is supported since API version 9 and deprecated since API version 10.

**Since:** 9

**Deprecated since:** 10

**Required permissions:** ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

<!--Device-wifiManagerExt-function enableHotspot(): void--><!--Device-wifiManagerExt-function enableHotspot(): void-End-->

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
      wifiManagerExt.enableHotspot();
  } catch (error) {
      console.error("failed: " + JSON.stringify(error));
  }
```
