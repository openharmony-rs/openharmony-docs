# SysVpnConfig (System API)

```TypeScript
export interface SysVpnConfig extends VpnConfig
```

Define configuration of the system VPN network.

**Inheritance/Implementation:** SysVpnConfig extends [VpnConfig](arkts-network-vpn-vpnconfig-i-sys.md)

**Since:** 12

<!--Device-vpn-export interface SysVpnConfig extends VpnConfig--><!--Device-vpn-export interface SysVpnConfig extends VpnConfig-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## forwardingRoutes

```TypeScript
forwardingRoutes?: string
```

The forwarding routes for the VPN network.

**Type:** string

**Since:** 12

<!--Device-SysVpnConfig-forwardingRoutes?: string--><!--Device-SysVpnConfig-forwardingRoutes?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## localAddresses

```TypeScript
localAddresses?: Array<LinkAddress>
```

The array of local addresses for VPN interface.

**Type:** Array&lt;[LinkAddress](arkts-network-vpn-linkaddress-t.md)&gt;

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

<!--Device-SysVpnConfig-localAddresses?: Array<LinkAddress>--><!--Device-SysVpnConfig-localAddresses?: Array<LinkAddress>-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## password

```TypeScript
password?: string
```

The user password for the VPN network.

**Type:** string

**Since:** 12

<!--Device-SysVpnConfig-password?: string--><!--Device-SysVpnConfig-password?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## pkcs12FileData

```TypeScript
pkcs12FileData?: Uint8Array
```

The p12 cert data for the ipsec VPN network.

**Type:** Uint8Array

**Since:** 20

<!--Device-SysVpnConfig-pkcs12FileData?: Uint8Array--><!--Device-SysVpnConfig-pkcs12FileData?: Uint8Array-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## pkcs12Password

```TypeScript
pkcs12Password?: string
```

The p12 cert password for the ipsec VPN network.

**Type:** string

**Since:** 20

<!--Device-SysVpnConfig-pkcs12Password?: string--><!--Device-SysVpnConfig-pkcs12Password?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## remoteAddresses

```TypeScript
remoteAddresses?: Array<string>
```

The array of addresses for remote server.

**Type:** Array&lt;string&gt;

**Since:** 20

<!--Device-SysVpnConfig-remoteAddresses?: Array<string>--><!--Device-SysVpnConfig-remoteAddresses?: Array<string>-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## saveLogin

```TypeScript
saveLogin?: boolean
```

Whether the VPN network save login name and password. The default value is false.

**Type:** boolean

**Since:** 12

<!--Device-SysVpnConfig-saveLogin?: boolean--><!--Device-SysVpnConfig-saveLogin?: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## userId

```TypeScript
userId?: number
```

The system user id for the VPN network.

**Type:** number

**Since:** 12

<!--Device-SysVpnConfig-userId?: int--><!--Device-SysVpnConfig-userId?: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## userName

```TypeScript
userName?: string
```

The user name for the VPN network.

**Type:** string

**Since:** 12

<!--Device-SysVpnConfig-userName?: string--><!--Device-SysVpnConfig-userName?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## vpnId

```TypeScript
vpnId?: string
```

The uuid for the VPN network.

**Type:** string

**Since:** 12

<!--Device-SysVpnConfig-vpnId?: string--><!--Device-SysVpnConfig-vpnId?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## vpnName

```TypeScript
vpnName?: string
```

The name for the VPN network.

**Type:** string

**Since:** 12

<!--Device-SysVpnConfig-vpnName?: string--><!--Device-SysVpnConfig-vpnName?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## vpnType

```TypeScript
vpnType?: SysVpnType
```

The type for the VPN network.

**Type:** [SysVpnType](arkts-network-vpn-sysvpntype-e-sys.md)

**Since:** 12

<!--Device-SysVpnConfig-vpnType?: SysVpnType--><!--Device-SysVpnConfig-vpnType?: SysVpnType-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.
