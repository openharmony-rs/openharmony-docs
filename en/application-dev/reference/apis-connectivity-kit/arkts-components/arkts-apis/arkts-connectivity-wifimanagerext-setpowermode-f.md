# setPowerMode

## Modules to Import

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## setPowerMode

```TypeScript
function setPowerMode(mode: PowerMode): void
```

Set the current Wi-Fi power mode.

**Since:** 9

**Deprecated since:** 10

**Required permissions:** ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

**System capability:** SystemCapability.Communication.WiFi.AP.Extension

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| mode | [PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md) | Yes |  |

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
      let model = 0;
      wifiManagerExt.setPowerMode(model);
  }catch(error){
      console.error("failed: " + JSON.stringify(error));
  }
```
