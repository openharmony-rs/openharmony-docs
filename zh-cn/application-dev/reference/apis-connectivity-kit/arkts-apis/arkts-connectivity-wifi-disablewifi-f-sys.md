# disableWifi（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## disableWifi

```TypeScript
function disableWifi(): boolean
```

去使能WLAN。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [disableWifi](arkts-connectivity-wifimanager-disablewifi-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.MANAGE_WIFI_CONNECTION

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
    wifi.disableWifi();
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
