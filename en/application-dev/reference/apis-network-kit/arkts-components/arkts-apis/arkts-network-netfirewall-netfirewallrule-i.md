# NetFirewallRule

Defines a firewall rule.

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## action

```TypeScript
action: FirewallRuleAction
```

Action, which can be allowing or denying.

**Type:** [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md)

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## appUid

```TypeScript
appUid?: number
```

Application or service UID.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## description

```TypeScript
description?: string
```

Firewall rule description. This parameter is optional and can contain a maximum of 256 characters.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## direction

```TypeScript
direction: NetFirewallRuleDirection
```

Rule direction, which can be inbound or outbound.

**Type:** [NetFirewallRuleDirection](arkts-network-netfirewall-netfirewallruledirection-e.md)

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## dns

```TypeScript
dns?: NetFirewallDnsParams
```

List of DNS server names. This parameter is valid only when **type** is set to **RULE_DNS**. This parameter cannot be empty when **type** is set to **RULE_DNS**.

**Type:** [NetFirewallDnsParams](arkts-network-netfirewall-netfirewalldnsparams-i.md)

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## domains

```TypeScript
domains?: Array<NetFirewallDomainParams>
```

List of domain names. This parameter is valid only when **type** is set to **RULE_DOMAIN**. Currently, domain names cannot contain Chinese characters.

**Type:** Array&lt;[NetFirewallDomainParams](arkts-network-netfirewall-netfirewalldomainparams-i.md)&gt;

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## id

```TypeScript
id?: number
```

ID of the firewall rule.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## interface

```TypeScript
interface?: string
```

Interface name: valid when type = RULE_IP, otherwise it will be ignored.

**Type:** string

**Since:** 26.0.0

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## isEnabled

```TypeScript
isEnabled: boolean
```

Whether to enable the rule. The value **true** means to enable the rule, and the value **false** means the opposite.

**Type:** boolean

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## localIps

```TypeScript
localIps?: Array<NetFirewallIpParams>
```

Local IP addresses. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.

**Type:** Array&lt;[NetFirewallIpParams](arkts-network-netfirewall-netfirewallipparams-i.md)&gt;

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## localPorts

```TypeScript
localPorts?: Array<NetFirewallPortParams>
```

Local ports. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.

**Type:** Array&lt;[NetFirewallPortParams](arkts-network-netfirewall-netfirewallportparams-i.md)&gt;

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## name

```TypeScript
name: string
```

Rule name. This parameter is mandatory and can contain a maximum of 128 characters.

**Type:** string

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## protocol

```TypeScript
protocol?: number
```

Protocol, which can be TCP (value **6**) or UDP (value **17**). This parameter is valid only when **type** is set to **RULE_IP**.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## remoteIps

```TypeScript
remoteIps?: Array<NetFirewallIpParams>
```

Remote IP addresses. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.

**Type:** Array&lt;[NetFirewallIpParams](arkts-network-netfirewall-netfirewallipparams-i.md)&gt;

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## remotePorts

```TypeScript
remotePorts?: Array<NetFirewallPortParams>
```

Remote ports. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 ports can be specified.

**Type:** Array&lt;[NetFirewallPortParams](arkts-network-netfirewall-netfirewallportparams-i.md)&gt;

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## type

```TypeScript
type: NetFirewallRuleType
```

Rule type, which can be IP, Domain, or DNS.

**Type:** [NetFirewallRuleType](arkts-network-netfirewall-netfirewallruletype-e.md)

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## userId

```TypeScript
userId: number
```

System user ID, which must exist.

**Type:** number

**Since:** 15

**System capability:** SystemCapability.Communication.NetManager.NetFirewall
