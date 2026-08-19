# enableHotspot

## 导入模块

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## enableHotspot

```TypeScript
function enableHotspot(): void
```

使能WLAN热点。 该方法为异步方法。启用WLAN热点后，Wi-Fi可能会被禁用。

**起始版本：** 9

**废弃版本：** 10

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

<!--Device-wifiManagerExt-function enableHotspot(): void--><!--Device-wifiManagerExt-function enableHotspot(): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2701000](../errorcode-wifi.md#2701000-ap扩展模块异常) | Operation failed. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';

  try {
      wifiManagerExt.enableHotspot();
  }catch(error){
      console.error("failed: " + JSON.stringify(error));
  }
```

