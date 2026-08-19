# HotspotConfig（系统接口）

WLAN热点配置信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [HotspotConfig](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md)

<!--Device-wifi-interface HotspotConfig--><!--Device-wifi-interface HotspotConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
import { wifiext } from '@kit.ConnectivityKit';
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

WLAN热点的频段

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [band](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#band)

<!--Device-HotspotConfig-band: number--><!--Device-HotspotConfig-band: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## maxConn

```TypeScript
maxConn: number
```

WLAN热点允许的最大连接数

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxConn](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#maxconn)

<!--Device-HotspotConfig-maxConn: number--><!--Device-HotspotConfig-maxConn: number-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## preSharedKey

```TypeScript
preSharedKey: string
```

WLAN热点的密码

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [preSharedKey](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#presharedkey)

<!--Device-HotspotConfig-preSharedKey: string--><!--Device-HotspotConfig-preSharedKey: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## securityType

```TypeScript
securityType: WifiSecurityType
```

WLAN热点的加密类型

**类型：** WifiSecurityType

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [securityType](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#securitytype)

<!--Device-HotspotConfig-securityType: WifiSecurityType--><!--Device-HotspotConfig-securityType: WifiSecurityType-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ssid

```TypeScript
ssid: string
```

WLAN热点的SSID

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ssid](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#ssid)

<!--Device-HotspotConfig-ssid: string--><!--Device-HotspotConfig-ssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

