# ConnectionProperties

```TypeScript
export interface ConnectionProperties
```

Defines the network connection properties.

> **NOTE:** 
> 
> The values of **linkAddresses**, **routes**, and **dnses** may be empty. You need to protect the empty values.
> You are advised to check whether the objects exist before using the values.

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## Modules to Import

```TypeScript
import { connection } from '@kit.NetworkKit';
```

## dnses

```TypeScript
dnses: Array<NetAddress>
```

Network address. For details, see [NetAddress](arkts-network-connection-netaddress-i.md).

**Type:** Array&lt;[NetAddress](arkts-network-connection-netaddress-i.md)&gt;

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## domains

```TypeScript
domains: string
```

Domain name.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## interfaceName

```TypeScript
interfaceName: string
```

Network interface card (NIC) name.

**Type:** string

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## isIPv4LinkValid

```TypeScript
isIPv4LinkValid?: boolean
```

Whether IPv4 is available on the current network. **true**: IPv4 is available when the IPv4 address is valid and the default IPv4 route exists. **false**: IPv4 is unavailable when the IPv4 address is invalid or the default IPv 4 route does not exist.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## isIPv6LinkValid

```TypeScript
isIPv6LinkValid?: boolean
```

Whether IPv6 is available on the current network. **true**: IPv6 is available when the IPv6 address is valid and the default IPv6 route exists. **false**: IPv6 is unavailable when the IPv6 address is invalid or the default IPv 6 route does not exist.

**Type:** boolean

**Since:** 24

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.Core

## linkAddresses

```TypeScript
linkAddresses: Array<LinkAddress>
```

Network link information.

**Type:** Array&lt;[LinkAddress](arkts-network-connection-linkaddress-i.md)&gt;

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## mtu

```TypeScript
mtu: number
```

Maximum transmission unit (MTU).

**Type:** number

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core

## routes

```TypeScript
routes: Array<RouteInfo>
```

Network route information.

**Type:** Array&lt;[RouteInfo](arkts-network-connection-routeinfo-i.md)&gt;

**Since:** 8

**System capability:** SystemCapability.Communication.NetManager.Core
