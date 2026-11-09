# addUpnpLocalP2pService

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addUpnpLocalP2pService

```TypeScript
function addUpnpLocalP2pService(uuid: string, device: string,
    services: Array<string>, serviceName: string): void
```

Adds and registers the local P2P service description of the UPnP (Universal Plug and Play) service to be discovered by the peer device.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function addUpnpLocalP2pService(uuid: string, device: string,    services: Array<string>, serviceName: string): void--><!--Device-wifiManager-function addUpnpLocalP2pService(uuid: string, device: string,    services: Array<string>, serviceName: string): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | string | Yes | UUID, which is in the form of a string. For details about the format, see [RFC 4122](http://www.ietf.org/rfc/rfc4122.txt). The value has a fixed length of 36 characters and cannot contain spaces, for example, **6859dede-8574-59ab-9332-123456789012**. |
| device | string | Yes | UPnP device type, which is in the form of a string. For details about the format, see [UPnP Device Architecture 1.1](http://www.upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf). The length depends on the protocol definition and cannot contain spaces. The length is generally dozens of characters, and it is recommended to keep it within 255 bytes, for example, **urn:schemas-upnp-org:device:MediaServer:1**. |
| services | Array&lt;string&gt; | Yes | Array of UPnP service types, which is in the form of a string. For details about the format, see [UPnP Device Architecture 1.1](http://www.upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf). The length of each element in the array must not exceed 512 bytes, and the array should not contain too many elements. An example of this parameter is **urn:schemas-upnp-org:service:ContentDirectory:1**. |
| serviceName | string | Yes | Service name used to identify the local service object. The value contains a maximum of 63 characters. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p-module-error) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p-module-error) | Wi-Fi STA disabled. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let uuid = "6859dede-8574-59ab-9332-123456789012";
  let device = "urn:schemas-upnp-org:device:MediaServer:1";
  let services = ["urn:schemas-upnp-org:service:ContentDirectory:1"];
  wifiManager.addUpnpLocalP2pService(uuid, device, services, "serviceName");
} catch (error) {
  console.error("failed: " + JSON.stringify(error));
}
```
