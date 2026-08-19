# getDeviceConfigs（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getDeviceConfigs

```TypeScript
function getDeviceConfigs(): Array<WifiDeviceConfig>
```

获取网络配置。 &lt;p&gt;只能获取本应用创建的网络配置。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getDeviceConfigs](arkts-connectivity-wifimanager-getdeviceconfigs-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION and ohos.permission.GET_WIFI_CONFIG

<!--Device-wifi-function getDeviceConfigs(): Array<WifiDeviceConfig>--><!--Device-wifi-function getDeviceConfigs(): Array<WifiDeviceConfig>-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Array&lt;WifiDeviceConfig&gt; | 网络配置信息的数组。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let configs = wifi.getDeviceConfigs();
    console.info("configs:" + JSON.stringify(configs));
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

