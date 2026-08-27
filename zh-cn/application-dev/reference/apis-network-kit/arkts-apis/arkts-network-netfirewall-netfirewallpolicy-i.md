# NetFirewallPolicy

防火墙策略，包含防火墙开关状态，默认的出站/入站行为（允许/阻止）。

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## inAction

```TypeScript
inAction: FirewallRuleAction
```

入站行为。

**类型：** [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md)

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## isOpen

```TypeScript
isOpen: boolean
```

是否开启防火墙。true表示开启防火墙，false表示关闭防火墙。

**类型：** boolean

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## outAction

```TypeScript
outAction: FirewallRuleAction
```

出站行为。

**类型：** [FirewallRuleAction](arkts-network-netfirewall-firewallruleaction-e.md)

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall
