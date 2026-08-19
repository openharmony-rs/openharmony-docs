# getSupportedFeatures（系统接口）

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## getSupportedFeatures

```TypeScript
function getSupportedFeatures(): number
```

查询设备支持的特性。 &lt;p&gt;检查设备是否支持指定特性。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [getSupportedFeatures](arkts-connectivity-wifimanager-getsupportedfeatures-f-sys.md)

**需要权限：** ohos.permission.GET_WIFI_INFO

<!--Device-wifi-function getSupportedFeatures(): number--><!--Device-wifi-function getSupportedFeatures(): number-End-->

**系统能力：** SystemCapability.Communication.WiFi.Core

**系统接口：** 此接口为系统接口。

**返回值：**

| 类型 | 说明 |
| --- | --- |
| number | 支持的特性值。 |

