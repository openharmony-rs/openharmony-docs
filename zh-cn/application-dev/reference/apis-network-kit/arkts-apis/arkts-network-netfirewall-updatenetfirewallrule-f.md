# updateNetFirewallRule

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## updateNetFirewallRule

```TypeScript
function updateNetFirewallRule(rule: NetFirewallRule): Promise<void>
```

更新防火墙规则。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.MANAGE_NET_FIREWALL

<!--Device-netFirewall-function updateNetFirewallRule(rule: NetFirewallRule): Promise<void>--><!--Device-netFirewall-function updateNetFirewallRule(rule: NetFirewallRule): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | [NetFirewallRule](arkts-network-netfirewall-netfirewallrule-i.md) | 是 | 防火墙规则。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [29400000](../errorcode-net-netfirewall.md#29400000-指定用户不存在) | The specified user does not exist. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Operation failed. Cannot connect to service. |
| [29400002](../errorcode-net-netfirewall.md#29400002-防火墙规则中的ip地址规则数量超过最大值) | The number of IP address rules in the firewall rule exceeds the maximum. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [29400003](../errorcode-net-netfirewall.md#29400003-防火墙规则中的port规则数量超过最大值) | The number of port rules in the firewall rule exceeds the maximum. |
| [29400004](../errorcode-net-netfirewall.md#29400004-防火墙规则中的域名规则数量超过最大值) | The number of domain rules in the firewall rule exceeds the maximum. |
| [29400005](../errorcode-net-netfirewall.md#29400005-模糊域名规则数量超过最大值) | The number of domain rules exceeds the maximum. |
| [29400006](../errorcode-net-netfirewall.md#29400006-指定的规则不存在) | The specified rule does not exist. |
| [29400007](../errorcode-net-netfirewall.md#29400007-dns规则重复) | The dns rule is duplication. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ipRuleUpd: netFirewall.NetFirewallRule = {
  id: 1,
  name: "rule1",
  description: "rule1 description update",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_IP,
  isEnabled: false,
  appUid: 20001,
  localIps: [
    {
      family: 1,
      type: 1,
      address: "10.10.1.1",
      mask: 32
    },{
      family: 1,
      type: 2,
      startIp: "10.20.1.1",
      endIp: "10.20.1.10"
    }],
  userId: 100,
  interface:"wlan0" // 从API版本26.0.0开始支持
};
netFirewall.updateNetFirewallRule(ipRuleUpd).then(() => {
  console.info('update firewall rule success.');
}, (reason: BusinessError) => {
  console.error('update firewall rule failed: ', JSON.stringify(reason));
});
```

