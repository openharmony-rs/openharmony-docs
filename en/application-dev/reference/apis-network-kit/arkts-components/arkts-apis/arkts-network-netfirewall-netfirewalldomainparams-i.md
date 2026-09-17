# NetFirewallDomainParams

Defines domain name parameters of a firewall rule. Currently, Chinese domain names are not supported.

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## domain

```TypeScript
domain: string
```

If **isWildcard** is set to **false**, the complete domain name, for example, "www.example.cn", needs to be specified.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## isWildcard

```TypeScript
isWildcard: boolean
```

Whether to contain wildcards. The value **true** means to contain wildcards; and the value **false** means the opposite.

**Type:** boolean

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
