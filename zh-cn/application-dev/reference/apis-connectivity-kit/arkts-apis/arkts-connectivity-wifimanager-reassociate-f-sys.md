# reassociate（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## reassociate

```TypeScript
function reassociate(): void
```

重新关联当前网络。

**起始版本：** 9

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [202](../../errorcode-universal.md#202-系统api权限校验失败) | System API is not allowed called by Non-system application. |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |
| [2501001](../errorcode-wifi.md#2501001-sta功能未打开) | Wi-Fi STA disabled. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

try {
    wifiManager.reassociate();
} catch (error) {
    console.error("failed:" + JSON.stringify(error));
}
```
