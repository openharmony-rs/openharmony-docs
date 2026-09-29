# HotspotConfig（系统接口）

```TypeScript
interface HotspotConfig
```

热点配置信息。

**起始版本：** 9

<!--Device-wifiManager-interface HotspotConfig--><!--Device-wifiManager-interface HotspotConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

热点的带宽。1: 2.4G, 2: 5G, 3: 双模频段

**类型：** number

**起始版本：** 9

<!--Device-HotspotConfig-band: int--><!--Device-HotspotConfig-band: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## channel

```TypeScript
channel?: number
```

热点的信道（2.4G：1~14,5G：7~196）。

**类型：** number

**起始版本：** 10

<!--Device-HotspotConfig-channel?: int--><!--Device-HotspotConfig-channel?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ipAddress

```TypeScript
ipAddress?: string
```

DHCP服务器的IP地址。

**类型：** string

**起始版本：** 10

<!--Device-HotspotConfig-ipAddress?: string--><!--Device-HotspotConfig-ipAddress?: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## maxConn

```TypeScript
maxConn: number
```

最大设备连接数。

**类型：** number

**起始版本：** 9

<!--Device-HotspotConfig-maxConn: int--><!--Device-HotspotConfig-maxConn: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## preSharedKey

```TypeScript
preSharedKey: string
```

热点的密钥。

**类型：** string

**起始版本：** 9

<!--Device-HotspotConfig-preSharedKey: string--><!--Device-HotspotConfig-preSharedKey: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型。

**类型：** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**起始版本：** 9

<!--Device-HotspotConfig-securityType: WifiSecurityType--><!--Device-HotspotConfig-securityType: WifiSecurityType-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ssid

```TypeScript
ssid: string
```

热点的SSID，编码格式为UTF-8。

**类型：** string

**起始版本：** 9

<!--Device-HotspotConfig-ssid: string--><!--Device-HotspotConfig-ssid: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。
