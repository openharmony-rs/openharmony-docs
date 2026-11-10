# addDnsSdServiceRequest

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addDnsSdServiceRequest

```TypeScript
function addDnsSdServiceRequest(serviceType?: string, instanceName?: string): void
```

Adds a DNS-SD service discovery request that matches DNS-SD services.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function addDnsSdServiceRequest(serviceType?: string, instanceName?: string): void--><!--Device-wifiManager-function addDnsSdServiceRequest(serviceType?: string, instanceName?: string): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| serviceType | string | No | Service type, which is used for peer service discovery. The recommended format is "_<ServiceName>._<Protocol>", for example, "_http._tcp". Corresponds to the serviceType input parameter in [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md). If this parameter is not specified, it defaults to an empty string, which matches all service types. |
| instanceName | string | No | Instance name, used to discover the peer service. Corresponds to the instanceName input parameter in [addDnsSdLocalP2pService](arkts-connectivity-wifimanager-adddnssdlocalp2pservice-f.md). If this parameter is not specified, it defaults to an empty string. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |
