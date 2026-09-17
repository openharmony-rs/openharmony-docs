# getIpv6Info

## Modules to Import

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getIpv6Info

```TypeScript
function getIpv6Info(): Ipv6Info
```

Obtain the IPv6 information of the Wi-Fi connection. The IPv6 information includes the host IP address, gateway address, and DNS information.

**Since:** 10

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| [Ipv6Info](arkts-connectivity-wifimanager-ipv6info-i.md) | Returns the IPv6 information of the Wi-Fi connection. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [801](../../errorcode-universal.md#801-api-not-supported) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta-internal-error) | Operation failed. |

**Examples**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let info = wifiManager.getIpv6Info();
    console.info("info:" + JSON.stringify(info));
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
