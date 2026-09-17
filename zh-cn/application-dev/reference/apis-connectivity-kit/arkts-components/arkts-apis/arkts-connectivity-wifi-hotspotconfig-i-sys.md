# HotspotConfig（系统接口）

热点配置信息。

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [HotspotConfig](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md)

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifi } from '@kit.ConnectivityKit';
```

## band

```TypeScript
band: number
```

热点的带宽。1: 2.4G, 2: 5G, 3: 双模频段

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [band](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#band)

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## maxConn

```TypeScript
maxConn: number
```

最大设备连接数。

**类型：** number

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [maxConn](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#maxconn)

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## preSharedKey

```TypeScript
preSharedKey: string
```

热点的密钥。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [preSharedKey](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#presharedkey)

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型。

**类型：** [WifiSecurityType](arkts-connectivity-wifi-wifisecuritytype-e.md)

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [securityType](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#securitytype)

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ssid

```TypeScript
ssid: string
```

热点的SSID，编码格式为UTF-8。

**类型：** string

**起始版本：** 7

**废弃版本：** 9

**替代接口：** [ssid](arkts-connectivity-wifimanager-hotspotconfig-i-sys.md#ssid)

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。
