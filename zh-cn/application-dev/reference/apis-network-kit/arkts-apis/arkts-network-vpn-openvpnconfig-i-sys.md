# OpenVpnConfig（系统接口）

```TypeScript
export interface OpenVpnConfig extends SysVpnConfig
```

定义开放VPN网络的配置。

**继承/实现关系：** OpenVpnConfig extends [SysVpnConfig](arkts-network-vpn-sysvpnconfig-i-sys.md)

**起始版本：** 12

<!--Device-vpn-export interface OpenVpnConfig extends SysVpnConfig--><!--Device-vpn-export interface OpenVpnConfig extends SysVpnConfig-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## askpass

```TypeScript
askpass?: string
```

OpenVPN网络的askpass文件。

**类型：** string

**起始版本：** 12

<!--Device-OpenVpnConfig-askpass?: string--><!--Device-OpenVpnConfig-askpass?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnAuthType

```TypeScript
ovpnAuthType?: number
```

OpenVPN网络的认证类型。

**类型：** number

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnAuthType?: int--><!--Device-OpenVpnConfig-ovpnAuthType?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnCaCertFilePath

```TypeScript
ovpnCaCertFilePath?: string
```

OpenVPN网络的CA证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnCaCertFilePath?: string--><!--Device-OpenVpnConfig-ovpnCaCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnConfig

```TypeScript
ovpnConfig?: string
```

OpenVPN网络的配置。

**类型：** string

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnConfig?: string--><!--Device-OpenVpnConfig-ovpnConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnConfigFilePath

```TypeScript
ovpnConfigFilePath?: string
```

OpenVPN网络的配置文件路径。

**类型：** string

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnConfigFilePath?: string--><!--Device-OpenVpnConfig-ovpnConfigFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnPort

```TypeScript
ovpnPort?: string
```

OpenVPN网络的端口。

**类型：** string

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnPort?: string--><!--Device-OpenVpnConfig-ovpnPort?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnPrivateKeyFilePath

```TypeScript
ovpnPrivateKeyFilePath?: string
```

OpenVPN网络的私钥文件路径。

**类型：** string

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnPrivateKeyFilePath?: string--><!--Device-OpenVpnConfig-ovpnPrivateKeyFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnProtocol

```TypeScript
ovpnProtocol?: number
```

OpenVPN网络的协议。

**类型：** number

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnProtocol?: int--><!--Device-OpenVpnConfig-ovpnProtocol?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ovpnUserCertFilePath

```TypeScript
ovpnUserCertFilePath?: string
```

OpenVPN网络的用户证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-OpenVpnConfig-ovpnUserCertFilePath?: string--><!--Device-OpenVpnConfig-ovpnUserCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。
