# isHotspotDualBandSupported（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isHotspotDualBandSupported

```TypeScript
function isHotspotDualBandSupported(): boolean
```

热点是否支持双频。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isHotspotDualBandSupported](arkts-connectivity-wifimanager-ishotspotdualbandsupported-f-sys.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifi-function isHotspotDualBandSupported(): boolean--><!--Device-wifi-function isHotspotDualBandSupported(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:支持，{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let ret = wifi.isHotspotDualBandSupported();
    console.info("result:" + ret);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

