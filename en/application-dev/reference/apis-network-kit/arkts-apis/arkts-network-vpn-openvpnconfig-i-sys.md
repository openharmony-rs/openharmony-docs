# OpenVpnConfig (System API)

```TypeScript
export interface OpenVpnConfig extends SysVpnConfig
```

Define configuration of the open VPN network.

**Inheritance/Implementation:** OpenVpnConfig extends [SysVpnConfig](arkts-network-vpn-sysvpnconfig-i-sys.md)

**Since:** 12

<!--Device-vpn-export interface OpenVpnConfig extends SysVpnConfig--><!--Device-vpn-export interface OpenVpnConfig extends SysVpnConfig-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## Modules to Import

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## askpass

```TypeScript
askpass?: string
```

The ask pass for the openvpn VPN network.

**Type:** string

**Since:** 12

<!--Device-OpenVpnConfig-askpass?: string--><!--Device-OpenVpnConfig-askpass?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnAuthType

```TypeScript
ovpnAuthType?: number
```

The auth type for the openvpn VPN network.

**Type:** number

**Since:** 12

<!--Device-OpenVpnConfig-ovpnAuthType?: int--><!--Device-OpenVpnConfig-ovpnAuthType?: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnCaCertFilePath

```TypeScript
ovpnCaCertFilePath?: string
```

The ca cert file path for the openvpn VPN network.

**Type:** string

**Since:** 12

<!--Device-OpenVpnConfig-ovpnCaCertFilePath?: string--><!--Device-OpenVpnConfig-ovpnCaCertFilePath?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnConfig

```TypeScript
ovpnConfig?: string
```

The config for the openvpn VPN network.

**Type:** string

**Since:** 12

<!--Device-OpenVpnConfig-ovpnConfig?: string--><!--Device-OpenVpnConfig-ovpnConfig?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnConfigFilePath

```TypeScript
ovpnConfigFilePath?: string
```

The config file path for the openvpn VPN network.

**Type:** string

**Since:** 12

<!--Device-OpenVpnConfig-ovpnConfigFilePath?: string--><!--Device-OpenVpnConfig-ovpnConfigFilePath?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnPort

```TypeScript
ovpnPort?: string
```

The port for the openvpn VPN network.

**Type:** string

**Since:** 12

<!--Device-OpenVpnConfig-ovpnPort?: string--><!--Device-OpenVpnConfig-ovpnPort?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnPrivateKeyFilePath

```TypeScript
ovpnPrivateKeyFilePath?: string
```

The private key file path for the openvpn VPN network.

**Type:** string

**Since:** 12

<!--Device-OpenVpnConfig-ovpnPrivateKeyFilePath?: string--><!--Device-OpenVpnConfig-ovpnPrivateKeyFilePath?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnProtocol

```TypeScript
ovpnProtocol?: number
```

The protocol for the openvpn VPN network.

**Type:** number

**Since:** 12

<!--Device-OpenVpnConfig-ovpnProtocol?: int--><!--Device-OpenVpnConfig-ovpnProtocol?: int-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.

## ovpnUserCertFilePath

```TypeScript
ovpnUserCertFilePath?: string
```

The user cert file path for the openvpn VPN network.

**Type:** string

**Since:** 12

<!--Device-OpenVpnConfig-ovpnUserCertFilePath?: string--><!--Device-OpenVpnConfig-ovpnUserCertFilePath?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.Vpn

**System API:** This is a system API.
