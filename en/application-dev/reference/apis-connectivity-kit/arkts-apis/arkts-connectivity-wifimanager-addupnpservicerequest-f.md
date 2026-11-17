# addUpnpServiceRequest

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addUpnpServiceRequest

```TypeScript
function addUpnpServiceRequest(searchTarget?: string): void
```

Adds a UPnP service discovery request that matches the specified search target.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function addUpnpServiceRequest(searchTarget?: string): void--><!--Device-wifiManager-function addUpnpServiceRequest(searchTarget?: string): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| searchTarget | string | No | UPnP search target. If this parameter is not specified, it defaults to an empty string.<br> Examples of input parameter types: <br> <ul> <li>Search all UPnP devices and services: "ssdp:all"<li>Search specific root devices: "upnp:rootdevice"<li>Search specific device types (urn:schemas-upnp-org:device:...): <br> for example "urn:schemas-upnp-org:device:MediaServer:2"<li>Search specific service types (urn:schemas-upnp-org:service:...): <br> for example "urn:schemas-upnp-org:service:ContentDirectory:2"<li>Search specific UUID: for example: "uuid:6859dede-8574-59ab-9332-123456789012"</ul> |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |
