# getCountryCode

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getCountryCode

```TypeScript
function getCountryCode(): string
```

Obtain the country code of the device.

**Since:** 9

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.Core

**Return value:**

| Type | Description |
| --- | --- |
| string | Returns the country code of this device. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2401000](../errorcode-wifi.md#2401000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let code = wifiManager.getCountryCode();
    console.info("code:" + code);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
