# isWifiActive

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## isWifiActive

```TypeScript
function isWifiActive(): boolean
```

查询Wi-Fi开关是否已激活。

**起始版本：** 9

**需要权限：** 
- API版本13+：N/A
- API版本9-12：ohos.permission.GET_WIFI_INFO

**原子化服务API：** 从API版本11开始，该接口支持在原子化服务中使用。

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:已激活， false:未激活。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied.<br>**适用版本：** 9 - 12 |
| [801](../../errorcode-universal.md#801-该设备不支持此api) | Capability not supported. |
| [2501000](../errorcode-wifi.md#2501000-sta内部异常) | Operation failed. |

**示例**

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';

  try {
    let isWifiActive = wifiManager.isWifiActive();
    console.info("isWifiActive:" + isWifiActive);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```
