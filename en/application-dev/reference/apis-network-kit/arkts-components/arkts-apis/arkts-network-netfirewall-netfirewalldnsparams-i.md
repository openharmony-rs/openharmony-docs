# NetFirewallDnsParams

```TypeScript
interface NetFirewallDnsParams
```

Defines the DNS information of a firewall rule.

> **Description**
> 
> This parameter cannot be empty when **rule.type** of [addNetFirewallRule](arkts-network-netfirewall-addnetfirewallrule-f.md)
> is set to RULE_DNS.

**Since:** 15

<!--Device-netFirewall-interface NetFirewallDnsParams--><!--Device-netFirewall-interface NetFirewallDnsParams-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## primaryDns

```TypeScript
primaryDns: string
```

Active DNS server.

**Type:** string

**Since:** 15

<!--Device-NetFirewallDnsParams-primaryDns: string--><!--Device-NetFirewallDnsParams-primaryDns: string-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## standbyDns

```TypeScript
standbyDns?: string
```

Standby DNS server.

**Type:** string

**Since:** 15

<!--Device-NetFirewallDnsParams-standbyDns?: string--><!--Device-NetFirewallDnsParams-standbyDns?: string-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
