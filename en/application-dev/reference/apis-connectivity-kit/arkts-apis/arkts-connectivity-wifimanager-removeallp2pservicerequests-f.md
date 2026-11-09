# removeAllP2pServiceRequests

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## removeAllP2pServiceRequests

```TypeScript
function removeAllP2pServiceRequests(): void
```

Removes all pending service discovery requests.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function removeAllP2pServiceRequests(): void--><!--Device-wifiManager-function removeAllP2pServiceRequests(): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |
