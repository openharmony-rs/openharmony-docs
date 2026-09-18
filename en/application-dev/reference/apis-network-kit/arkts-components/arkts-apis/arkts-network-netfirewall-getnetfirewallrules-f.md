# getNetFirewallRules

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## getNetFirewallRules

```TypeScript
function getNetFirewallRules(userId: number, requestParam: RequestParam): Promise<FirewallRulePage>
```

Obtains firewall rules by user ID. You need to specify the pagination query parameter when calling this API. Currently, firewall rules can be sorted by name. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**Since:** 15

**Required permissions:** ohos.permission.GET_NET_FIREWALL

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | System user ID, which must exist. |
| requestParam | [RequestParam](arkts-network-netfirewall-requestparam-i.md) | Yes | Pagination query parameter. The **orderField** field can be sorted only by firewall rule name. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[FirewallRulePage](arkts-network-netfirewall-firewallrulepage-i.md)&gt; | Promise used to return the result, which is list of firewall rules. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denied. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. |
| [2100001](../errorcode-net-connection.md#2100001-invalid-parameter-value) | Invalid parameter value. |
| [2100002](../errorcode-net-connection.md#2100002-service-connection-failure) | Operation failed. Cannot connect to service. |
| [2100003](../errorcode-net-connection.md#2100003-system-internal-error) | System internal error. |
| [29400000](../errorcode-net-netfirewall.md#29400000-specified-user-does-not-exist) | The specified user does not exist. |

**Examples**

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ruleParam: netFirewall.RequestParam = {
  page: 1,
  pageSize: 10,
  orderField: netFirewall.NetFirewallOrderField.ORDER_BY_RULE_NAME,
  orderType: netFirewall.NetFirewallOrderType.ORDER_ASC
};
netFirewall.getNetFirewallRules(100, ruleParam).then((result: netFirewall.FirewallRulePage) => {
  console.info("result:", JSON.stringify(result));
}, (error: BusinessError) => {
  console.error("get firewall rules failed: " + JSON.stringify(error));
});
```
