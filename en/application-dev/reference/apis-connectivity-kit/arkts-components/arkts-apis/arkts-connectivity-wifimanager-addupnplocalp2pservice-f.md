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

Add a UPnP local P2P service description and register it.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| uuid | string | Yes | A string representation of this UUID in the following format. as per &lt;a href="http://www.ietf.org/rfc/rfc4122.txt"&gt;RFC 4122&lt;/a&gt;.<br> The standard fixed length is 36 characters, and spaces are not allowed. for example, "6859dede-8574-59ab-9332-123456789012" |
| device | string | Yes | UPnP device type, a string representation of this device in the following format, as per &lt;a href="http://www.upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf"&gt;. UPnP Device Architecture 1.1&lt;/a&gt;<br> The length depends on the standard definition, and spaces are not allowed. It is usually tens of characters, and it is recommended to keep it within 255 characters. for example, "urn:schemas-upnp-org:device:MediaServer:1" |
| services | Array&lt;string&gt; | Yes | UPnP service type list, a string representation of this service in the following format, as per &lt;a href="http://www.upnp.org/specs/arch/UPnP-arch-DeviceArchitecture-v1.1.pdf"&gt;. UPnP Device Architecture 1.1&lt;/a&gt;<br> The length of each service must not exceed 512 bytes. It is recommended that the Array contain no more. for example, ["urn:schemas-upnp-org:service:ContentDirectory:1"] |
| serviceName | string | Yes | Service name used to identify the local service object. |

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

try {
  let uuid = "6859dede-8574-59ab-9332-123456789012";
  let device = "urn:schemas-upnp-org:device:MediaServer:1";
  let services = ["urn:schemas-upnp-org:service:ContentDirectory:1"];
  wifiManager.addUpnpLocalP2pService(uuid, device, services, "serviceName");
} catch (error) {
  console.error("failed: " + JSON.stringify(error));
}
```
