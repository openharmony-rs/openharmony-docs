# isOpenSoftApAllowed (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## isOpenSoftApAllowed

```TypeScript
function isOpenSoftApAllowed(): boolean
```

Checks whether Wi-Fi hotspot operations are allowed under certain circumstances. When Airplane mode is enabled, if the system does not support the coexistence of SoftAP and STA or signal bridging, the hotspot switch cannot be operated.

**Since:** 18

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifiManager-function isOpenSoftApAllowed(): boolean--><!--Device-wifiManager-function isOpenSoftApAllowed(): boolean-End-->

**System capability:** SystemCapability.Communication.WiFi.AP.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| boolean | Whether Wi-Fi hotspot operations are allowed. The value **true** indicates Wi-Fi hotspot operations are allowed, and the value **false** indicates the opposite. |

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
  let ret = wifiManager.isOpenSoftApAllowed();
  console.info("result:" + ret);
}catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

<!--DelEnd-->
