# HotspotConfig（系统接口）

热点配置信息。

**起始版本：** 9

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

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## channel

```TypeScript
channel?: number
```

热点的信道（2.4G：1~14,5G：7~196）。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ipAddress

```TypeScript
ipAddress?: string
```

DHCP服务器的IP地址。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## maxConn

```TypeScript
maxConn: number
```

最大设备连接数。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## preSharedKey

```TypeScript
preSharedKey: string
```

热点的密钥。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## securityType

```TypeScript
securityType: WifiSecurityType
```

加密类型。

**类型：** [WifiSecurityType](arkts-connectivity-wifimanager-wifisecuritytype-e.md)

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ssid

```TypeScript
ssid: string
```

热点的SSID，编码格式为UTF-8。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。
