# FirewallRulePage

```TypeScript
interface FirewallRulePage
```

Defines the pagination structure for firewall rules.

**Since:** 15

<!--Device-netFirewall-interface FirewallRulePage--><!--Device-netFirewall-interface FirewallRulePage-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## data

```TypeScript
data: Array<NetFirewallRule>
```

Page data.

**Type:** Array&lt;[NetFirewallRule](arkts-network-netfirewall-netfirewallrule-i.md)&gt;

**Since:** 15

<!--Device-FirewallRulePage-data: Array<NetFirewallRule>--><!--Device-FirewallRulePage-data: Array<NetFirewallRule>-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## page

```TypeScript
page: number
```

Current page number. The value range is [1,1000].

**Type:** number

**Since:** 15

<!--Device-FirewallRulePage-page: int--><!--Device-FirewallRulePage-page: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## pageSize

```TypeScript
pageSize: number
```

Page size. The value range is [1,50].

**Type:** number

**Since:** 15

<!--Device-FirewallRulePage-pageSize: int--><!--Device-FirewallRulePage-pageSize: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## totalPage

```TypeScript
totalPage: number
```

Total number of pages. The value range is [1,1000].

**Type:** number

**Since:** 15

<!--Device-FirewallRulePage-totalPage: int--><!--Device-FirewallRulePage-totalPage: int-End-->

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
