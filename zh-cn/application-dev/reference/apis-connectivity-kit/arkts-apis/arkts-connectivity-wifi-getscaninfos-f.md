# getScanInfos

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getScanInfos

```TypeScript
function getScanInfos(): Promise<Array<WifiScanInfo>>
```

获取扫描结果，使用Promise异步回调。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or ohos.permission.LOCATION)

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;[WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md)&gt;&gt; | Promise对象。返回扫描到的热点列表。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

wifi.getScanInfos().then(result => {
    let len = result.length;
    console.info("wifi received scan info: " + len);
    for (let i = 0; i < len; ++i) {
        console.info("ssid: " + result[i].ssid);
        console.info("bssid: " + result[i].bssid);
        console.info("capabilities: " + result[i].capabilities);
        console.info("securityType: " + result[i].securityType);
        console.info("rssi: " + result[i].rssi);
        console.info("band: " + result[i].band);
        console.info("frequency: " + result[i].frequency);
        console.info("channelWidth: " + result[i].channelWidth);
        console.info("timestamp: " + result[i].timestamp);
    }
});
```


<a id="getscaninfos-1"></a>

## getScanInfos

```TypeScript
function getScanInfos(callback: AsyncCallback<Array<WifiScanInfo>>): void
```

获取扫描结果，使用callback异步回调。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or ohos.permission.LOCATION)

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-base-asynccallback-i.md)&lt;Array&lt;[WifiScanInfo](arkts-connectivity-wifi-wifiscaninfo-i.md)&gt;&gt; | 是 | 回调函数。当成功时，err为0，data为扫描到的热点；否则err为非0值，data为空。 |

**示例**

参见 [getScanInfos](#getscaninfos)
