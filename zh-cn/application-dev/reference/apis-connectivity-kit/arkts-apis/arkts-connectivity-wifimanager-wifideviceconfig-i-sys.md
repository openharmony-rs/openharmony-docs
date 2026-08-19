# WifiDeviceConfig

WLAN设备配置信息。

**起始版本：** 23

<!--Device-wifiManager-interface WifiDeviceConfig--><!--Device-wifiManager-interface WifiDeviceConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
import { wifiManagerExt } from '@kit.ConnectivityKit';
```

## configStatus

```TypeScript
configStatus?: int
```

设备配置状态：0 - 使能，1 - 去使能，2 - 永久去使能，3 - 未知。

**类型：** int

**起始版本：** 23

<!--Device-WifiDeviceConfig-configStatus?: int--><!--Device-WifiDeviceConfig-configStatus?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## creatorUid

```TypeScript
creatorUid?: int
```

WLAN配置创建者的UID。

**类型：** int

**起始版本：** 23

<!--Device-WifiDeviceConfig-creatorUid?: int--><!--Device-WifiDeviceConfig-creatorUid?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## disableReason

```TypeScript
disableReason?: int
```

去使能原因

**类型：** int

**起始版本：** 23

<!--Device-WifiDeviceConfig-disableReason?: int--><!--Device-WifiDeviceConfig-disableReason?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## family

```TypeScript
family?: int
```

静态IP族：0 - IPv4，1 - Ipv6。

**类型：** int

**起始版本：** 23

<!--Device-WifiDeviceConfig-family?: int--><!--Device-WifiDeviceConfig-family?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## ipType

```TypeScript
ipType?: IpType
```

IP类型

**类型：** IpType

**起始版本：** 23

<!--Device-WifiDeviceConfig-ipType?: IpType--><!--Device-WifiDeviceConfig-ipType?: IpType-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isAutoConnectAllowed

```TypeScript
isAutoConnectAllowed?: boolean
```

是否允许自动连接配置：false - 不允许，true - 允许。

**类型：** boolean

**起始版本：** 23

<!--Device-WifiDeviceConfig-isAutoConnectAllowed?: boolean--><!--Device-WifiDeviceConfig-isAutoConnectAllowed?: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isSecureWifi

```TypeScript
isSecureWifi?: boolean
```

安全WLAN探测配置：false - 否，true - 是。

**类型：** boolean

**起始版本：** 23

<!--Device-WifiDeviceConfig-isSecureWifi?: boolean--><!--Device-WifiDeviceConfig-isSecureWifi?: boolean-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## proxyConfig

```TypeScript
proxyConfig?: WifiProxyConfig
```

代理配置。

**类型：** [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md)

**起始版本：** 23

<!--Device-WifiDeviceConfig-proxyConfig?: WifiProxyConfig--><!--Device-WifiDeviceConfig-proxyConfig?: WifiProxyConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

随机MAC地址，长度为6。

**类型：** string

**起始版本：** 23

<!--Device-WifiDeviceConfig-randomMacAddr?: string--><!--Device-WifiDeviceConfig-randomMacAddr?: string-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## randomMacType

```TypeScript
randomMacType?: int
```

随机MAC类型

**类型：** int

**起始版本：** 23

<!--Device-WifiDeviceConfig-randomMacType?: int--><!--Device-WifiDeviceConfig-randomMacType?: int-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## staticIp

```TypeScript
staticIp?: IpConfig
```

静态IP配置

**类型：** IpConfig

**起始版本：** 23

<!--Device-WifiDeviceConfig-staticIp?: IpConfig--><!--Device-WifiDeviceConfig-staticIp?: IpConfig-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## staticIpv6

```TypeScript
staticIpv6?: Ipv6Config
```

静态IPv6配置

**类型：** [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md)

**起始版本：** 23

<!--Device-WifiDeviceConfig-staticIpv6?: Ipv6Config--><!--Device-WifiDeviceConfig-staticIpv6?: Ipv6Config-End-->

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

