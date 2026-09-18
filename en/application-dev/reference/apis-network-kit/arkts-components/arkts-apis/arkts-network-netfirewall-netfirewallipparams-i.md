# NetFirewallIpParams

Defines the IP parameters of the firewall rule. The IP address type can be IPv4 or IPv6. A single IP address or IP address segment is supported.

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## address

```TypeScript
address?: string
```

IP address. This parameter is mandatory and valid only when type is set to **1**.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## endIp

```TypeScript
endIp?: string
```

End IP address. This parameter is mandatory and valid only when type is set to **2**. The value ranges from 0.0.0.1 to 255.255.255.254. Otherwise, this parameter will be ignored.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## family

```TypeScript
family?: number
```

**1**: IPv4.

**2**: IPv6.

The default value is **IPv4**. Other values are not supported currently.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## mask

```TypeScript
mask?: number
```

IPv4: subnet mask.

IPv6: address prefix.

This parameter is mandatory and valid only when type is set to **1**.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## startIp

```TypeScript
startIp?: string
```

Start IP address. This parameter is mandatory and valid only when type is set to **2**. The value ranges from 0.0.0.1 to 255.255.255.254. Otherwise, this parameter will be ignored.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## type

```TypeScript
type: number
```

**1**: IP address or subnet. In this case, the **address** and **mask** fields must be specified. When a single IP address is used, the **mask** field must be set to **32**.

**2**: IP address segment. In this case, the **startIp** and **endIp** fields must be specified.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
