# getScanResults

## getScanResults

```TypeScript
function getScanResults(): Promise<Array<WifiScanInfo>>
```

获取扫描结果，使用Promise异步回调。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** 10

**替代接口：** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md#getscaninfolist)

**需要权限：** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or (ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION))

<!--Device-wifiManager-function getScanResults(): Promise<Array<WifiScanInfo>>--><!--Device-wifiManager-function getScanResults(): Promise<Array<WifiScanInfo>>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;Array&lt;WifiScanInfo&gt;&gt; | 返回扫描到的WLAN热点信息（如果有）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |


## getScanResults

```TypeScript
function getScanResults(callback: AsyncCallback<Array<WifiScanInfo>>): void
```

获取扫描结果，使用callback异步回调。

**起始版本：** 9

**ArkTS模式：** 起始版本为9。

**废弃版本：** 10

**替代接口：** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md#getscaninfolist)

**需要权限：** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or (ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION))

<!--Device-wifiManager-function getScanResults(callback: AsyncCallback<Array<WifiScanInfo>>): void--><!--Device-wifiManager-function getScanResults(callback: AsyncCallback<Array<WifiScanInfo>>): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| callback | [AsyncCallback](../../apis-basic-service-kit/arkts-apis/arkts-basicservices-asynccallback-t.md)&lt;Array&lt;WifiScanInfo&gt;&gt; | 是 | 回调函数，返回扫描到的WLAN热点信息（如果有）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

## 示例

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  wifiManager.getScanResults((err, result) => {
      if (err) {
          console.error("get scan info error");
          return;
      }
  
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
  
  wifiManager.getScanResults().then(result => {
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
  }).catch((err:number) => {
      console.error("failed:" + JSON.stringify(err));
  });
```

