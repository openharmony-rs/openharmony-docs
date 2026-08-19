# setNetFirewallPolicy

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## setNetFirewallPolicy

```TypeScript
function setNetFirewallPolicy(userId: int, policy: NetFirewallPolicy): Promise<void>
```

设置系统用户ID的防火墙策略，包含防火墙开关状态，默认的出站/入站行为（允许/阻止）。支持不同的系统用户ID配置不同的防火墙策略。使用Promise异步回调。 > **说明：** > > 同一系统用户下，多应用调用该接口下发策略，会以最新下发的策略为准。

**起始版本：** 15

**需要权限：** ohos.permission.MANAGE_NET_FIREWALL

<!--Device-netFirewall-function setNetFirewallPolicy(userId: int, policy: NetFirewallPolicy): Promise<void>--><!--Device-netFirewall-function setNetFirewallPolicy(userId: int, policy: NetFirewallPolicy): Promise<void>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 是 | 系统用户ID，只能是存在的用户ID。 |
| policy | [NetFirewallPolicy](arkts-network-netfirewall-netfirewallpolicy-i.md) | 是 | 设置的防火墙策略。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | 无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [29400000](../errorcode-net-netfirewall.md#29400000-指定用户不存在) | The specified user does not exist. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let policy: netFirewall.NetFirewallPolicy = {
  isOpen: true,
  inAction: netFirewall.FirewallRuleAction.RULE_DENY,
  outAction: netFirewall.FirewallRuleAction.RULE_ALLOW
};
netFirewall.setNetFirewallPolicy(100, policy).then(() => {
  console.info("set firewall policy success.");
}).catch((error : BusinessError) => {
  console.error("set firewall policy failed: " + JSON.stringify(error));
});
```

