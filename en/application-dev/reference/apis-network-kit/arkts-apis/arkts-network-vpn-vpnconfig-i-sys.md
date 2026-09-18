# VpnConfig (System API)

Defines the VPN configuration.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## addresses

```TypeScript
addresses: Array<LinkAddress>
```

IP address of the vNIC.

**Type:** Array&lt;[LinkAddress](arkts-network-vpn-linkaddress-t.md)&gt;

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## blockedApplications

```TypeScript
blockedApplications?: Array<string>
```

Used to specify that the bundle name of the string type cannot access the VPN network.

**Type:** Array&lt;string&gt;

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## dnsAddresses

```TypeScript
dnsAddresses?: Array<string>
```

IP address of the DNS server.

**Type:** Array&lt;string&gt;

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## isBlocking

```TypeScript
isBlocking?: boolean
```

Whether the blocking mode is used. The value **true** indicates that the blocking mode is used, and the value **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## isIPv4Accepted

```TypeScript
isIPv4Accepted?: boolean
```

Whether IPv4 is supported. The value **true** indicates that IPv4 is supported, and the value **false** indicates the opposite. Default value: **true**.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## isIPv6Accepted

```TypeScript
isIPv6Accepted?: boolean
```

Whether IPv6 is supported. The value **true** indicates that IPv6 is supported, and the value **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## isLegacy

```TypeScript
isLegacy?: boolean
```

Whether the built-in VPN is supported. The value **true** indicates that the built-in VPN is supported, and the value **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## mtu

```TypeScript
mtu?: number
```

Maximum transmission unit (MTU), in bytes.

**Type:** number

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## routes

```TypeScript
routes?: Array<RouteInfo>
```

Route information of the vNIC.

**Type:** Array&lt;[RouteInfo](arkts-network-vpn-routeinfo-t.md)&gt;

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## searchDomains

```TypeScript
searchDomains?: Array<string>
```

List of DNS search domains.

**Type:** Array&lt;string&gt;

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## trustedApplications

```TypeScript
trustedApplications?: Array<string>
```

Used to specify that the bundle name of the string type can access the VPN network.

**Type:** Array&lt;string&gt;

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## vpnId

```TypeScript
vpnId?: string
```

Unique VPN ID.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.
