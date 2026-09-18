# VpnConfig

Defines the VPN configuration.

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## Modules to Import

```TypeScript
import { vpnExtension } from '@kit.NetworkKit';
```

## addresses

```TypeScript
addresses: Array<LinkAddress>
```

IP addresses of vNICs. Before API version 23, a maximum of 64 IP addresses are supported. Starting from API version 23, a maximum of 2000 IP addresses are supported.

**Type:** Array&lt;[LinkAddress](arkts-network-vpnextension-linkaddress-t.md)&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## blockedApplications

```TypeScript
blockedApplications?: Array<string>
```

List of blocked applications, which are represented by bundle names of the string type. After such a list is configured, only applications that are not in the list can be proxied by the VPN according to the specified **routes**. Before API version 23, a maximum of 64 blocked application bundle names can be configured. Since API version 23, a maximum of 256 blocked application bundle names can be configured.

**Note:**  Configure either **trustedApplications** or **blockedApplications** as they are mutually exclusive.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## dnsAddresses

```TypeScript
dnsAddresses?: Array<string>
```

IP address of the DNS server. After the IP address is configured, when the VPN is active and proxy-enabled applications access the Internet, the configured DNS server will be used for DNS queries.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## isBlocking

```TypeScript
isBlocking?: boolean
```

Whether the blocking mode is used. The value **true** indicates that the blocking mode is used, and the value **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## isInternal

```TypeScript
isInternal?: boolean
```

Whether the built-in VPN is supported. The value **true** indicates that the built-in VPN is supported, and the value **false** indicates the opposite. The default value is **false**.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## isIPv4Accepted

```TypeScript
isIPv4Accepted?: boolean
```

Whether IPv4 is supported. The value **true** indicates that the IPv4 is supported, and the value **false** indicates the opposite. The default value is **true**.

Note: If the IPv4 is supported, you need to configure IPv4 addresses in **addresses**.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## isIPv6Accepted

```TypeScript
isIPv6Accepted?: boolean
```

Whether IPv6 is supported. The value **true** indicates that the IPV6 is supported, and the value **false** indicates the opposite. The default value is **false**.

Note: If the IPv6 is supported, you need to configure IPv6 addresses in **addresses**.

**Type:** boolean

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## mtu

```TypeScript
mtu?: number
```

Maximum transmission unit (MTU), in bytes. The value range is [576,1500].

**Type:** number

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## routes

```TypeScript
routes?: Array<RouteInfo>
```

Route information of the vNIC. Before API version 23, a maximum of 1024 routes can be configured. Starting from API version 23, a maximum of 10,000 routes can be configured.

**Type:** Array&lt;[RouteInfo](arkts-network-vpnextension-routeinfo-t.md)&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## searchDomains

```TypeScript
searchDomains?: Array<string>
```

List of DNS search domains.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## trustedApplications

```TypeScript
trustedApplications?: Array<string>
```

List of trusted applications, which are represented by bundle names of the string type. After such a list is configured, only the applications in the list can be proxied by the VPN according to the specified **routes**. Before API version 23, a maximum of 64 trusted application bundle names can be configured. Since API version 23, a maximum of 256 trusted application bundle names can be configured.

**Note:**  Configure either **trustedApplications** or **blockedApplications** as they are mutually exclusive.

**Type:** Array&lt;string&gt;

**Since:** 11

**System capability:** SystemCapability.Communication.NetManager.Vpn

## vpnId

```TypeScript
vpnId?: string
```

Unique VPN ID.

**Type:** string

**Since:** 20

**System capability:** SystemCapability.Communication.NetManager.Vpn
