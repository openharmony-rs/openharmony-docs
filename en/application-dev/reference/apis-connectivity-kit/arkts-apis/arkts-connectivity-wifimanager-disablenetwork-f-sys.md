# disableNetwork (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## disableNetwork

```TypeScript
function disableNetwork(netId: number): void
```

Disable the specified DeviceConfig by networkId. The disabled DeviceConfig will not be associated with again.

**Since:** 9

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netId | number | Yes | Identifies the network to disable. The value of networkId cannot be less than 0. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. 3.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta-disabled) | Wi-Fi STA disabled. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let netId = 0;
  wifiManager.disableNetwork(netId);  
} catch (error) {
  console.error(`failed: ${JSON.stringify(error)}`);
}
```

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let netId = 0;
    let blockDuration = 300;
    wifiManager.disableNetwork(netId, blockDuration);
  } catch (error) {
    console.error(`failed: ${JSON.stringify(error)}`);
  }
```


## disableNetwork

```TypeScript
function disableNetwork(netId: number, blockDuration: number): void
```

Disable the specified DeviceConfig by networkId for a period of time. The disabled DeviceConfig will not be associated with again.

**Since:** 23

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| netId | number | Yes | Identifies the network to disable. The value of networkId cannot be less than 0. |
| blockDuration | number | Yes | Indicates the duration of network disablement(unit is secondes), If the value is -1, means permanent disablement. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta-disabled) | Wi-Fi STA disabled. |

**Examples**

See [disableNetwork](#disablenetwork)
