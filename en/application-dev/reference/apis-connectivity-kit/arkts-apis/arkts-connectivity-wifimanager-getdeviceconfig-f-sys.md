# getDeviceConfig (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getDeviceConfig

```TypeScript
function getDeviceConfig(networkId: number): WifiDeviceConfig
```

Obtain the single Wi-Fi configuration with Network ID.

**Since:** 24

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| networkId | number | Yes | The network ID of the Wi-Fi configuration to retrieve. |

**Return value:**

| Type | Description |
| --- | --- |
| [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | Returns the Wi-Fi configuration corresponding to the network ID. |

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
    let networkId = 0;
    let config = wifiManager.getDeviceConfig(networkId);
    console.info(`config: ${JSON.stringify(config)}`);    
  }catch(error){
    console.error(`failed: ${JSON.stringify(error)}`);
  }
```
