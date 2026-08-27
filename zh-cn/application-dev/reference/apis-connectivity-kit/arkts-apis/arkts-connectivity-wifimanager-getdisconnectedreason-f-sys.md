# getDisconnectedReason（系统接口）

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## getDisconnectedReason

```TypeScript
function getDisconnectedReason(): DisconnectedReason
```

获取最近的断开连接原因。

**起始版本：** 10

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| DisconnectedReason | 返回最近的断开连接原因。 |

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
  let disconnectedReason = wifiManager.getDisconnectedReason();  
    console.info("disconnectedReason:" + disconnectedReason);
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
