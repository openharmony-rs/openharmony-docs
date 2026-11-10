# removeP2pServiceRequest

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## removeP2pServiceRequest

```TypeScript
function removeP2pServiceRequest(request: WifiP2pServiceRequest): void
```

Removes a specified service discovery request. You can obtain the list of registered service discovery requests by calling [getP2pServiceRequest](arkts-connectivity-wifimanager-getp2pservicerequest-f.md).

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function removeP2pServiceRequest(request: WifiP2pServiceRequest): void--><!--Device-wifiManager-function removeP2pServiceRequest(request: WifiP2pServiceRequest): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| request | [WifiP2pServiceRequest](arkts-connectivity-wifimanager-wifip2pservicerequest-i.md) | Yes | Service discovery request to remove. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |
