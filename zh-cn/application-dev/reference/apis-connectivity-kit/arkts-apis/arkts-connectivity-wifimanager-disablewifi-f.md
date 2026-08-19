# disableWifi

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## disableWifi

```TypeScript
function disableWifi(): void
```

关闭WLAN。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION)

<!--Device-wifiManager-function disableWifi(): void--><!--Device-wifiManager-function disableWifi(): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501004](../errorcode-wifi.md#2501004-服务关闭失败) | Operation failed because the service is being opened. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.disableWifi();
  }catch(error){
    console.error(`disableWifi failed. ${error.message}`);
  }
```

