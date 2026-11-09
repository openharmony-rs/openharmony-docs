# setScanAlwaysAllowed (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## setScanAlwaysAllowed

```TypeScript
function setScanAlwaysAllowed(isScanAlwaysAllowed: boolean): void
```

Sets whether scan is always allowed.

- This interface controls whether the device can support hotspot scanning when Wi-Fi is disabled.  
- After this function is enabled, the system can still scan for nearby Wi-Fi hotspots even if Wi-Fi is disabled.  
- This function is mainly used in network discovery and location locating scenarios.

**Since:** 10

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

<!--Device-wifiManager-function setScanAlwaysAllowed(isScanAlwaysAllowed: boolean): void--><!--Device-wifiManager-function setScanAlwaysAllowed(isScanAlwaysAllowed: boolean): void-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isScanAlwaysAllowed | boolean | Yes | Whether scan is always allowed. The value **true** indicates that scan is always allowed, and the value **false** indicates the opposite. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | System API is not allowed called by Non-system application. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Invalid parameters. Possible causes: 1. Mandatory parameters are left unspecified. 2. Incorrect parameter types. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |
