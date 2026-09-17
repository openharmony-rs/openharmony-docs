# startScan

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## startScan

```TypeScript
function startScan(): void
```

启动Wi-Fi扫描。

- 应用程序在前台运行时，两分钟内最多可扫描四次。  
- 在后台运行时，三十分钟内最多可扫描一次。  
- 通过[on('wifiScanStateChange')](arkts-connectivity-wifimanager-on-f.md#onwifiscanstatechange)订阅扫描状  
态变更事件，监听扫描完成通知。

**起始版本：** 21

**需要权限：** ohos.permission.SET_WIFI_INFO

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
    wifiManager.startScan();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
