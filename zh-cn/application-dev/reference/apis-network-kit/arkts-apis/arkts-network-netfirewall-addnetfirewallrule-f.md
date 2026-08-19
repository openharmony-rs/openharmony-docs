# addNetFirewallRule

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## addNetFirewallRule

```TypeScript
function addNetFirewallRule(rule: NetFirewallRule): Promise<int>
```

添加系统用户ID的防火墙规则，目前支持的规则类型有：IP、Domain、DNS。使用Promise异步回调。 > **说明：**> > 1. 防火墙规则优先级说明（[setNetFirePolicy](arkts-network-netfirewall-setnetfirewallpolicy-f.md)和 > [addNetFirewallRule](#addnetfirewallrule)无调用顺序要求）： > > - 调用[setNetFirePolicy](arkts-network-netfirewall-setnetfirewallpolicy-f.md)设置默认策略为阻止，调用 > [addNetFirewallRule](#addnetfirewallrule)新增显式规则，规则优先级由高到低为： > > - 显式阻止规则 > > - 显式允许规则 > > - 默认阻止策略 > > - 调用[setNetFirePolicy](arkts-network-netfirewall-setnetfirewallpolicy-f.md)设置默认策略为允许，调用 > [addNetFirewallRule](#addnetfirewallrule)新增显式规则，规则优先级由高到低为： > > - 显式允许规则 > > - 显式阻止规则 > > - 默认允许策略 > > - 防火墙IP规则和域名规则冲突时（域名解析的IP与IP规则的IP相同，规则行为冲突）： > > - 若以域名方式访问，则域名规则优先级高于IP规则，不受域名解析出的IP的规则影响。 > > - 若以IP方式访问，遵循以下原则： > > - 域名规则放行，若以IP方式访问之前经历过域名解析过程，则IP规则拦截或者默认策略拦截是不生效的，最终以IP方式访问是放行的。 > > - 域名规则放行，若以IP方式访问之前未经历过域名解析过程，则IP规则拦截或者默认策略拦截是生效的，最终以IP方式访问是拦截的。 > > - 域名规则拦截，则IP规则放行或者默认策略放行是生效的，最终以IP方式访问是放行的。 > > 2. 规则类型补充说明： > > - 当addNetFirewallRule的入参rule.type配置为RULE_IP时： > > - 若rule.action为RULE_ALLOW，且rule.localIps、rule.remoteIps均不配置，规则生效为全IP段允许通行； > > - 若rule.action 为RULE_DENY，且rule.localIps、rule.remoteIps均不配置，规则生效为全IP段拦截。 > > - 当addNetFirewallRule的入参rule.type配置为RULE_DOMAIN时，若rule.domains未配置，该规则不生效。 > > 3. 防火墙规则添加上限说明： > > - 单个系统用户ID添加的防火墙规则上限是1000，若超过该上限，则报错29400001。 > > - 所有的系统用户ID添加的防火墙规则总和的上限是2000，若超过该上限，则报错29400001。 > > - 所有的系统用户ID添加的模糊域名规则总和的上限是100，若超过该上限，则报错29400005。

**起始版本：** 15

**需要权限：** ohos.permission.MANAGE_NET_FIREWALL

<!--Device-netFirewall-function addNetFirewallRule(rule: NetFirewallRule): Promise<int>--><!--Device-netFirewall-function addNetFirewallRule(rule: NetFirewallRule): Promise<int>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| rule | [NetFirewallRule](arkts-network-netfirewall-netfirewallrule-i.md) | 是 | 防火墙规则。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;int&gt; | 以Promise形式返回防火墙规则ID，防火墙规则ID由系统自动生成。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [29400000](../errorcode-net-netfirewall.md#29400000-指定用户不存在) | The specified user does not exist. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [29400001](../errorcode-net-netfirewall.md#29400001-防火墙规则数量超过最大值) | The number of firewall rules exceeds the maximum. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Operation failed. Cannot connect to service. |
| [29400002](../errorcode-net-netfirewall.md#29400002-防火墙规则中的ip地址规则数量超过最大值) | The number of IP address rules in the firewall rule exceeds the maximum. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [29400003](../errorcode-net-netfirewall.md#29400003-防火墙规则中的port规则数量超过最大值) | The number of port rules in the firewall rule exceeds the maximum. |
| [29400004](../errorcode-net-netfirewall.md#29400004-防火墙规则中的域名规则数量超过最大值) | The number of domain rules in the firewall rule exceeds the maximum. |
| [29400005](../errorcode-net-netfirewall.md#29400005-模糊域名规则数量超过最大值) | The number of domain rules exceeds the maximum. |
| [29400007](../errorcode-net-netfirewall.md#29400007-dns规则重复) | The dns rule is duplication. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ipRule: netFirewall.NetFirewallRule = {
  name: "rule1",
  description: "rule1 description",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_IP,
  isEnabled: true,
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
  remoteIps:[
    {
      family: 1,
      type: 1,
      address: "20.10.1.1",
      mask: 32
    },{
      family: 1,
      type: 2,
      startIp: "20.20.1.1",
      endIp: "20.20.1.10"
    }],
  protocol: 6,
  localPorts: [
    {
      startPort: 1000,
      endPort: 1000
    },{
      startPort: 2000,
      endPort: 2001
    }],
  remotePorts: [
    {
      startPort: 443,
      endPort: 443
    }],
  userId: 100,
  interface:"wlan0" // 从API版本26.0.0开始支持
};
netFirewall.addNetFirewallRule(ipRule).then((result: number) => {
  console.info('rule Id: ', result);
}, (reason: BusinessError) => {
  console.error('add firewall rule failed: ', JSON.stringify(reason));
});

let domainRule: netFirewall.NetFirewallRule = {
  name: "rule2",
  description: "rule2 description",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_DOMAIN,
  isEnabled: true,
  appUid: 20002,
  domains: [
    {
      isWildcard: false,
      domain: "www.example.cn"
    },{
      isWildcard: true,
      domain: "*.example.cn"
    }],
  userId: 100,
  interface:"wlan0" // 从API版本26.0.0开始支持
};
netFirewall.addNetFirewallRule(domainRule).then((result: number) => {
  console.info('rule Id: ', result);
}, (reason: BusinessError) => {
  console.error('add firewall rule failed: ', JSON.stringify(reason));
});

let dnsRule: netFirewall.NetFirewallRule = {
  name: "rule3",
  description: "rule3 description",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_DNS,
  isEnabled: true,
  appUid: 20003,
  dns:{
   primaryDns: "4.4.4.4",
   standbyDns: "8.8.8.8",
  },
  userId: 100,
  interface:"wlan0" // 从API版本26.0.0开始支持
};
netFirewall.addNetFirewallRule(dnsRule).then((result: number) => {
  console.info('rule Id: ', result);
}, (reason: BusinessError) => {
  console.error('add firewall rule failed: ', JSON.stringify(reason));
});
```

