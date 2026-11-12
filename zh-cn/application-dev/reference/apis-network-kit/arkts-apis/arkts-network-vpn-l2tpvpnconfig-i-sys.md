# L2tpVpnConfig（系统接口）

```TypeScript
export interface L2tpVpnConfig extends SysVpnConfig
```

定义L2TP VPN网络的配置。

**继承/实现关系：** L2tpVpnConfig extends [SysVpnConfig](arkts-network-vpn-sysvpnconfig-i-sys.md)

**起始版本：** 12

<!--Device-vpn-export interface L2tpVpnConfig extends SysVpnConfig--><!--Device-vpn-export interface L2tpVpnConfig extends SysVpnConfig-End-->

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

L2TP VPN网络的CA证书配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecCaCertConfig?: string--><!--Device-L2tpVpnConfig-ipsecCaCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecCaCertFilePath

```TypeScript
ipsecCaCertFilePath?: string
```

L2TP VPN网络的CA证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecCaCertFilePath?: string--><!--Device-L2tpVpnConfig-ipsecCaCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecConfig

```TypeScript
ipsecConfig?: string
```

L2TP VPN网络的配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecConfig?: string--><!--Device-L2tpVpnConfig-ipsecConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecIdentifier

```TypeScript
ipsecIdentifier?: string
```

L2TP VPN网络的标识符。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecIdentifier?: string--><!--Device-L2tpVpnConfig-ipsecIdentifier?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPreSharedKey

```TypeScript
ipsecPreSharedKey?: string
```

L2TP VPN网络的预共享密钥。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPreSharedKey?: string--><!--Device-L2tpVpnConfig-ipsecPreSharedKey?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateServerCertConfig

```TypeScript
ipsecPrivateServerCertConfig?: string
```

L2TP VPN网络的服务端私钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPrivateServerCertConfig?: string--><!--Device-L2tpVpnConfig-ipsecPrivateServerCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateServerCertFilePath

```TypeScript
ipsecPrivateServerCertFilePath?: string
```

L2TP VPN网络的服务端私钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPrivateServerCertFilePath?: string--><!--Device-L2tpVpnConfig-ipsecPrivateServerCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateUserCertConfig

```TypeScript
ipsecPrivateUserCertConfig?: string
```

L2TP VPN网络的用户私钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPrivateUserCertConfig?: string--><!--Device-L2tpVpnConfig-ipsecPrivateUserCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPrivateUserCertFilePath

```TypeScript
ipsecPrivateUserCertFilePath?: string
```

L2TP VPN网络的用户私钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPrivateUserCertFilePath?: string--><!--Device-L2tpVpnConfig-ipsecPrivateUserCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicServerCertConfig

```TypeScript
ipsecPublicServerCertConfig?: string
```

L2TP VPN网络的服务端公钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPublicServerCertConfig?: string--><!--Device-L2tpVpnConfig-ipsecPublicServerCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicServerCertFilePath

```TypeScript
ipsecPublicServerCertFilePath?: string
```

L2TP VPN网络的服务端公钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPublicServerCertFilePath?: string--><!--Device-L2tpVpnConfig-ipsecPublicServerCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicUserCertConfig

```TypeScript
ipsecPublicUserCertConfig?: string
```

L2TP VPN网络的用户公钥证书配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPublicUserCertConfig?: string--><!--Device-L2tpVpnConfig-ipsecPublicUserCertConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecPublicUserCertFilePath

```TypeScript
ipsecPublicUserCertFilePath?: string
```

L2TP VPN网络的用户公钥证书文件路径。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecPublicUserCertFilePath?: string--><!--Device-L2tpVpnConfig-ipsecPublicUserCertFilePath?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## ipsecSecrets

```TypeScript
ipsecSecrets?: string
```

L2TP VPN网络的secrets文件。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-ipsecSecrets?: string--><!--Device-L2tpVpnConfig-ipsecSecrets?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## l2tpSharedKey

```TypeScript
l2tpSharedKey?: string
```

L2TP VPN网络的共享密钥。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-l2tpSharedKey?: string--><!--Device-L2tpVpnConfig-l2tpSharedKey?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## optionsL2tpdClient

```TypeScript
optionsL2tpdClient?: string
```

L2TP VPN网络的客户端配置项。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-optionsL2tpdClient?: string--><!--Device-L2tpVpnConfig-optionsL2tpdClient?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## strongSwanConfig

```TypeScript
strongSwanConfig?: string
```

L2TP VPN网络的strongSwan配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-strongSwanConfig?: string--><!--Device-L2tpVpnConfig-strongSwanConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。

## xl2tpdConfig

```TypeScript
xl2tpdConfig?: string
```

L2TP VPN网络的xl2tpd配置。

**类型：** string

**起始版本：** 12

<!--Device-L2tpVpnConfig-xl2tpdConfig?: string--><!--Device-L2tpVpnConfig-xl2tpdConfig?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.Vpn

**系统接口：** 此接口为系统接口。
