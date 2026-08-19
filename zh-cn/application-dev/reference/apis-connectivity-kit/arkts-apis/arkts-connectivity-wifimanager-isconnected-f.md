# isConnected

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isConnected

```TypeScript
function isConnected(): boolean
```

检查WLAN连接是否已建立。

**起始版本：** 23

**需要权限：** ohos.permission.GET_WIFI_INFO

**原子化服务API：** 从API版本23开始，该接口支持在原子化服务API中使用。

<!--Device-wifiManager-function isConnected(): boolean--><!--Device-wifiManager-function isConnected(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WLAN连接已建立时返回{ |

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
    let ret = wifiManager.isConnected();
    console.info("isConnected:" + ret);
  }catch(error){
    console.error("failed:" + JSON.stringify(error));
  }
```

