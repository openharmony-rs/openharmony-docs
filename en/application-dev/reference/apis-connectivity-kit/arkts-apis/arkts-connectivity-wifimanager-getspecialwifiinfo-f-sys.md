# getSpecialWifiInfo (System API)

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getSpecialWifiInfo

```TypeScript
function getSpecialWifiInfo(): SpecialWifiInfo
```

Get special Wi-Fi info

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function getSpecialWifiInfo(): SpecialWifiInfo--><!--Device-wifiManager-function getSpecialWifiInfo(): SpecialWifiInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| [SpecialWifiInfo](arkts-connectivity-wifimanager-specialwifiinfo-i-sys.md) | Returns the special Wi-Fi info. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [202](../../errorcode-universal.md#202-permission-verification-failed-for-calling-a-system-api) | Permission verification failed. A non-system application calls a system API. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | The Wi-Fi service is not started properly, or there is an Wi-Fi service error. |
