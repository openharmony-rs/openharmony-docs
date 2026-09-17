# getIpInfo

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getIpInfo

```TypeScript
function getIpInfo(): IpInfo
```

Obtains the IP information of a Wi-Fi connection.

<p>The IP information includes the host IP address, gateway address, and DNS information.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| [IpInfo](arkts-connectivity-wifi-ipinfo-i.md) | Returns the IP information of the Wi-Fi connection. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let info = wifi.getIpInfo();
  console.info("info:" + JSON.stringify(info));
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
