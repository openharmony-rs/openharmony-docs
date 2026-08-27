# startDiscoverDevices

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## startDiscoverDevices

```TypeScript
function startDiscoverDevices(): boolean
```

发现WLAN P2P设备。

**起始版本：** 8

**废弃版本：** 9

**替代接口：** startDiscoverP2pDevices

**需要权限：** ohos.permission.GET_WIFI_INFO and ohos.permission.LOCATION

**系统能力：** SystemCapability.Communication.WiFi.P2P

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 操作成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.startDiscoverDevices();  
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```
