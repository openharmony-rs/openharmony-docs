# getDeviceConfigs (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getDeviceConfigs

```TypeScript
function getDeviceConfigs(): Array<WifiDeviceConfig>
```

Obtains the list of all existing Wi-Fi configurations.

<p>You can obtain only the Wi-Fi configurations you created on your own application.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [getDeviceConfigs](arkts-connectivity-wifimanager-getdeviceconfigs-f.md)

**Required permissions:** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.GET_WIFI_CONFIG

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md)&gt; | sReturns the list of all existing Wi-Fi configurations you created on your application. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let configs = wifi.getDeviceConfigs();
    console.info("configs:" + JSON.stringify(configs));
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
