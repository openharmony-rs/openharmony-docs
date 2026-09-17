# addUntrustedConfig

## Modules to Import

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## addUntrustedConfig

```TypeScript
function addUntrustedConfig(config: WifiDeviceConfig): Promise<boolean>
```

Adds a specified untrusted hotspot configuration.

<p>This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Yes | Indicates the device configuration for connection to the Wi-Fi network. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;boolean&gt; | Returns `true` if the untrusted hotspot configuration is added, returns `false` otherwise. |

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
      ipAddress: 0,
      gateway: 0,
      dnsServers: [],
      domains: []
    }
  }
  wifi.addUntrustedConfig(config).then(result => {
    console.info("result:" + JSON.stringify(result));
  });  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

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
      ipAddress: 0,
      gateway: 0,
      dnsServers: [],
      domains: []
    }
  }
  wifi.addUntrustedConfig(config, (error, result) => {
    console.info("result:" + JSON.stringify(result));
  });  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```


## addUntrustedConfig

```TypeScript
function addUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback<boolean>): void
```

Adds a specified untrusted hotspot configuration.

<p>This method adds one configuration at a time. After this configuration is added, your device will determine whether to connect to the hotspot.

**Since:** 7

**Deprecated since:** 9

**Substitutes:** [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md)

**Required permissions:** ohos.permission.SET_WIFI_INFO

**System capability:** SystemCapability.Communication.WiFi.STA

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | Yes | Indicates the device configuration for connection to the Wi-Fi network. |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | Yes |  |

**Examples**

See [addUntrustedConfig](#adduntrustedconfig)
