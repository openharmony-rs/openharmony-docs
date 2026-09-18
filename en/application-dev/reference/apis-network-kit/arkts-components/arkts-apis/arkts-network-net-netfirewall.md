# @ohos.net.netFirewall(Network Firewall)

The **netFirewall** module implements the network firewall functionality for applications. It allows applications to query the firewall interception records of the device.

**Since:** 14

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [addNetFirewallRule](arkts-network-netfirewall-addnetfirewallrule-f.md) | Adds a firewall rule for the system user ID. The supported rule types are IP, Domain, and DNS. This API uses a promise to return the result. |
| [getNetFirewallPolicy](arkts-network-netfirewall-getnetfirewallpolicy-f.md) | Queries the firewall policy for a system user ID, including the firewall switch status and default inbound or outbound behavior (allow or deny). This API uses a promise to return the result. |
| [getNetFirewallRule](arkts-network-netfirewall-getnetfirewallrule-f.md) | Obtains a firewall rule based on the specified user ID and rule ID. This API uses a promise to return the result. |
| [getNetFirewallRules](arkts-network-netfirewall-getnetfirewallrules-f.md) | Obtains firewall rules by user ID. You need to specify the pagination query parameter when calling this API. Currently, firewall rules can be sorted by name. This API uses a promise to return the result. |
| [removeNetFirewallRule](arkts-network-netfirewall-removenetfirewallrule-f.md) | Deletes a specified firewall rule of a system user ID. This API uses a promise to return the result. |
| [setNetFirewallPolicy](arkts-network-netfirewall-setnetfirewallpolicy-f.md) | Sets the firewall policy for a system user ID, including the firewall switch status and default inbound or outbound behavior (allow or deny). Different firewall policies can be configured for different system user IDs. This API uses a promise to return the result. |
| [updateNetFirewallRule](arkts-network-netfirewall-updatenetfirewallrule-f.md) | Updates a firewall rule. This API uses a promise to return the result. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [getInterceptedRecords](arkts-network-netfirewall-getinterceptedrecords-f-sys.md) | Get intercepted records by userId, and it is necessary to specify the pagination query parameters. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [FirewallRulePage](arkts-network-netfirewall-firewallrulepage-i.md) | Defines the pagination structure for firewall rules. |
| [NetFirewallDnsParams](arkts-network-netfirewall-netfirewalldnsparams-i.md) | Defines the DNS information of a firewall rule. |
| [NetFirewallDomainParams](arkts-network-netfirewall-netfirewalldomainparams-i.md) | Defines domain name parameters of a firewall rule. Currently, Chinese domain names are not supported. |
| [NetFirewallIpParams](arkts-network-netfirewall-netfirewallipparams-i.md) | Defines the IP parameters of the firewall rule. The IP address type can be IPv4 or IPv6. A single IP address or IP address segment is supported. |
| [NetFirewallPolicy](arkts-network-netfirewall-netfirewallpolicy-i.md) | Defines the firewall policy, including the firewall switch status and default inbound or outbound action (allow or deny). |
| [NetFirewallPortParams](arkts-network-netfirewall-netfirewallportparams-i.md) | Defines the port parameters of a firewall rule. |
| [NetFirewallRule](arkts-network-netfirewall-netfirewallrule-i.md) | Defines a firewall rule. |
| [RequestParam](arkts-network-netfirewall-requestparam-i.md) | Defines query parameters. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [InterceptedRecord](arkts-network-netfirewall-interceptedrecord-i-sys.md) | Intercepted record. |
| [InterceptedRecordPage](arkts-network-netfirewall-interceptedrecordpage-i-sys.md) | Intercepted record page information. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md) | Enumerates the firewall rule actions, including allowing or denying network connections. |
| [NetFirewallOrderField](arkts-network-netfirewall-netfirewallorderfield-e.md) | Enumerates the sorting methods of firewall rules. |
| [NetFirewallOrderType](arkts-network-netfirewall-netfirewallordertype-e.md) | Enumerates the sorting order of firewall rules, which can be ascending or descending. |
| [NetFirewallRuleDirection](arkts-network-netfirewall-netfirewallruledirection-e.md) | Enumerates the firewall rule directions, including inbound and outbound. |
| [NetFirewallRuleType](arkts-network-netfirewall-netfirewallruletype-e.md) | Enumerates the firewall rule types, including IP, Domain, and DNS. |
