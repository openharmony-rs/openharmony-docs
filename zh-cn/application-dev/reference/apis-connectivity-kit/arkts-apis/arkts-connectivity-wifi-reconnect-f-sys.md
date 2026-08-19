# reconnect（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## reconnect

```TypeScript
function reconnect(): boolean
```

重新连接网络。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [reconnect](arkts-connectivity-wifimanager-reconnect-f-sys.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

<!--Device-wifi-function reconnect(): boolean--><!--Device-wifi-function reconnect(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:操作成功，false:操作失败。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.reconnect();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

