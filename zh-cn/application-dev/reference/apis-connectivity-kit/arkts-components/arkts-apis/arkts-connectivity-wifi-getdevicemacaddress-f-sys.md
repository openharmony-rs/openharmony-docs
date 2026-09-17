# getDeviceMacAddress（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## getDeviceMacAddress

```TypeScript
function getDeviceMacAddress(): string[]
```

获取设备的MAC地址。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getDeviceMacAddress](arkts-connectivity-wifimanager-getdevicemacaddress-f.md)

**需要权限：** ohos.permission.GET_WIFI_LOCAL_MAC and ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| string[] | MAC地址。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
    let ret = wifi.getDeviceMacAddress();
    console.info("deviceMacAddress:" + JSON.stringify(ret));
}catch(error){
    console.error("failed:" + JSON.stringify(error));
}
```
