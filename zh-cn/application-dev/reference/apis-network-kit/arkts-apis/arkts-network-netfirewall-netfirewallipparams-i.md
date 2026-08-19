# NetFirewallIpParams(网络防火墙)

防火墙规则的IP参数，IP类型包括IPv4、IPv6，支持单个IP或IP段。

**起始版本：** 15

<!--Device-netFirewall-interface NetFirewallIpParams--><!--Device-netFirewall-interface NetFirewallIpParams-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## address

```TypeScript
address?: string
```

IP地址。当type等于1时需要设置，并且仅在type等于1时有效，否则将被忽略。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallIpParams-address?: string--><!--Device-NetFirewallIpParams-address?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## endIp

```TypeScript
endIp?: string
```

结束IP。当type等于2时需要设置，并且仅在type等于2时有效，范围从0.0.0.1到255.255.255.254，否则将被忽略。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallIpParams-endIp?: string--><!--Device-NetFirewallIpParams-endIp?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## family

```TypeScript
family?: int
```

1：表示family地址族设置为IPv4。 2：表示family地址族设置为IPv6。 默认IPv4，其他当前不支持。

**类型：** int

**起始版本：** 15

<!--Device-NetFirewallIpParams-family?: int--><!--Device-NetFirewallIpParams-family?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## mask

```TypeScript
mask?: int
```

IPv4：子网掩码。 IPv6：前缀。 当type等于1时需要设置，并且仅在type等于1时有效，否则将被忽略。

**类型：** int

**起始版本：** 15

<!--Device-NetFirewallIpParams-mask?: int--><!--Device-NetFirewallIpParams-mask?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## startIp

```TypeScript
startIp?: string
```

起始IP。当type等于2时需要设置，并且仅在type等于2时有效，范围从0.0.0.1到255.255.255.254，否则将被忽略。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallIpParams-startIp?: string--><!--Device-NetFirewallIpParams-startIp?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## type

```TypeScript
type: int
```

1：IP地址或子网。该场景下必须指定address和mask字段，当使用单个IP时，mask字段需设置为32。 2：IP段，该场景下必须指定startIp和endIp字段。

**类型：** int

**起始版本：** 15

<!--Device-NetFirewallIpParams-type: int--><!--Device-NetFirewallIpParams-type: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

