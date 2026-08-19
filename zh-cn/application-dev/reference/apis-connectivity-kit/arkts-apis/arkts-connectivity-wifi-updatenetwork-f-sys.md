# updateNetwork（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## updateNetwork

```TypeScript
function updateNetwork(config: WifiDeviceConfig): number
```

更新网络配置。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** updateDeviceConfig

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

<!--Device-wifi-function updateNetwork(config: WifiDeviceConfig): number--><!--Device-wifi-function updateNetwork(config: WifiDeviceConfig): number-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiDeviceConfig | 是 | WLAN配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 返回更新的网络配置ID，如果值为{ |

**示例**

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

