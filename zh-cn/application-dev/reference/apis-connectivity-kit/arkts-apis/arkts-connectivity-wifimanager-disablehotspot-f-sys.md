# disableHotspot（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## disableHotspot

```TypeScript
function disableHotspot(): void
```

关闭WLAN热点功能。 此方法为异步方法。如果WLAN热点关闭后WLAN已使能，则WLAN可能会重新使能。

**起始版本：** 23

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifiManager-function disableHotspot(): void--><!--Device-wifiManager-function disableHotspot(): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  wifiManager.disableHotspot();  
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

