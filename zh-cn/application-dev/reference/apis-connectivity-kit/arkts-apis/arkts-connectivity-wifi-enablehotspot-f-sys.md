# enableHotspot（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## enableHotspot

```TypeScript
function enableHotspot(): boolean
```

使能热点。 &lt;p&gt;该方法是异步的。使能热点后，WLAN可能会被去使能。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [enableHotspot](arkts-connectivity-wifimanager-enablehotspot-f-sys.md)

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifi-function enableHotspot(): boolean--><!--Device-wifi-function enableHotspot(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.enableHotspot();    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

