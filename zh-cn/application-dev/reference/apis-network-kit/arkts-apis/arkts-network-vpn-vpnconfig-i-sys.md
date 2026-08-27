# VpnConfig（系统接口）

VPN 配置参数。

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## addresses

```TypeScript
addresses: Array<LinkAddress>
```

VPN虚拟网卡的 IP 地址。

**类型：** Array&lt;LinkAddress&gt;

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## blockedApplications

```TypeScript
blockedApplications?: Array<string>
```

string类型表示的包名不能接入VPN网络。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## dnsAddresses

```TypeScript
dnsAddresses?: Array<string>
```

DNS服务器地址信息。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## isBlocking

```TypeScript
isBlocking?: boolean
```

是否阻塞模式。true表示是阻塞模式，false表示不是阻塞模式。默认值为false。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## isIPv4Accepted

```TypeScript
isIPv4Accepted?: boolean
```

是否支持IPv4。true表示支持IPv4，false表示不支持IPv4。默认值为true。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## isIPv6Accepted

```TypeScript
isIPv6Accepted?: boolean
```

是否支持IPv6。true表示支持IPv6，false表示不支持IPv6。默认值为false。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## isLegacy

```TypeScript
isLegacy?: boolean
```

是否支持内置VPN。true表示支持内置VPN，false表示不支持内置VPN。默认值为false。

**类型：** boolean

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## mtu

```TypeScript
mtu?: number
```

最大传输单元MTU值(单位:字节)。

**类型：** number

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## routes

```TypeScript
routes?: Array<RouteInfo>
```

VPN虚拟网卡的路由信息。

**类型：** Array&lt;RouteInfo&gt;

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## searchDomains

```TypeScript
searchDomains?: Array<string>
```

DNS 的搜索域列表。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## trustedApplications

```TypeScript
trustedApplications?: Array<string>
```

string类型表示的包名可以接入VPN网络。

**类型：** Array&lt;string&gt;

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## vpnId

```TypeScript
vpnId?: string
```

VPN唯一标识。

**类型：** string

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。
