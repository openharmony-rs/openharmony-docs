# startScan

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## startScan

```TypeScript
function startScan(): void
```

Scan Wi-Fi hotspot.

**Since:** 21

**Required permissions:** ohos.permission.SET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.startScan();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
