# isConnected

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isConnected

```TypeScript
function isConnected(): boolean
```

查询WLAN是否已连接。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isConnected](arkts-connectivity-wifimanager-isconnected-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function isConnected(): boolean--><!--Device-wifi-function isConnected(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:已连接，false:未连接。 |

