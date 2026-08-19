# getScanInfoList

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getScanInfoList

```TypeScript
function getScanInfoList(): Array<WifiScanInfo>
```

获取扫描结果。如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function getScanInfoList(): Array<WifiScanInfo>--><!--Device-wifiManager-function getScanInfoList(): Array<WifiScanInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WifiScanInfo&gt; | 返回扫描到的WLAN热点信息（如果有）。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let scanInfoList = wifiManager.getScanInfoList();
    console.info("scanInfoList:" + JSON.stringify(scanInfoList));
    let len = scanInfoList.length;
        console.info("wifi received scan info: " + len);
    if(len > 0){
      for (let i = 0; i < len; ++i) {
        console.info("ssid: " + scanInfoList[i].ssid);
        console.info("bssid: " + scanInfoList[i].bssid);
        console.info("capabilities: " + scanInfoList[i].capabilities);
        console.info("securityType: " + scanInfoList[i].securityType);
        console.info("rssi: " + scanInfoList[i].rssi);
        console.info("band: " + scanInfoList[i].band);
        console.info("frequency: " + scanInfoList[i].frequency);
        console.info("channelWidth: " + scanInfoList[i].channelWidth);
        console.info("timestamp: " + scanInfoList[i].timestamp);
        console.info("supportedWifiCategory: " + scanInfoList[i].supportedWifiCategory);
        console.info("isHiLinkNetwork: " + scanInfoList[i].isHiLinkNetwork);
      }
    }  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

