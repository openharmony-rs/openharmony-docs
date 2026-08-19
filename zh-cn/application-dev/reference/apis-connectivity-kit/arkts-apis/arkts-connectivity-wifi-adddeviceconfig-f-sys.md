# addDeviceConfig（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig): Promise<number>
```

添加网络配置，使用Promise异步回调。 &lt;p&gt;添加配置后，配置将被更新。&lt;/p&gt;

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

<!--Device-wifi-function addDeviceConfig(config: WifiDeviceConfig): Promise<number>--><!--Device-wifi-function addDeviceConfig(config: WifiDeviceConfig): Promise<number>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiDeviceConfig | 是 | WLAN配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | 返回添加的网络配置ID，如果值为{ |

**示例**

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


## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback<number>): void
```

添加网络配置，使用callback异步回调。 &lt;p&gt;添加配置后，配置将被更新。&lt;/p&gt;

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

<!--Device-wifi-function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback<number>): void--><!--Device-wifi-function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback<number>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiDeviceConfig | 是 | WLAN配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;number&gt; | 是 |  |

**示例**

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

