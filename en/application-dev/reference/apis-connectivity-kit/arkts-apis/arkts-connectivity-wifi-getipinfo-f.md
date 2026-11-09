# getIpInfo

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getIpInfo

```TypeScript
function getIpInfo(): IpInfo
```

Obtains IP information.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getIpInfo(): IpInfo--><!--Device-wifi-function getIpInfo(): IpInfo-End-->

**System capability:** SystemCapability.Communication.WiFi.STA

**Return value:**

| Type | Description |
| --- | --- |
| [IpInfo](arkts-connectivity-wifi-ipinfo-i.md) | IP information obtained. |

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
