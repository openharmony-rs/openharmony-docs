# getP2pServiceRequest

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getP2pServiceRequest

```TypeScript
function getP2pServiceRequest(): Promise<Array<WifiP2pServiceRequest>>
```

Queries the pending P2P service discovery requests. This API uses a promise to return the result.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function getP2pServiceRequest(): Promise<Array<WifiP2pServiceRequest>>--><!--Device-wifiManager-function getP2pServiceRequest(): Promise<Array<WifiP2pServiceRequest>>-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WifiP2pServiceRequest](arkts-connectivity-wifimanager-wifip2pservicerequest-i.md)&gt;&gt; | Promise used to return the pending service discovery request list. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |
