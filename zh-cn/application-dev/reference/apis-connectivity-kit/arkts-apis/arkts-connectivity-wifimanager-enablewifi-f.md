# enableWifi

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## enableWifi

```TypeScript
function enableWifi(): void
```

启动WLAN。

**起始版本：** 15

**需要权限：** ohos.permission.SET_WIFI_INFO and (ohos.permission.MANAGE_WIFI_CONNECTION or ohos.permission.MANAGE_ENTERPRISE_WIFI_CONNECTION)

**系统能力：** SystemCapability.Communication.WiFi.STA

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501003](../errorcode-wifi.md#2501003-服务打开失败) | Operation failed because the service is being closed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
  
  try {
    wifiManager.enableWifi();
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
