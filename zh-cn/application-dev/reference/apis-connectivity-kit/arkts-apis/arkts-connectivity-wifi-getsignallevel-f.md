# getSignalLevel

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getSignalLevel

```TypeScript
function getSignalLevel(rssi: number, band: number): number
```

查询WLAN信号强度。

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [getSignalLevel](arkts-connectivity-wifimanager-getsignallevel-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getSignalLevel(rssi: number, band: number): number--><!--Device-wifi-function getSignalLevel(rssi: number, band: number): number-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rssi | number | 是 | 热点的信号强度(dBm)。 |
| band | number | 是 | WLAN接入点的频段。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 信号强度，取值范围为[0, 4]。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let rssi = 0;
  let band = 0;
  let level = wifi.getSignalLevel(rssi,band);
  console.info("level:" + JSON.stringify(level));
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

