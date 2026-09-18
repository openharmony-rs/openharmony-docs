# RequestParam

查询输入信息结构。

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## orderField

```TypeScript
orderField: NetFirewallOrderField
```

排序方法。 该字段仅支持根据防火墙规则名排序。

**类型：** [NetFirewallOrderField](arkts-network-netfirewall-netfirewallorderfield-e.md)

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## orderType

```TypeScript
orderType: NetFirewallOrderType
```

排序顺序。

**类型：** [NetFirewallOrderType](arkts-network-netfirewall-netfirewallordertype-e.md)

**起始版本：** 15

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

## page

```TypeScript
page: number
```

页码，值范围：[1, 1000]。

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
