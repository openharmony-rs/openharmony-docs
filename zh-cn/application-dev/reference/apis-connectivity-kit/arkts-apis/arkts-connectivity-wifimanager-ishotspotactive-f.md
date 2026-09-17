# isHotspotActive

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## isHotspotActive

```TypeScript
function isHotspotActive(): boolean
```

热点是否已开启。

**起始版本：** 15

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 热点是否已开启。true:已开启， false:未开启。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application.<br>**适用版本：** 9 - 14 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
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
