# IpsecVpnConfig（系统接口）

```TypeScript
export interface IpsecVpnConfig extends SysVpnConfig
```

定义IPSec VPN网络的配置。

**继承/实现关系：** IpsecVpnConfig extends [SysVpnConfig](arkts-network-vpn-sysvpnconfig-i-sys.md)

**起始版本：** 12

<!--Device-vpn-export interface IpsecVpnConfig extends SysVpnConfig--><!--Device-vpn-export interface IpsecVpnConfig extends SysVpnConfig-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { vpn } from '@kit.NetworkKit';
```

## ipsecCaCertConfig

```TypeScript
ipsecCaCertConfig?: string
```

IPSec VPN网络的CA证书配置。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecCaCertConfig?: string--><!--Device-IpsecVpnConfig-ipsecCaCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecCaCertFilePath

```TypeScript
ipsecCaCertFilePath?: string
```

IPSec VPN网络的CA证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecCaCertFilePath?: string--><!--Device-IpsecVpnConfig-ipsecCaCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecIdentifier

```TypeScript
ipsecIdentifier?: string
```

IPSec VPN网络的标识符。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecIdentifier?: string--><!--Device-IpsecVpnConfig-ipsecIdentifier?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPreSharedKey

```TypeScript
ipsecPreSharedKey?: string
```

IPSec VPN网络的预共享密钥。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPreSharedKey?: string--><!--Device-IpsecVpnConfig-ipsecPreSharedKey?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateServerCertConfig

```TypeScript
ipsecPrivateServerCertConfig?: string
```

IPSec VPN网络的服务端私钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPrivateServerCertConfig?: string--><!--Device-IpsecVpnConfig-ipsecPrivateServerCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateServerCertFilePath

```TypeScript
ipsecPrivateServerCertFilePath?: string
```

IPSec VPN网络的服务端私钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPrivateServerCertFilePath?: string--><!--Device-IpsecVpnConfig-ipsecPrivateServerCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateUserCertConfig

```TypeScript
ipsecPrivateUserCertConfig?: string
```

IPSec VPN网络的用户私钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPrivateUserCertConfig?: string--><!--Device-IpsecVpnConfig-ipsecPrivateUserCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateUserCertFilePath

```TypeScript
ipsecPrivateUserCertFilePath?: string
```

IPSec VPN网络的用户私钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPrivateUserCertFilePath?: string--><!--Device-IpsecVpnConfig-ipsecPrivateUserCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicServerCertConfig

```TypeScript
ipsecPublicServerCertConfig?: string
```

IPSec VPN网络的服务端公钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPublicServerCertConfig?: string--><!--Device-IpsecVpnConfig-ipsecPublicServerCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicServerCertFilePath

```TypeScript
ipsecPublicServerCertFilePath?: string
```

IPSec VPN网络的服务端公钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPublicServerCertFilePath?: string--><!--Device-IpsecVpnConfig-ipsecPublicServerCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicUserCertConfig

```TypeScript
ipsecPublicUserCertConfig?: string
```

IPSec VPN网络的用户公钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPublicUserCertConfig?: string--><!--Device-IpsecVpnConfig-ipsecPublicUserCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicUserCertFilePath

```TypeScript
ipsecPublicUserCertFilePath?: string
```

IPSec VPN网络的用户公钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-ipsecPublicUserCertFilePath?: string--><!--Device-IpsecVpnConfig-ipsecPublicUserCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## strongSwanConfig

```TypeScript
strongSwanConfig?: string
```

IPSec VPN网络的strongSwan配置。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-strongSwanConfig?: string--><!--Device-IpsecVpnConfig-strongSwanConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## swanctlConfig

```TypeScript
swanctlConfig?: string
```

IPSec VPN网络的swanctl配置。

**类型：** string

**起始版本：** 12

<!--Device-IpsecVpnConfig-swanctlConfig?: string--><!--Device-IpsecVpnConfig-swanctlConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。
