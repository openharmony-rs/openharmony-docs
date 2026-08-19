# removeDevice（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## removeDevice

```TypeScript
function removeDevice(id: number): boolean
```

移除指定的网络配置。 &lt;p&gt;删除WLAN网络后，其配置将从网络配置列表中删除。 如果正在连接该WLAN网络，连接将被中断。 应用只能删除自己创建的WLAN网络。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** removeDeviceConfig

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

<!--Device-wifi-function removeDevice(id: number): boolean--><!--Device-wifi-function removeDevice(id: number): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| id | number | 是 | WLAN网络的ID， 可通过{ |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let id = 0;
    wifi.removeDevice(id);        
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```

