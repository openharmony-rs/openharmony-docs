# InterfaceConfiguration（系统接口）

以太网连接配置网络信息。

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
import { ethernet } from '@kit.NetworkKit';
```

## dnsServers

```TypeScript
dnsServers: string
```

以太网连接配置dns服务地址，地址值范围：0-255.0-255.0-255.0-255（DHCP模式无需配置）多地址间用“,”隔开。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

## gateway

```TypeScript
gateway: string
```

以太网连接配置网关信息，地址值范围：0-255.0-255.0-255.0-255（DHCP模式无需配置）。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

## httpProxy

```TypeScript
httpProxy?: HttpProxy
```

以太网连接代理配置信息，默认情况下不配置任何代理信息。

**类型：** HttpProxy

**起始版本：** 10

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

## ipAddr

```TypeScript
ipAddr: string
```

以太网连接静态配置ip信息，地址值范围：0-255.0-255.0-255.0-255（DHCP模式无需配置）。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

## mode

```TypeScript
mode: IPSetMode
```

以太网连接配置模式。

**类型：** [IPSetMode](arkts-network-ethernet-ipsetmode-e-sys.md)

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

## netMask

```TypeScript
netMask: string
```

以太网连接配置子网掩码，地址值范围：0-255.0-255.0-255.0-255（DHCP模式无需配置）。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。

## route

```TypeScript
route: string
```

以太网连接静态配置路由信息，地址值范围：0-255.0-255.0-255.0-255（DHCP模式无需配置）。

**类型：** string

**起始版本：** 9

**系统能力：** SystemCapability.Communication.NetManager.Ethernet

**系统接口：** 此接口为系统接口。
