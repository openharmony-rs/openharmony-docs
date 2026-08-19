# setPowerMode

## 导入模块

```TypeScript
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## setPowerMode

```TypeScript
function setPowerMode(mode: PowerMode): void
```

设置功率模式。

**起始版本：** 9

**废弃版本：** 10

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT_EXT

<!--Device-wifiManagerExt-function setPowerMode(mode: PowerMode): void--><!--Device-wifiManagerExt-function setPowerMode(mode: PowerMode): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Extension

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| mode | [PowerMode](arkts-connectivity-wifimanagerext-powermode-e.md) | 是 |  |

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
      let model = 0;
      wifiManagerExt.setPowerMode(model);
  }catch(error){
      console.error("failed: " + JSON.stringify(error));
  }
```

