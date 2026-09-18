# WifiDeviceConfig

Wi-Fi配置信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

## 导入模块

```TypeScript
import { wifiManager } from '@kit.ConnectivityKit';
```

## configStatus

```TypeScript
configStatus?: number
```

返回当前网络是否允许参与选网。

1 - 允许参与选网，2 - 禁止参与

3 - 永久禁止参与，4 - 未知

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 12

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## creatorUid

```TypeScript
creatorUid?: number
```

创建用户的ID。

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## disableReason

```TypeScript
disableReason?: number
```

禁用原因：

-1 - 未知原因，0 - 未禁用，1 - 关联拒绝，2 - 认证失败

3 - DHCP失败，4 - 暂时无互联网连接

5 - 认证无凭据，6 - 永久无互联网连接

7 - 由WIFI管理器禁用，8 - 由于密码错误禁用

9 - 认证无订阅，10 - 私有EAP认证错误

11 - 未找到网络，12 - 连续失败

13 - 由系统禁用，14 - EAP-AKA认证失败

15 - 解除关联原因，16 - 禁用网络选择最大值

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## family

```TypeScript
family?: number
```

Static IP family: 0 - IPv4, 1 - Ipv6.

**类型：** number

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## ipType

```TypeScript
ipType?: IpType
```

IP地址类型。

**系统接口：** 此接口为系统接口。

**类型：** [IpType](arkts-connectivity-wifimanager-iptype-e-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isAutoConnectAllowed

```TypeScript
isAutoConnectAllowed?: boolean
```

是否允许自动连接。false:不允许，true:允许自动连接。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**起始版本：** 17

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## isSecureWifi

```TypeScript
isSecureWifi?: boolean
```

安全Wi-Fi检测。false:不是安全Wi-Fi，true:是安全Wi-Fi。

**系统接口：** 此接口为系统接口。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## proxyConfig

```TypeScript
proxyConfig?: WifiProxyConfig
```

代理配置。

**系统接口：** 此接口为系统接口。

**类型：** [WifiProxyConfig](arkts-connectivity-wifimanager-wifiproxyconfig-i-sys.md)

**起始版本：** 10

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## randomMacAddr

```TypeScript
randomMacAddr?: string
```

MAC地址。

**系统接口：** 此接口为系统接口。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## randomMacType

```TypeScript
randomMacType?: number
```

MAC地址类型。0 - 随机MAC地址，1 - 设备MAC地址

**系统接口：** 此接口为系统接口。

**类型：** number

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## staticIp

```TypeScript
staticIp?: IpConfig
```

静态IP配置信息。

**系统接口：** 此接口为系统接口。

**类型：** [IpConfig](arkts-connectivity-wifimanager-ipconfig-i-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。

## staticIpv6

```TypeScript
staticIpv6?: Ipv6Config
```

IPv6 config of static

**类型：** [Ipv6Config](arkts-connectivity-wifimanager-ipv6config-i-sys.md)

**起始版本：** 20

**系统能力：** SystemCapability.Communication.WiFi.STA

**系统接口：** 此接口为系统接口。
