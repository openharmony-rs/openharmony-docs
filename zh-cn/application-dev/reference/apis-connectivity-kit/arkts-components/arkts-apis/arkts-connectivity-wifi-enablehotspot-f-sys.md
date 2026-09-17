# enableHotspot（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## enableHotspot

```TypeScript
function enableHotspot(): boolean
```

开启热点。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [enableHotspot](arkts-connectivity-wifimanager-enablehotspot-f-sys.md)

**需要权限：** ohos.permission.MANAGE_WIFI_HOTSPOT

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 开启热点是否成功。true:操作成功， false:操作失败。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    wifi.enableHotspot();    
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
