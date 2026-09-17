# NetFirewallIpParams

防火墙规则的IP参数，IP类型包括IPv4、IPv6，支持单个IP或IP段。

**起始版本：** 15

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

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## endIp

```TypeScript
endIp?: string
```

结束IP。当type等于2时需要设置，并且仅在type等于2时有效，范围从0.0.0.1到255.255.255.254，否则将被忽略。

**类型：** string

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## family

```TypeScript
family?: number
```

1：表示family地址族设置为IPv4。

2：表示family地址族设置为IPv6。

默认IPv4，其他当前不支持。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## mask

```TypeScript
mask?: number
```

IPv4：子网掩码。

IPv6：前缀。

当type等于1时需要设置，并且仅在type等于1时有效，否则将被忽略。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## startIp

```TypeScript
startIp?: string
```

起始IP。当type等于2时需要设置，并且仅在type等于2时有效，范围从0.0.0.1到255.255.255.254，否则将被忽略。

**类型：** string

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## type

```TypeScript
type: number
```

1：IP地址或子网。该场景下必须指定address和mask字段，当使用单个IP时，mask字段需设置为32。

2：IP段，该场景下必须指定startIp和endIp字段。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall
