# getScanResultsSync

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getScanResultsSync

```TypeScript
function getScanResultsSync(): Array<WifiScanInfo>
```

获取扫描结果，使用同步方式返回扫描到的WLAN热点信息（如果有）。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [getScanInfoList](arkts-connectivity-wifimanager-getscaninfolist-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and (ohos.permission.GET_WIFI_PEERS_MAC or (ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION))

<!--Device-wifiManager-function getScanResultsSync(): Array<WifiScanInfo>--><!--Device-wifiManager-function getScanResultsSync(): Array<WifiScanInfo>-End-->

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

