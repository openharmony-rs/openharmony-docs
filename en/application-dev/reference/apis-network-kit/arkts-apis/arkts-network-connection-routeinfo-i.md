# RouteInfo

Defines network route information.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## destination

```TypeScript
destination: LinkAddress
```

Destination address.

**Type:** [LinkAddress](arkts-network-connection-linkaddress-i.md)

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## gateway

```TypeScript
gateway: NetAddress
```

Gateway address.

**Type:** [NetAddress](arkts-network-connection-netaddress-i.md)

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## hasGateway

```TypeScript
hasGateway: boolean
```

Whether a gateway is present. Whether a gateway is available. The value **true** indicates that a gateway is available, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## interface

```TypeScript
interface: string
```

NIC name.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## isDefaultRoute

```TypeScript
isDefaultRoute: boolean
```

Whether the route is the default one. Whether the route is the default route. The value **true** indicates that the route is the default route, and the value **false** indicates the opposite.

Note: The IPv4 default route refers to the route whose destination address is **0.0.0.0/0**. The IPv6 default route refers to the route whose destination address is **::/0**.

**Type:** boolean

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## isExcludedRoute

```TypeScript
isExcludedRoute?: boolean
```

Whether the route is excluded. The value **true** indicates that the route is excluded, and the value **false** indicates the opposite.

**Type:** boolean

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Core
