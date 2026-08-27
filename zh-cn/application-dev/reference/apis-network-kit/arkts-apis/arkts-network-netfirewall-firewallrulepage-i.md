# FirewallRulePage

防火墙规则页信息结构。

**起始版本：** 15

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

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## page

```TypeScript
page: number
```

当前页码，值范围：[1,1000]。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## pageSize

```TypeScript
pageSize: number
```

页面大小，值范围：[1, 50]。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## totalPage

```TypeScript
totalPage: number
```

总页数，值范围：[1,1000]。

**类型：** number

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall
