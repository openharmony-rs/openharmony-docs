# scan

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## scan

```TypeScript
function scan(): boolean
```

启动WLAN扫描。 &lt;p&gt;该接口工作在异步模式。&lt;/p&gt;

**起始版本：** 6

**废弃版本：** 9

**替代接口：** [scan](arkts-connectivity-wifimanager-scan-f.md)

**需要权限：** ohos.permission.SET_WIFI_INFO and ohos.permission.LOCATION

<!--Device-wifi-function scan(): boolean--><!--Device-wifi-function scan(): boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| boolean | 扫描操作执行成功时返回{ |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  wifi.scan();
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

