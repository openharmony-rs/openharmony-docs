# WifiDeviceConfig

WLAN设备配置信息。

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## configStatus

```TypeScript
configStatus?: number
```

设备配置状态：0 - 使能，1 - 去使能，2 - 永久去使能，3 - 未知。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## creatorUid

```TypeScript
creatorUid?: number
```

WLAN配置创建者的UID。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## disableReason

```TypeScript
disableReason?: number
```

去使能原因

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## family

```TypeScript
family?: number
```

静态IP族：0 - IPv4，1 - Ipv6。

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## ipType

```TypeScript
ipType?: IpType
```

IP类型

**类型：** IpType

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isAutoConnectAllowed

```TypeScript
isAutoConnectAllowed?: boolean
```

是否允许自动连接配置：false - 不允许，true - 允许。

**类型：** boolean

**起始版本：** 17

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isSecureWifi

```TypeScript
isSecureWifi?: boolean
```

安全WLAN探测配置：false - 否，true - 是。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## netId

```TypeScript
netId?: number
```

分配的networkId

**类型：** number

**起始版本：** 22

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## proxyConfig

```TypeScript
proxyConfig?: WifiProxyConfig
```

代理配置。

**类型：** [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

随机MAC地址，长度为6。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## randomMacType

```TypeScript
randomMacType?: number
```

随机MAC类型

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## staticIp

```TypeScript
staticIp?: IpConfig
```

静态IP配置

**类型：** IpConfig

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## staticIpv6

```TypeScript
staticIpv6?: Ipv6Config
```

静态IPv6配置

**类型：** [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md)

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。
