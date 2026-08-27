# HotspotConfig（系统接口）

WLAN热点配置信息。

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

WLAN热点的频段

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## channel

```TypeScript
channel?: number
```

WLAN热点的信道。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ipAddress

```TypeScript
ipAddress?: string
```

DHCP服务器的IP地址，为字符串形式，例如192.168.43.1

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## maxConn

```TypeScript
maxConn: number
```

WLAN热点允许的最大连接数

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## preSharedKey

```TypeScript
preSharedKey: string
```

WLAN热点的密码

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## securityType

```TypeScript
securityType: WifiSecurityType
```

WLAN热点的加密方式

**类型：** WifiSecurityType

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。

## ssid

```TypeScript
ssid: string
```

WLAN热点的SSID

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.AP.Core

**系统接口：** 此接口为系统接口。
