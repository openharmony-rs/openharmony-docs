# addDnsSdLocalP2pService

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## addDnsSdLocalP2pService

```TypeScript
function addDnsSdLocalP2pService(instanceName: string, serviceType: string,
    txtRecord: Map<string, string>, serviceName: string): void
```

Adds and registers the local P2P service description of DNS-SD (DNS service discovery) to be discovered by the peer device.

**Since:** 26.0.1

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

<!--Device-wifiManager-function addDnsSdLocalP2pService(instanceName: string, serviceType: string,    txtRecord: Map<string, string>, serviceName: string): void--><!--Device-wifiManager-function addDnsSdLocalP2pService(instanceName: string, serviceType: string,    txtRecord: Map<string, string>, serviceName: string): void-End-->

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceName | string | Yes | Instance name, which is used for service discovery by the peer device. The value contains a maximum of 63 characters. |
| serviceType | string | Yes | Service type, which is used for service discovery by the peer device. The value contains a maximum of 63 characters. It cannot be an empty string and can be customized. The recommended format is _<ServiceName>._<Protocol>, for example, **_http._tcp**. |
| txtRecord | Map&lt;string, string&gt; | Yes | TXT record containing key-value pairs. A key cannot contain equal signs (=). The length of a single record equals to **key.length** + **value.length**, which must be less than 255 bytes. It is recommended that the total length of all serialized keys and values be 200 to 400 bytes. If the length exceeds the limit of a single mDNS packet, the data may fail to be broadcast correctly or be ignored by the peer device. There is no limit on the number of key-value pairs. For the format, see [draft-cheshire-dnsext-dns-sd-11.txt](http://files.dns-sd.org/draft-cheshire-dnsext-dns-sd.txt). |
| serviceName | string | Yes | Service name, which is used to identify the local service object. The value contains a maximum of 63 characters. |

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
  let txtRecord: Map<string, string> = new Map();
  txtRecord.set("name", "xxx");
  wifiManager.addDnsSdLocalP2pService("instanceName", "_http._tcp", txtRecord, "serviceName");
} catch (error) {
  console.error("failed: " + JSON.stringify(error));
}
```
