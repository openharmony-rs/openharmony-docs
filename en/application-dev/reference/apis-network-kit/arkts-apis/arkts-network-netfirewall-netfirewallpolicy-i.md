# NetFirewallPolicy

Defines the firewall policy, including the firewall switch status and default inbound or outbound action (allow or deny).

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## inAction

```TypeScript
inAction: FirewallRuleAction
```

Inbound action.

**Type:** [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md)

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## isOpen

```TypeScript
isOpen: boolean
```

Whether to enable the firewall. The value **true** means to enable the firewall, and the value **false** means the opposite.

**Type:** boolean

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## outAction

```TypeScript
outAction: FirewallRuleAction
```

Outbound action.

**Type:** [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md)

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
