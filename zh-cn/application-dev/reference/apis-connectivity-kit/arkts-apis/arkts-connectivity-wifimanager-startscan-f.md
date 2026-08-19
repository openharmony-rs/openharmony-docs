# startScan

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## startScan

```TypeScript
function startScan(): void
```

启动WLAN扫描。

**起始版本：** 23

**需要权限：** ohos.permission.SET_WIFI_INFO

<!--Device-wifiManager-function startScan(): void--><!--Device-wifiManager-function startScan(): void-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.startScan();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

