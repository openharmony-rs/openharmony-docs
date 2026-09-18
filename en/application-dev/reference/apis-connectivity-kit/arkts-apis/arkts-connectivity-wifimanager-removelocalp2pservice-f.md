# removeLocalP2pService

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## removeLocalP2pService

```TypeScript
function removeLocalP2pService(srvInfo: WifiP2pServiceInfo): void
```

Remove a registered local P2P service added with the [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md) or [addUpnpLocalP2pService](arkts-connectivity-wifimanager-addupnplocalp2pservice-f.md).

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| srvInfo | [WifiP2pServiceInfo](arkts-connectivity-wifimanager-wifip2pserviceinfo-i.md) | Yes | Service description consistent with the registered one. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | The Wi-Fi service is not started properly, or there is an Wi-Fi service error. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { BusinessError } from '@kit.BasicServicesKit';

  wifiManager.getLocalP2pServices().then((data: wifiManager.WifiP2pServiceInfo[]) => {
    data.forEach((item: wifiManager.WifiP2pServiceInfo) => {
      if (item.serviceName === "serviceName") {
        wifiManager.removeLocalP2pService(item);
      }
    });
  }).catch((error: BusinessError) => {
    console.error("failed: " + JSON.stringify(error));
  });
```
