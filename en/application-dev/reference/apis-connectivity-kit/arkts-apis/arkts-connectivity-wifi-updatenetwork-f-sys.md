# updateNetwork (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## updateNetwork

```TypeScript
function updateNetwork(config: WifiDeviceConfig): number
```

Updates the specified Wi-Fi configuration.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** updateDeviceConfig

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Yes | Indicates the Wi-Fi configuration to update. |

**Return value:**

| Type | Description |
| --- | --- |
| number | Returns the network ID in the updated Wi-Fi configuration if the update is successful; returns `-1` if the specified Wi-Fi configuration is not contained in the list. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let config:wifi.WifiDeviceConfig = {
        ssid : "****",
        bssid:  "****",
        preSharedKey: "****",
        isHiddenSsid: false,
        securityType: 3,
        creatorUid: 0,
        disableReason: 0,
        netId: 0,
        randomMacType: 0,
        randomMacAddr:  "****",
        ipType: 0,
        staticIp: {
            ipAddress: "",
            gateway: "",
            dnsServers: [],
            domains: []
        }
    }
    let ret = wifi.updateNetwork(config);
    console.error("ret:" + ret);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
