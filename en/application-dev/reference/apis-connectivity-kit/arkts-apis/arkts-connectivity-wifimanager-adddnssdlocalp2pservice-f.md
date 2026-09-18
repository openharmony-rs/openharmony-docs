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

Add a Bonjour (DNS-SD) local P2P service description and register it.

**Since:** 26.1.0

**Required permissions:** ohos.permission.GET_WIFI_INFO_INTERNAL

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.WiFi.P2P

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| instanceName | string | Yes | Instance name, which is used for peer service discovery.<br>The maximum length is 63. |
| serviceType | string | Yes | Service type, which is used for peer service discovery. This parameter cannot be left blank. The value can be customized. The recommended format is "_&lt;ServiceName&gt;._&lt;Protocol&gt;", for example, "_http._tcp".<br>The maximum length is 63. |
| txtRecord | Map&lt;string, string&gt; | Yes | TXT record containing key/value pairs. The key cannot contain an equal sign (=), and the length of a single record (key.length + value.length). must be less than 255 bytes.<br> It is recommended that the total size of all keys and values after serialization be kept within 200-400 bytes. <br>Exceeding the limit of a single mDNS packet will cause the data to fail to be properly broadcast or to be ignored by the peer. There is no limit to the number of key-value pairs. The definition format is as follows: &lt;a href="http://files.dns-sd.org/draft-cheshire-dnsext-dns-sd.txt"&gt;draft-cheshire-dnsext-dns-sd.txt&lt;/a&gt; |
| serviceName | string | Yes | Service name used to identify the local service object.<br>The maximum length is 63. |

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
  let txtRecord: Map<string, string> = new Map();
  txtRecord.set("name", "xxx");
  wifiManager.addDnsSdLocalP2pService("instanceName", "_http._tcp", txtRecord, "serviceName");
} catch (error) {
  console.error("failed: " + JSON.stringify(error));
}
```
