# stopDiscoverDevices

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## stopDiscoverDevices

```TypeScript
function stopDiscoverDevices(): void
```

停止发现WLAN P2P设备。

**起始版本：** 9

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.P2P

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2801000](../errorcode-wifi.md#2801000-p2p模块异常) | Operation failed. |
| [2801001](../errorcode-wifi.md#2801001-p2p功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    wifiManager.stopDiscoverDevices();  
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
