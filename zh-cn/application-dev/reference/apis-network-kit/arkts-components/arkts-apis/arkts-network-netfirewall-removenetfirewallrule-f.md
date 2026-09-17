# removeNetFirewallRule

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## removeNetFirewallRule

```TypeScript
function removeNetFirewallRule(userId: number, ruleId: number): Promise<void>
```

删除系统用户ID的指定防火墙规则。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.MANAGE_NET_FIREWALL

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 系统用户ID，只能是存在的用户ID。 |
| ruleId | number | 是 | 防火墙规则ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;void&gt; | Promise对象。无返回结果的Promise对象。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [29400000](../errorcode-net-netfirewall.md#29400000-指定用户不存在) | The specified user does not exist. |
| [29400006](../errorcode-net-netfirewall.md#29400006-指定的规则不存在) | The specified rule does not exist. |

**示例**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

netFirewall.removeNetFirewallRule(100, 1).then(() => {
  console.info("delete firewall rule success.");
}).catch((error : BusinessError) => {
  console.error("delete firewall rule failed: " + JSON.stringify(error));
});
```
