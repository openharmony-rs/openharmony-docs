# isHotspotActive

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isHotspotActive

```TypeScript
function isHotspotActive(): boolean
```

检查设备上的WLAN热点是否已激活。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifiManager-function isHotspotActive(): boolean--><!--Device-wifiManager-function isHotspotActive(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WLAN热点已使能时返回{ |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2601000](../errorcode-wifi.md#2601000-hotspot模块异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let ret = wifiManager.isHotspotActive();
    console.info("result:" + ret);    
  } catch(error) {
    console.error("failed:" + JSON.stringify(error));
  }
```

