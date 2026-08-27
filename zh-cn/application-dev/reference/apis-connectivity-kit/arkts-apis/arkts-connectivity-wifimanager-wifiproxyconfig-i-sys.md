# WifiProxyConfig（系统接口）

WLAN代理配置。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## exclusionObjects

```TypeScript
exclusionObjects?: string
```

手动配置代理的排除对象。对象之间用','分隔。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## pacWebAddress

```TypeScript
pacWebAddress?: string
```

自动配置代理的PAC网址。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## proxyMethod

```TypeScript
proxyMethod?: ProxyMethod
```

WLAN代理方式

**类型：** [ProxyMethod](arkts-connectivity-wifimanager-proxymethod-e-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## serverHostName

```TypeScript
serverHostName?: string
```

手动配置代理的服务器主机名。

**类型：** string

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## serverPort

```TypeScript
serverPort?: number
```

手动配置代理的服务器端口。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。
