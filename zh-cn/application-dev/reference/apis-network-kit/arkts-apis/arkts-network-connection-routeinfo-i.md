# RouteInfo

网络路由信息。

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## 导入模块

```TypeScript
```

## destination

```TypeScript
destination: LinkAddress
```

目的地址。

**类型：** LinkAddress

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## gateway

```TypeScript
gateway: NetAddress
```

网关地址。

**类型：** NetAddress

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## hasGateway

```TypeScript
hasGateway: boolean
```

是否有网关。true：有网关；false：无网关。

**类型：** boolean

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## interface

```TypeScript
interface: string
```

网卡名称。

**类型：** string

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## isDefaultRoute

```TypeScript
isDefaultRoute: boolean
```

是否为默认路由。true：默认路由；false：非默认路由。  
**说明：** IPv4默认路由是指目的地址为0.0.0.0/0的路由；IPv6默认路由是指目的地址为::/0的路由。

**类型：** boolean

**起始版本：** 8

**系统能力：** SystemCapability.Communication.NetManager.Core

## isExcludedRoute

```TypeScript
isExcludedRoute?: boolean
```

是否为排除路由。true表示排除路由，false表示非排除路由，默认值为false。

**类型：** boolean

**起始版本：** 20

**系统能力：** SystemCapability.Communication.NetManager.Core
