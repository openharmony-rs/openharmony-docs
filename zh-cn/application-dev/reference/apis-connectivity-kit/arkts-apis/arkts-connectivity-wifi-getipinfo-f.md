# getIpInfo

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getIpInfo

```TypeScript
function getIpInfo(): IpInfo
```

获取IP信息。 &lt;p&gt;IP信息包括主机IP地址、网关地址和DNS信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getIpInfo](arkts-connectivity-wifimanager-getipinfo-f.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getIpInfo(): IpInfo--><!--Device-wifi-function getIpInfo(): IpInfo-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**返回值：**

| 类型 | 说明 |
| --- | --- |
| IpInfo | IP信息。 |

**示例**

```TypeScript
import wifi from '@ohos.wifi';

try {
  let info = wifi.getIpInfo();
  console.info("info:" + JSON.stringify(info));
}catch(error){
  console.error("failed:" + JSON.stringify(error));
}
```

