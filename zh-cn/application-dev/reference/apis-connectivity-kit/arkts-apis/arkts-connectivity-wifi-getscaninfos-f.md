# getScanInfos

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getScanInfos

```TypeScript
function getScanInfos(): Promise<Array<WifiScanInfo>>
```

获取扫描结果，使用Promise异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or ohos.permission.LOCATION)

<!--Device-wifi-function getScanInfos(): Promise<Array<WifiScanInfo>>--><!--Device-wifi-function getScanInfos(): Promise<Array<WifiScanInfo>>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WifiScanInfo&gt;&gt; | 返回扫描到的热点列表。 |


## getScanInfos

```TypeScript
function getScanInfos(callback: AsyncCallback<Array<WifiScanInfo>>): void
```

获取扫描结果，使用callback异步回调。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or ohos.permission.LOCATION)

<!--Device-wifi-function getScanInfos(callback: AsyncCallback<Array<WifiScanInfo>>): void--><!--Device-wifi-function getScanInfos(callback: AsyncCallback<Array<WifiScanInfo>>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-services-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;WifiScanInfo&gt;&gt; | 是 |  |

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

