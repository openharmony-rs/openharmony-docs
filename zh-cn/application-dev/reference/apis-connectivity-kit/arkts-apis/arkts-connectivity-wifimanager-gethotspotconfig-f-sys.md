# getHotspotConfig（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getHotspotConfig

```TypeScript
function getHotspotConfig(): HotspotConfig
```

获取WLAN热点配置。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

<!--Device-wifiManager-function getHotspotConfig(): HotspotConfig--><!--Device-wifiManager-function getHotspotConfig(): HotspotConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| HotspotConfig | 返回已存在或已使能的WLAN热点配置。 |

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
  let config = wifiManager.getHotspotConfig();
  console.info("result:" + JSON.stringify(config));    
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

