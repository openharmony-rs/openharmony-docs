# VpnConfig

三方VPN配置参数。

**起始版本：** 11

<!--Device-vpnExtension-export interface VpnConfig--><!--Device-vpnExtension-export interface VpnConfig-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## 导入模块

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## addresses

```TypeScript
addresses: Array<LinkAddress>
```

VPN虚拟网卡的IP地址。API version 23之前，最多支持64个IP地址；从API version 23开始，最多支持2000个IP地址。

**类型：** Array&lt;LinkAddress&gt;

**起始版本：** 11

<!--Device-VpnConfig-addresses: Array<LinkAddress>--><!--Device-VpnConfig-addresses: Array<LinkAddress>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## blockedApplications

```TypeScript
blockedApplications?: Array<string>
```

被阻止的应用信息列表，string类型表示的包名。当配置该列表后，该列表中的应用数据不会被VPN代理，其他应用可以根据routes配置被VPN代理。API version 23前最多可配置64个被阻止的应用包名；从API version 23开始最多可配置256个被阻止的应用包名。 **注意**：trustedApplications和blockedApplications列表不能同时配置。

**类型：** Array&lt;string&gt;

**起始版本：** 11

<!--Device-VpnConfig-blockedApplications?: Array<string>--><!--Device-VpnConfig-blockedApplications?: Array<string>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## dnsAddresses

```TypeScript
dnsAddresses?: Array<string>
```

DNS服务器地址信息。当配置DNS服务器地址后，VPN启动状态下被代理的应用上网时，使用配置的DNS服务器做DNS查询。

**类型：** Array&lt;string&gt;

**起始版本：** 11

<!--Device-VpnConfig-dnsAddresses?: Array<string>--><!--Device-VpnConfig-dnsAddresses?: Array<string>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isBlocking

```TypeScript
isBlocking?: boolean
```

是否阻塞模式。true表示阻塞模式，false表示非阻塞模式, 默认值为false。

**类型：** boolean

**起始版本：** 11

<!--Device-VpnConfig-isBlocking?: boolean--><!--Device-VpnConfig-isBlocking?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isIPv4Accepted

```TypeScript
isIPv4Accepted?: boolean
```

是否支持IPv4。true表示支持，false表示不支持, 默认值为true。 **注意**：若支持IPv4功能，需要在addresses中配置IPv4类型的IP地址。

**类型：** boolean

**起始版本：** 11

<!--Device-VpnConfig-isIPv4Accepted?: boolean--><!--Device-VpnConfig-isIPv4Accepted?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isIPv6Accepted

```TypeScript
isIPv6Accepted?: boolean
```

是否支持IPv6。true表示支持，false表示不支持, 默认值为false。 **注意**：若支持IPv6功能，需要在addresses中配置IPv6类型的IP地址。

**类型：** boolean

**起始版本：** 11

<!--Device-VpnConfig-isIPv6Accepted?: boolean--><!--Device-VpnConfig-isIPv6Accepted?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## isInternal

```TypeScript
isInternal?: boolean
```

是否支持内置VPN。true表示支持，false表示不支持, 默认值为false。

**类型：** boolean

**起始版本：** 11

<!--Device-VpnConfig-isInternal?: boolean--><!--Device-VpnConfig-isInternal?: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## mtu

```TypeScript
mtu?: int
```

最大传输单元MTU值（单位：字节）。取值范围：[576，1500]。

**类型：** int

**起始版本：** 11

<!--Device-VpnConfig-mtu?: int--><!--Device-VpnConfig-mtu?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## routes

```TypeScript
routes?: Array<RouteInfo>
```

VPN虚拟网卡的路由信息（API version 23前最多可配置1024条路由；从API version 23开始最多可配置10000条路由）。

**类型：** Array&lt;RouteInfo&gt;

**起始版本：** 11

<!--Device-VpnConfig-routes?: Array<RouteInfo>--><!--Device-VpnConfig-routes?: Array<RouteInfo>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## searchDomains

```TypeScript
searchDomains?: Array<string>
```

DNS的搜索域列表。

**类型：** Array&lt;string&gt;

**起始版本：** 11

<!--Device-VpnConfig-searchDomains?: Array<string>--><!--Device-VpnConfig-searchDomains?: Array<string>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## trustedApplications

```TypeScript
trustedApplications?: Array<string>
```

受信任的应用信息列表，string类型表示的包名。当配置该列表后，仅该列表中的应用数据才能根据routes被VPN代理。API version 23前最多可配置64个受信任的应用包名；从API version 23开始最多可配 置256个受信任的应用包名。 **注意**：trustedApplications和blockedApplications列表不能同时配置。

**类型：** Array&lt;string&gt;

**起始版本：** 11

<!--Device-VpnConfig-trustedApplications?: Array<string>--><!--Device-VpnConfig-trustedApplications?: Array<string>-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

## vpnId

```TypeScript
vpnId?: string
```

VPN唯一标识。

**类型：** string

**起始版本：** 20

<!--Device-VpnConfig-vpnId?: string--><!--Device-VpnConfig-vpnId?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

