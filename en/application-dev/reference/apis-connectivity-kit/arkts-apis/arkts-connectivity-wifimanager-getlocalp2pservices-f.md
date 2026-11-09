# getLocalP2pServices

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getLocalP2pServices

```TypeScript
function getLocalP2pServices(): Promise<Array<WifiP2pServiceInfo>>
```

Queries the local P2P services. This API uses a promise to return the result.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function getLocalP2pServices(): Promise<Array<WifiP2pServiceInfo>>--><!--Device-wifiManager-function getLocalP2pServices(): Promise<Array<WifiP2pServiceInfo>>-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;Array&lt;[WifiP2pServiceInfo](arkts-connectivity-wifimanager-wifip2pserviceinfo-i.md)&gt;&gt; | Promise used to return the array of registered local P2P services. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

wifiManager.getLocalP2pServices().then((data: wifiManager.WifiP2pServiceInfo[]) => {
  console.info("get local P2P services: " + JSON.stringify(data));
}).catch((error: BusinessError) => {
  console.error("failed: " + JSON.stringify(error));
});
```
