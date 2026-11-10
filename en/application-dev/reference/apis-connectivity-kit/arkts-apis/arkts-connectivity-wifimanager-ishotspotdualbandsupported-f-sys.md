# isHotspotDualBandSupported (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## isHotspotDualBandSupported

```TypeScript
function isHotspotDualBandSupported(): boolean
```

Checks whether the Wi-Fi hotspot function of the current device supports dual bands (both 2.4 GHz and 5 GHz).

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifiManager-function isHotspotDualBandSupported(): boolean--><!--Device-wifiManager-function isHotspotDualBandSupported(): boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether the hotspot supports dual bands. The value **true** indicates dual bands are supported, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2601000](../errorcode-wifi.md#2601000-hotspot-module-error) | Operation failed. |

<!--Del-->
**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let ret = wifiManager.isHotspotDualBandSupported();
  console.info("result:" + ret);    
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

<!--DelEnd-->
