# getStations（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getStations

```TypeScript
function getStations(): Array<StationInfo>
```

获取连接的设备。 &lt;p&gt;该方法只能在作为热点的设备上使用。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** getHotspotStations

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.MANAGE_WIFI_HOTSPOT

<!--Device-wifi-function getStations(): Array<StationInfo>--><!--Device-wifi-function getStations(): Array<StationInfo>-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;StationInfo&gt; | 连接的设备数组。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let stations = wifi.getStations();
    console.info("result:" + JSON.stringify(stations));        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

