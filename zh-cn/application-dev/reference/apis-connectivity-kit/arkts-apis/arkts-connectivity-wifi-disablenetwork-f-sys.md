# disableNetwork（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## disableNetwork

```TypeScript
function disableNetwork(netId: number): boolean
```

去使能网络配置。 &lt;p&gt;去使能的网络将不再被关联。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** disableDeviceConfig

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

<!--Device-wifi-function disableNetwork(netId: number): boolean--><!--Device-wifi-function disableNetwork(netId: number): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| netId | number | 是 | 网络配置ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 指定网络已去使能返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let netId = 0;
    wifi.disableNetwork(netId);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

