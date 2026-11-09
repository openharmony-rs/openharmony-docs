# getSupportedFeatures (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getSupportedFeatures

```TypeScript
function getSupportedFeatures(): number
```

Obtains the features supported by this device.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getSupportedFeatures(): long--><!--Device-wifiManager-function getSupportedFeatures(): long-End-->

**System capability:** SystemCapability.Communication.WiFi.Core

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| number | Feature value. Each bit represents a feature: <br>0x0001: WLAN infrastructure mode <br>0x0002: 5 GHz feature <br>0x0004: Generic Advertisement Service (GAS)/Access Network Query Protocol (ANQP) feature <br>0x0008: Wi-Fi Direct <br>0x0010: SoftAP <br>0x0040: Wi-Fi Aware <br>0x8000: WLAN AP/STA concurrency <br>0x8000000: WPA3 Personal (WPA-3 SAE) <br>0x10000000: WPA3-Enterprise Suite B <br>0x20000000: Enhanced open feature |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2401000](../errorcode-wifi.md#2401000-sta-internal-error) | Operation failed. |

<!--Del-->
**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
    let ret = wifiManager.getSupportedFeatures();
    console.info("supportedFeatures:" + ret);
} catch (error) {
    console.error("failed:" + JSON.stringify(error));
}
```

<!--DelEnd-->
