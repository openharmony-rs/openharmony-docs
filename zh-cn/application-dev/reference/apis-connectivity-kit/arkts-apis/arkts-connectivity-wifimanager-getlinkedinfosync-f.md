# getLinkedInfoSync

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getLinkedInfoSync

```TypeScript
function getLinkedInfoSync(): WifiLinkedInfo
```

获取WLAN连接信息。此接口同步返回结果。 如果未获取ohos.permission.GET_WIFI_PEERS_MAC权限，返回随机bssid。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function getLinkedInfoSync(): WifiLinkedInfo--><!--Device-wifiManager-function getLinkedInfoSync(): WifiLinkedInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| WifiLinkedInfo | 返回WLAN连接信息。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  try {
    let linkInfo = wifiManager.getLinkedInfoSync();
    console.info("get linked info:" + JSON.stringify(linkInfo));
  } catch(error) {
    console.error("get linked info failed:" + JSON.stringify(error));
  }
```

