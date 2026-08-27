# ConnectionProperties

网络连接信息。

> **注意：**
> 
> linkAddresses、routes和dnses可能为空，需要做好空值保护，建议使用前先判断对象是否存在。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## dnses

```TypeScript
dnses: Array<NetAddress>
```

网络地址，参考[NetAddress](arkts-network-connection-netaddress-i.md)。

**类型：** Array&lt;NetAddress&gt;

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## domains

```TypeScript
domains: string
```

域名。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## interfaceName

```TypeScript
interfaceName: string
```

网卡名称。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## isIPv4LinkValid

```TypeScript
isIPv4LinkValid?: boolean
```

当前网络的IPv4是否可用。true：当IPv4地址有效，且存在IPv4的默认路由时，认为IPv4可用；false：当IPv4地址无效，或者不存在IPv4的默认路由时，认为IPv4不可用。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## isIPv6LinkValid

```TypeScript
isIPv6LinkValid?: boolean
```

当前网络的IPv6是否可用。true：当IPv6地址有效，且存在IPv6的默认路由时，认为IPv6可用；false：当IPv6地址无效，或者不存在IPv6的默认路由时，认为IPv6不可用。

**类型：** boolean

**起始版本：** 24

**模型约束：** 此接口仅可在Stage模型下使用。

**系统能力：** SystemCapability.Communication.NetManager.Core

## linkAddresses

```TypeScript
linkAddresses: Array<LinkAddress>
```

链路信息。

**类型：** Array&lt;LinkAddress&gt;

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## mtu

```TypeScript
mtu: number
```

最大传输单元。

**类型：** number

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## routes

```TypeScript
routes: Array<RouteInfo>
```

路由信息。

**类型：** Array&lt;RouteInfo&gt;

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core
