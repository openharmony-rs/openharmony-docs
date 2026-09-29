# NetFirewallPolicy

```TypeScript
interface NetFirewallPolicy
```

Defines the firewall policy, including the firewall switch status and default inbound or outbound action (allow or deny).

**Since:** 15

<!--Device-netFirewall-interface NetFirewallPolicy--><!--Device-netFirewall-interface NetFirewallPolicy-End-->

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

<!--Device-NetFirewallPolicy-inAction: FirewallRuleAction--><!--Device-NetFirewallPolicy-inAction: FirewallRuleAction-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## isOpen

```TypeScript
isOpen: boolean
```

Whether to enable the firewall. The value **true** means to enable the firewall, and the value **false** means the opposite.

**Type:** boolean

**Since:** 15

<!--Device-NetFirewallPolicy-isOpen: boolean--><!--Device-NetFirewallPolicy-isOpen: boolean-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## outAction

```TypeScript
outAction: FirewallRuleAction
```

Outbound action.

**Type:** [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md)

**Since:** 15

<!--Device-NetFirewallPolicy-outAction: FirewallRuleAction--><!--Device-NetFirewallPolicy-outAction: FirewallRuleAction-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
