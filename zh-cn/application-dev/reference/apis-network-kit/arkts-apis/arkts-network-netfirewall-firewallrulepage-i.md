# FirewallRulePage(网络防火墙)

防火墙规则页信息结构。

**起始版本：** 15

<!--Device-netFirewall-interface FirewallRulePage--><!--Device-netFirewall-interface FirewallRulePage-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## data

```TypeScript
data: Array<NetFirewallRule>
```

页面数据。

**类型：** Array&lt;[NetFirewallRule](arkts-network-netfirewall-netfirewallrule-i.md)&gt;

**起始版本：** 15

<!--Device-FirewallRulePage-data: Array<NetFirewallRule>--><!--Device-FirewallRulePage-data: Array<NetFirewallRule>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## page

```TypeScript
page: int
```

当前页码，值范围：[1,1000]。

**类型：** int

**起始版本：** 15

<!--Device-FirewallRulePage-page: int--><!--Device-FirewallRulePage-page: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## pageSize

```TypeScript
pageSize: int
```

页面大小，值范围：[1, 50]。

**类型：** int

**起始版本：** 15

<!--Device-FirewallRulePage-pageSize: int--><!--Device-FirewallRulePage-pageSize: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## totalPage

```TypeScript
totalPage: int
```

总页数，值范围：[1,1000]。

**类型：** int

**起始版本：** 15

<!--Device-FirewallRulePage-totalPage: int--><!--Device-FirewallRulePage-totalPage: int-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

