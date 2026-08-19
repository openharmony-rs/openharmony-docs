# setHotspotConfig（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## setHotspotConfig

```TypeScript
function setHotspotConfig(config: HotspotConfig): void
```

设置设备的热点配置。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

<!--Device-wifiManager-function setHotspotConfig(config: HotspotConfig): void--><!--Device-wifiManager-function setHotspotConfig(config: HotspotConfig): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | HotspotConfig | 是 | 表示WLAN热点配置。 SSID和{@code securityType}必须有效且正确。 如果{@code securityType}不是{@code open}，{@code preSharedKey}必须有效且正确。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [401](../../errorcode-universal.md#401-参数检查失败) | Invalid parameters. Possible causes: 1. Incorrect parameter types. 2.Parameter verification failed. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
  let config:wifiManager.HotspotConfig = {
    ssid: "****",
    securityType: 3,
    band: 0,
    channel: 0,
    preSharedKey: "****",
    maxConn: 0
  }
  let ret = wifiManager.setHotspotConfig(config);
  console.info("result:" + ret);    
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

