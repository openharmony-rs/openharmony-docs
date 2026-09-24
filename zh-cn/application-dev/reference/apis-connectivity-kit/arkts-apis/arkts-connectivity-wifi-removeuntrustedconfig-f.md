# removeUntrustedConfig

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## removeUntrustedConfig

```TypeScript
function removeUntrustedConfig(config: WifiDeviceConfig): Promise<boolean>
```

移除不可信网络配置，使用Promise异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | 是 | Wi-Fi配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | Promise对象。表示操作结果，true: 成功， false: 失败。 |

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
      ipAddress: 0,
      gateway: 0,
      dnsServers: [],
      domains: []
    }
  }
  wifi.removeUntrustedConfig(config).then(result => {
    console.info("result:" + JSON.stringify(result));
  });  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```


<a id="removeuntrustedconfig-1"></a>

## removeUntrustedConfig

```TypeScript
function removeUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback<boolean>): void
```

移除不可信网络配置，使用callback异步回调。

> **说明：** 
> 
> 从API version 7开始支持，从API version 9开始废弃。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [removeCandidateConfig](arkts-connectivity-wifimanager-removecandidateconfig-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | [WifiDeviceConfig](arkts-connectivity-wifi-wifideviceconfig-i.md) | 是 | Wi-Fi配置信息。 |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;boolean&gt; | 是 | 回调函数。当操作成功时，异步错误对象error为0，data表示操作结果，true: 成功， false: 失败。如果error为非0，表示处理出现错误。 |

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
      ipAddress: 0,
      gateway: 0,
      dnsServers: [],
      domains: []
    }
  }
  wifi.removeUntrustedConfig(config, (error, result) => {
  console.info("result:" + JSON.stringify(result));
  });  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
