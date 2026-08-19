# NetFirewallRule(网络防火墙)

防火墙规则信息结构。

**起始版本：** 15

<!--Device-netFirewall-interface NetFirewallRule--><!--Device-netFirewall-interface NetFirewallRule-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## action

```TypeScript
action: FirewallRuleAction
```

行为，包含允许和阻止。

**类型：** [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md)

**起始版本：** 15

<!--Device-NetFirewallRule-action: FirewallRuleAction--><!--Device-NetFirewallRule-action: FirewallRuleAction-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## appUid

```TypeScript
appUid?: int
```

应用程序或服务UID。

**类型：** int

**起始版本：** 15

<!--Device-NetFirewallRule-appUid?: int--><!--Device-NetFirewallRule-appUid?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## description

```TypeScript
description?: string
```

规则描述，可选，最多256个字符。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallRule-description?: string--><!--Device-NetFirewallRule-description?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## direction

```TypeScript
direction: NetFirewallRuleDirection
```

规则方向，包含入站和出站。

**类型：** [NetFirewallRuleDirection](arkts-network-netfirewall-netfirewallruledirection-e.md)

**起始版本：** 15

<!--Device-NetFirewallRule-direction: NetFirewallRuleDirection--><!--Device-NetFirewallRule-direction: NetFirewallRuleDirection-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## dns

```TypeScript
dns?: NetFirewallDnsParams
```

DNS：当type=RULE_DNS时有效，否则将被忽略。当type=RULE_DNS时，该字段不能为空。

**类型：** [NetFirewallDnsParams](arkts-network-netfirewall-netfirewalldnsparams-i.md)

**起始版本：** 15

<!--Device-NetFirewallRule-dns?: NetFirewallDnsParams--><!--Device-NetFirewallRule-dns?: NetFirewallDnsParams-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## domains

```TypeScript
domains?: Array<NetFirewallDomainParams>
```

域名列表，当type=RULE_DOMAIN时有效，否则将被忽略，目前不支持中文域名。

**类型：** Array&lt;[NetFirewallDomainParams](arkts-network-netfirewall-netfirewalldomainparams-i.md)&gt;

**起始版本：** 15

<!--Device-NetFirewallRule-domains?: Array<NetFirewallDomainParams>--><!--Device-NetFirewallRule-domains?: Array<NetFirewallDomainParams>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## id

```TypeScript
id?: int
```

防火墙规则的ID。

**类型：** int

**起始版本：** 15

<!--Device-NetFirewallRule-id?: int--><!--Device-NetFirewallRule-id?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## interface

```TypeScript
interface?: string
```

接口名：当type=RULE_IP时有效，否则忽略。

**类型：** string

**起始版本：** 26.0.0

**模型约束：** 此接口仅可在Stage模型下使用。

<!--Device-NetFirewallRule-interface?: string--><!--Device-NetFirewallRule-interface?: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## isEnabled

```TypeScript
isEnabled: boolean
```

是否启用规则。true表示启用，false表示不启用。

**类型：** boolean

**起始版本：** 15

<!--Device-NetFirewallRule-isEnabled: boolean--><!--Device-NetFirewallRule-isEnabled: boolean-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## localIps

```TypeScript
localIps?: Array<NetFirewallIpParams>
```

本地IP地址。当type=RULE_IP时有效，否则将被忽略，最多10个。

**类型：** Array&lt;[NetFirewallIpParams](arkts-network-netfirewall-netfirewallipparams-i.md)&gt;

**起始版本：** 15

<!--Device-NetFirewallRule-localIps?: Array<NetFirewallIpParams>--><!--Device-NetFirewallRule-localIps?: Array<NetFirewallIpParams>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## localPorts

```TypeScript
localPorts?: Array<NetFirewallPortParams>
```

本地端口。当type=RULE_IP时有效，否则将被忽略，最多10个。

**类型：** Array&lt;[NetFirewallPortParams](arkts-network-netfirewall-netfirewallportparams-i.md)&gt;

**起始版本：** 15

<!--Device-NetFirewallRule-localPorts?: Array<NetFirewallPortParams>--><!--Device-NetFirewallRule-localPorts?: Array<NetFirewallPortParams>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## name

```TypeScript
name: string
```

规则名称，必填，最多128个字符。

**类型：** string

**起始版本：** 15

<!--Device-NetFirewallRule-name: string--><!--Device-NetFirewallRule-name: string-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## protocol

```TypeScript
protocol?: int
```

协议，包含TCP：6，UDP：17。当type=RULE_IP时有效。

**类型：** int

**起始版本：** 15

<!--Device-NetFirewallRule-protocol?: int--><!--Device-NetFirewallRule-protocol?: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## remoteIps

```TypeScript
remoteIps?: Array<NetFirewallIpParams>
```

远端IP地址。当type=RULE_IP时有效，否则将被忽略，最多10个。

**类型：** Array&lt;[NetFirewallIpParams](arkts-network-netfirewall-netfirewallipparams-i.md)&gt;

**起始版本：** 15

<!--Device-NetFirewallRule-remoteIps?: Array<NetFirewallIpParams>--><!--Device-NetFirewallRule-remoteIps?: Array<NetFirewallIpParams>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## remotePorts

```TypeScript
remotePorts?: Array<NetFirewallPortParams>
```

远端端口。当type=RULE_IP时有效，否则将被忽略。最多10个。

**类型：** Array&lt;[NetFirewallPortParams](arkts-network-netfirewall-netfirewallportparams-i.md)&gt;

**起始版本：** 15

<!--Device-NetFirewallRule-remotePorts?: Array<NetFirewallPortParams>--><!--Device-NetFirewallRule-remotePorts?: Array<NetFirewallPortParams>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## type

```TypeScript
type: NetFirewallRuleType
```

规则类型，包含IP、Domain、DNS。

**类型：** [NetFirewallRuleType](arkts-network-netfirewall-netfirewallruletype-e.md)

**起始版本：** 15

<!--Device-NetFirewallRule-type: NetFirewallRuleType--><!--Device-NetFirewallRule-type: NetFirewallRuleType-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## userId

```TypeScript
userId: int
```

系统用户ID，只能是存在的用户ID。

**类型：** int

**起始版本：** 15

<!--Device-NetFirewallRule-userId: int--><!--Device-NetFirewallRule-userId: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

