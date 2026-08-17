# addUntrustedConfig

## addUntrustedConfig

```TypeScript
function addUntrustedConfig(config: WifiDeviceConfig): Promise<boolean>
```

添加不可信网络配置，使用Promise异步回调。 &lt;p&gt;该方法一次添加一个配置。添加该配置后，设备将决定是否连接到热点。

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md#addcandidateconfig)

**需要权限：** ohos.permission.SET_WIFI_INFO

<!--Device-wifi-function addUntrustedConfig(config: WifiDeviceConfig): Promise<boolean>--><!--Device-wifi-function addUntrustedConfig(config: WifiDeviceConfig): Promise<boolean>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiDeviceConfig | 是 | WLAN配置信息。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;boolean&gt; | 表示操作结果，{ |

## 示例

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


## addUntrustedConfig

```TypeScript
function addUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback<boolean>): void
```

添加不可信网络配置，使用callback异步回调。 &lt;p&gt;该方法一次添加一个配置。添加该配置后，设备将决定是否连接到热点。

**起始版本：** 7

**ArkTS模式：** 起始版本为7。

**废弃版本：** 9

**替代接口：** [addCandidateConfig](arkts-connectivity-wifimanager-addcandidateconfig-f.md#addcandidateconfig)

**需要权限：** ohos.permission.SET_WIFI_INFO

<!--Device-wifi-function addUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback<boolean>): void--><!--Device-wifi-function addUntrustedConfig(config: WifiDeviceConfig, callback: AsyncCallback<boolean>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | WifiDeviceConfig | 是 | WLAN配置信息。 |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;boolean&gt; | 是 |  |

## 示例

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
  wifi.addUntrustedConfig(config,(error,result) => {
    console.info("result:" + JSON.stringify(result));
  });  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

