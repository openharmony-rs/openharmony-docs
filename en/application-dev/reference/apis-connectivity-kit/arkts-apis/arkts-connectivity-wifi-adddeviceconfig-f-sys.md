# addDeviceConfig (System API)

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig): Promise<number>
```

Adds Wi-Fi connection configuration to the device.

<p>The configuration will be updated when the configuration is added.</p>

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Yes | Indicates the device configuration for connection to the Wi-Fi network. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;number&gt; | Returns `networkId` if the configuration is added; returns `-1` otherwise. |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let config:wifi.WifiDeviceConfig = {
        ssid : "****",
        bssid:  "****",
        preSharedKey: "****",
        isHiddenSsid: false,
        securityType: 0,
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
    wifi.addDeviceConfig(config).then(result => {
        console.info("result:" + JSON.stringify(result));
    });    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```


<a id="adddeviceconfig-1"></a>

## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback<number>): void
```

Adds Wi-Fi connection configuration to the device.

<p>The configuration will be updated when the configuration is added.</p>

**Since:** 6

**Deprecated since:** 9

**Substitutes:** [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**System capability:** SystemCapability.Communication.WiFi.STA

**System API:** This is a system API.

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Yes | Indicates the device configuration for connection to the Wi-Fi network. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | Yes |  |

**Examples**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let config:wifi.WifiDeviceConfig = {
        ssid : "****",
        bssid:  "****",
        preSharedKey: "****",
        isHiddenSsid: false,
        securityType: 0,
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
    wifi.addDeviceConfig(config,(error,result) => {
        console.info("result:" + JSON.stringify(result));
    });    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
