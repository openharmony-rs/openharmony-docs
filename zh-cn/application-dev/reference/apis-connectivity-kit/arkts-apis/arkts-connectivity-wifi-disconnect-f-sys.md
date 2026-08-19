# disconnect（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## disconnect

```TypeScript
function disconnect(): boolean
```

断开连接的网络。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [disconnect](arkts-connectivity-wifimanager-disconnect-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

<!--Device-wifi-function disconnect(): boolean--><!--Device-wifi-function disconnect(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.disconnect();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

