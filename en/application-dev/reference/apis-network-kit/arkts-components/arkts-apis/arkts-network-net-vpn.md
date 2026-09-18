# @ohos.net.vpn(VPN Management)

This module is the built-in VPN function provided by the OS. It allows users to set up VPN connections through the network settings of the OS. Generally, this module provides only limited functions and is subject to strict restrictions.

**Since:** 10

**System capability:** SystemCapability.Communication.NetManager.Vpn

## Modules to Import

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [addSysVpnConfig](arkts-network-vpn-addsysvpnconfig-f-sys.md) | Add a system VPN network configuration. |
| [createVpnConnection](arkts-network-vpn-createvpnconnection-f-sys.md) | Creates a VPN connection. |
| [deleteSysVpnConfig](arkts-network-vpn-deletesysvpnconfig-f-sys.md) | Delete the configuration of system VPN network by the specified vpnId. |
| [getConnectedSysVpnConfig](arkts-network-vpn-getconnectedsysvpnconfig-f-sys.md) | Get the connected VPN network configuration. |
| [getConnectedVpnAppInfo](arkts-network-vpn-getconnectedvpnappinfo-f-sys.md) | Get the connected VPN App Info. |
| [getSysVpnConfig](arkts-network-vpn-getsysvpnconfig-f-sys.md) | Get the configuration of system VPN network by the specified vpnId. |
| [getSysVpnConfigList](arkts-network-vpn-getsysvpnconfiglist-f-sys.md) | Get all system VPN network configuration. |
| [off](arkts-network-vpn-off-f-sys.md#offconnect) | Unsubscribes from vpn connect state changes. |
| [off](arkts-network-vpn-off-f-sys.md#offconnectmulti) | Unsubscribes from vpn connect state changes. |
| [on](arkts-network-vpn-on-f-sys.md#onconnect) | Subscribes to vpn connect state changes. |
| [on](arkts-network-vpn-on-f-sys.md#onconnectmulti) | Subscribes to vpn connect state changes. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [IpsecVpnConfig](arkts-network-vpn-ipsecvpnconfig-i-sys.md) | Define configuration of the ipsec VPN network. |
| [L2tpVpnConfig](arkts-network-vpn-l2tpvpnconfig-i-sys.md) | Define configuration of the l2tp VPN network. |
| [OpenVpnConfig](arkts-network-vpn-openvpnconfig-i-sys.md) | Define configuration of the open VPN network. |
| [SysVpnConfig](arkts-network-vpn-sysvpnconfig-i-sys.md) | Define configuration of the system VPN network. |
| [VpnConfig](arkts-network-vpn-vpnconfig-i-sys.md) | Defines the VPN configuration. |
| [VpnConnection](arkts-network-vpn-vpnconnection-i-sys.md) | Defines a VPN connection object. Before calling **VpnConnection** APIs, you need to create a VPN connection object by calling [vpn.createVpnConnection](arkts-network-vpn-createvpnconnection-f-sys.md). |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [SysVpnType](arkts-network-vpn-sysvpntype-e-sys.md) | Defines the type for the VPN network. |
<!--DelEnd-->

### Types

| Name | Description |
| --- | --- |
| [AbilityContext](arkts-network-vpn-abilitycontext-t.md) | The context of an ability. It allows access to ability-specific resources. |
| [LinkAddress](arkts-network-vpn-linkaddress-t.md) | Defines the network link address information. |
| [RouteInfo](arkts-network-vpn-routeinfo-t.md) | Defines the network route information. |
