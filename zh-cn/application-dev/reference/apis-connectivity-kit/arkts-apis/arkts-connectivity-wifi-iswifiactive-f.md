# isWifiActive

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## isWifiActive

```TypeScript
function isWifiActive(): boolean
```

查询WLAN是否已使能。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [isWifiActive](arkts-connectivity-wifimanager-iswifiactive-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | WLAN已使能时返回{ |

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
