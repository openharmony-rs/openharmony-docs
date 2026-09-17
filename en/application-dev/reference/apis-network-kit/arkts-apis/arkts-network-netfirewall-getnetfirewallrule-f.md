# getNetFirewallRule

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## getNetFirewallRule

```TypeScript
function getNetFirewallRule(userId: number, ruleId: number): Promise<NetFirewallRule>
```

Obtains a firewall rule based on the specified user ID and rule ID. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**Since:** 15

**Required permissions:** ohos.permission.GET_NET_FIREWALL

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | System user ID, which must exist. |
| ruleId | number | Yes | ID of the firewall rule. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NetFirewallRule](arkts-network-netfirewall-netfirewallrule-i.md)&gt; | Promise used to return the result, which is a firewall rule. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [29400000](../errorcode-net-netfirewall.md#29400000-specified-user-does-not-exist) | The specified user does not exist. |
| [29400006](../errorcode-net-netfirewall.md#29400006-specified-rule-does-not-exist) | The specified rule does not exist. |

**Examples**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

netFirewall.getNetFirewallRule(100, 1).then((rule: netFirewall.NetFirewallRule) => {
  console.info("result:", JSON.stringify(rule));
}).catch((error : BusinessError) => {
  console.error(" get firewall rules failed: " + JSON.stringify(error));
});
```
