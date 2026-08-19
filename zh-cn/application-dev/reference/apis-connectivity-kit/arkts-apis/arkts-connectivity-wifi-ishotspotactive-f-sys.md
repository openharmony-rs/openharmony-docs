# isHotspotActive（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## isHotspotActive

```TypeScript
function isHotspotActive(): boolean
```

热点是否已使能。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [isHotspotActive](arkts-connectivity-wifimanager-ishotspotactive-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function isHotspotActive(): boolean--><!--Device-wifi-function isHotspotActive(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:已使能，false:未使能。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let ret = wifi.isHotspotActive();
    console.info("result:" + ret);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

