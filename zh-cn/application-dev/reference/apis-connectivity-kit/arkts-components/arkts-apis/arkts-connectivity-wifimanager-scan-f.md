# scan

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## scan

```TypeScript
function scan(): void
```

启动Wi-Fi扫描，使用前先开启Wi-Fi。

**起始版本：** 9

**废弃版本：** 10

**替代接口：** [startScan](arkts-connectivity-wifimanager-startscan-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.APPROXIMATELY_LOCATION

**系统能力：** SystemCapability.Communication.WiFi.STA

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.scan();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
