# enableHiLinkHandshake (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## enableHiLinkHandshake

```TypeScript
function enableHiLinkHandshake(isHiLinkEnable: boolean, bssid: string, config: WifiDeviceConfig): void
```

Enable hiLink handshake.

**Since:** 12

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| isHiLinkEnable | boolean | Yes | Indicates the HiLink enable or not. |
| bssid | string | Yes | Indicates the Wi-Fi bssid. |
| config | [WifiDeviceConfig](arkts-connectivity-wifimanager-wifideviceconfig-i.md) | Yes | Indicates the Wi-Fi device config. |

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
// You can obtain config data by using getScanInfoList, which can be used only when WifiScanInfo.isHiLinkNetwork is true.
let config:wifiManager.WifiDeviceConfig = {
  ssid : "****",
  preSharedKey : "****",
  securityType : 0,
  bssid : "38:37:8b:80:bf:cc",
  bssidType : 1,
  isHiddenSsid : false
}  
try {
  wifiManager.enableHiLinkHandshake(true, config.bssid, config);
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
