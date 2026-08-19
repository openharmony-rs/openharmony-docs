# getNetFirewallRule

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## getNetFirewallRule

```TypeScript
function getNetFirewallRule(userId: int, ruleId: int): Promise<NetFirewallRule>
```

通过userId和ruleId获取指定的防火墙规则。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.GET_NET_FIREWALL

<!--Device-netFirewall-function getNetFirewallRule(userId: int, ruleId: int): Promise<NetFirewallRule>--><!--Device-netFirewall-function getNetFirewallRule(userId: int, ruleId: int): Promise<NetFirewallRule>-End-->

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | int | 是 | 系统用户ID，只能是存在的用户ID。 |
| ruleId | int | 是 | 防火墙规则ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NetFirewallRule](arkts-network-netfirewall-netfirewallrule-i.md)&gt; | 以Promise形式返回防火墙规则。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [29400000](../errorcode-net-netfirewall.md#29400000-指定用户不存在) | The specified user does not exist. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [29400006](../errorcode-net-netfirewall.md#29400006-指定的规则不存在) | The specified rule does not exist. |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |

**示例**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

netFirewall.getNetFirewallRule(100, 1).then((rule: netFirewall.NetFirewallRule) => {
  console.info("result:", JSON.stringify(rule));
}).catch((error : BusinessError) => {
  console.error(" get firewall rules failed: " + JSON.stringify(error));
});
```

