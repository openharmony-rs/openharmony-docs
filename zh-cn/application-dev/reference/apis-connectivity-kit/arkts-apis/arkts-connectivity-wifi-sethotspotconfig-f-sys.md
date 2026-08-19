# setHotspotConfig（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## setHotspotConfig

```TypeScript
function setHotspotConfig(config: HotspotConfig): boolean
```

设置热点配置信息。 &lt;p&gt;仅支持配置OPEN和WPA2 PSK热点。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [setHotspotConfig](arkts-connectivity-wifimanager-sethotspotconfig-f-sys.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.GET_WIFI_CONFIG

<!--Device-wifi-function setHotspotConfig(config: HotspotConfig): boolean--><!--Device-wifi-function setHotspotConfig(config: HotspotConfig): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| config | HotspotConfig | 是 |  |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let config:wifi.HotspotConfig = {
        ssid: "****",
        securityType: 3,
        band: 0,
        preSharedKey: "****",
        maxConn: 0
    }
    let ret = wifi.setHotspotConfig(config);
    console.info("result:" + ret);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

