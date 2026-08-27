# getNetFirewallPolicy

## 导入模块

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## getNetFirewallPolicy

```TypeScript
function getNetFirewallPolicy(userId: number): Promise<NetFirewallPolicy>
```

查询系统用户ID的防火墙策略，包含防火墙开关状态，默认出站入站行为（允许/阻止）。使用Promise异步回调。

**起始版本：** 15

**需要权限：** ohos.permission.GET_NET_FIREWALL

**系统能力：** SystemCapability.Communication.NetManager.NetFirewall

**参数：**

| 参数名 | 类型 | 必填 | 说明 |
| --- | --- | --- | --- |
| userId | number | 是 | 系统用户ID，只能是存在的用户ID。 |

**返回值：**

| 类型 | 说明 |
| --- | --- |
| Promise&lt;[NetFirewallPolicy](arkts-network-netfirewall-netfirewallpolicy-i.md)&gt; | 以Promise形式返回当前用户防火墙策略。 |

**错误码：**

| 错误码ID | 错误信息 |
| --- | --- |
| [201](../../errorcode-universal.md#201-权限校验失败) | Permission denied. |
| [401](../../errorcode-universal.md#401-参数检查失败) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-非法参数值) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-连接服务失败) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-系统内部错误) | System internal error. |
| [29400000](../errorcode-net-netfirewall.md#29400000-指定用户不存在) | The specified user does not exist. |

**示例**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

netFirewall.getNetFirewallPolicy(100).then((result: netFirewall.NetFirewallPolicy) => {
  console.info('firewall policy: ', JSON.stringify(result));
}, (reason: BusinessError) => {
  console.error('get firewall policy failed: ', JSON.stringify(reason));
});
```
