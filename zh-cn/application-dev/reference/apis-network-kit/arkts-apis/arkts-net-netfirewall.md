# @ohos.net.netFirewall(网络防火墙)

本模块为应用程序提供网络防火墙能力。应用程序可以对机器进行防火墙拦截记录的查询。

**起始版本：** 14

<!--Device-unnamed-declare namespace netFirewall--><!--Device-unnamed-declare namespace netFirewall-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## 汇总

### 函数

| 名称 | 说明 |
| --- | --- |
| [addNetFirewallRule(网络防火墙)](arkts-network-netfirewall-addnetfirewallrule-f.md) | 添加系统用户ID的防火墙规则，目前支持的规则类型有：IP、Domain、DNS。使用Promise异步回调。 |
| [getNetFirewallPolicy(网络防火墙)](arkts-network-netfirewall-getnetfirewallpolicy-f.md) | 查询系统用户ID的防火墙策略，包含防火墙开关状态，默认出站入站行为（允许/阻止）。使用Promise异步回调。 |
| [getNetFirewallRule(网络防火墙)](arkts-network-netfirewall-getnetfirewallrule-f.md) | 通过userId和ruleId获取指定的防火墙规则。使用Promise异步回调。 |
| [getNetFirewallRules(网络防火墙)](arkts-network-netfirewall-getnetfirewallrules-f.md) | 按用户ID获取防火墙规则，需要指定分页查询参数。目前支持根据防火墙规则名排序。使用Promise异步回调。 |
| [removeNetFirewallRule(网络防火墙)](arkts-network-netfirewall-removenetfirewallrule-f.md) | 删除系统用户ID的指定防火墙规则。使用Promise异步回调。 |
| [setNetFirewallPolicy(网络防火墙)](arkts-network-netfirewall-setnetfirewallpolicy-f.md) | 设置系统用户ID的防火墙策略，包含防火墙开关状态，默认的出站/入站行为（允许/阻止）。支持不同的系统用户ID配置不同的防火墙策略。使用Promise异步回调。 |
| [updateNetFirewallRule(网络防火墙)](arkts-network-netfirewall-updatenetfirewallrule-f.md) | 更新防火墙规则。使用Promise异步回调。 |

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [getInterceptedRecords(网络防火墙)](arkts-network-netfirewall-getinterceptedrecords-f-sys.md) | 按userId获取截获的记录，需要指定分页查询参数。 |
<!--DelEnd-->

### 接口

| 名称 | 说明 |
| --- | --- |
| [FirewallRulePage(网络防火墙)](arkts-network-netfirewall-firewallrulepage-i.md) | 防火墙规则页信息结构。 |
| [NetFirewallDnsParams(网络防火墙)](arkts-network-netfirewall-netfirewalldnsparams-i.md) | 防火墙规则DNS信息。 |
| [NetFirewallDomainParams(网络防火墙)](arkts-network-netfirewall-netfirewalldomainparams-i.md) | 防火墙规则域名参数，目前不支持中文域名。 |
| [NetFirewallIpParams(网络防火墙)](arkts-network-netfirewall-netfirewallipparams-i.md) | 防火墙规则的IP参数，IP类型包括IPv4、IPv6，支持单个IP或IP段。 |
| [NetFirewallPolicy(网络防火墙)](arkts-network-netfirewall-netfirewallpolicy-i.md) | 防火墙策略，包含防火墙开关状态，默认的出站/入站行为（允许/阻止）。 |
| [NetFirewallPortParams(网络防火墙)](arkts-network-netfirewall-netfirewallportparams-i.md) | 防火墙规则端口参数。 |
| [NetFirewallRule(网络防火墙)](arkts-network-netfirewall-netfirewallrule-i.md) | 防火墙规则信息结构。 |
| [RequestParam(网络防火墙)](arkts-network-netfirewall-requestparam-i.md) | 查询输入信息结构。 |

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [InterceptedRecord(网络防火墙)](arkts-network-netfirewall-interceptedrecord-i-sys.md) | 拦截记录。 |
| [InterceptedRecordPage(网络防火墙)](arkts-network-netfirewall-interceptedrecordpage-i-sys.md) | 拦截记录分页信息。 |
<!--DelEnd-->

### 枚举

| 名称 | 说明 |
| --- | --- |
| [FirewallRuleAction(网络防火墙)](arkts-network-netfirewall-firewallruleaction-e.md) | 枚举类型，防火墙规则行为，包含允许网络连接、阻止网络连接。 |
| [NetFirewallOrderField(网络防火墙)](arkts-network-netfirewall-netfirewallorderfield-e.md) | 枚举类型，防火墙规则排序方法。 |
| [NetFirewallOrderType(网络防火墙)](arkts-network-netfirewall-netfirewallordertype-e.md) | 枚举类型，防火墙规则排序顺序，包含升序或降序。 |
| [NetFirewallRuleDirection(网络防火墙)](arkts-network-netfirewall-netfirewallruledirection-e.md) | 枚举类型，防火墙规则方向，包含入站、出站。 |
| [NetFirewallRuleType(网络防火墙)](arkts-network-netfirewall-netfirewallruletype-e.md) | 枚举类型，防火墙规则类型，包含IP、Domain、DNS。 |

