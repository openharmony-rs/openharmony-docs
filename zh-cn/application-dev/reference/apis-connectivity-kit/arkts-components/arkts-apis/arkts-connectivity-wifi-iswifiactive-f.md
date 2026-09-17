# isWifiActive

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## isWifiActive

```TypeScript
function isWifiActive(): boolean
```

查询Wi-Fi是否已使能。

> **说明：** 
> 
> 从API version 6开始支持，从API version 9开始废弃。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | true:已使能， false:未使能。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let isWifiActive = wifi.isWifiActive();
  console.info("isWifiActive:" + isWifiActive);
} catch (error) {
  console.error("failed:" + JSON.stringify(error));
}
```
