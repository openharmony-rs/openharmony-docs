# addDeviceConfig（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig): Promise<number>
```

添加网络配置。使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | 是 | Wi-Fi配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;number&gt; | Promise对象。返回添加的网络配置ID，如果值为-1表示添加失败。 |

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


<a id="adddeviceconfig-1"></a>

## addDeviceConfig

```TypeScript
function addDeviceConfig(config: WifiDeviceConfig, callback: AsyncCallback<number>): void
```

添加网络配置。使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [addDeviceConfig](arkts-connectivity-wifimanager-adddeviceconfig-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.SET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | 是 | Wi-Fi配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;number&gt; | 是 | 回调函数。当操作成功时，error为0，data为添加的网络配置ID，如果data值为-1，表示添加失败。当error为非0，表示处理出现错误。 |

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
