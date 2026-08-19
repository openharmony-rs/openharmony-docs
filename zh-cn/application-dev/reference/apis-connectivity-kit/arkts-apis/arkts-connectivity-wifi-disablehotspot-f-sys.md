# disableHotspot（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## disableHotspot

```TypeScript
function disableHotspot(): boolean
```

去使能热点。 &lt;p&gt;该方法是异步的。去使能热点后，如果WLAN已使能，WLAN可能会被重新使能。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [disableHotspot](arkts-connectivity-wifimanager-disablehotspot-f-sys.md)

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifi-function disableHotspot(): boolean--><!--Device-wifi-function disableHotspot(): boolean-End-->

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
    wifi.disableHotspot();    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

