# isHotspotDualBandSupported（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isHotspotDualBandSupported

```TypeScript
function isHotspotDualBandSupported(): boolean
```

检查作为WLAN热点的设备是否同时支持2.4 GHz和5 GHz WLAN。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifiManager-function isHotspotDualBandSupported(): boolean--><!--Device-wifiManager-function isHotspotDualBandSupported(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 方法调用成功时返回{ |

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
  let ret = wifiManager.isHotspotDualBandSupported();
  console.info("result:" + ret);    
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```

