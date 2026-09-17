# getNetFirewallPolicy

## Modules to Import

```TypeScript
import { netFirewall } from '@kit.NetworkKit';
```

## getNetFirewallPolicy

```TypeScript
function getNetFirewallPolicy(userId: number): Promise<NetFirewallPolicy>
```

Queries the firewall policy for a system user ID, including the firewall switch status and default inbound or outbound behavior (allow or deny). This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**Since:** 15

**Required permissions:** ohos.permission.GET_NET_FIREWALL

**System capability:** SystemCapability.Communication.NetManager.NetFirewall

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| userId | number | Yes | System user ID, which must exist. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[NetFirewallPolicy](arkts-network-netfirewall-netfirewallpolicy-i.md)&gt; | Promise used to return the result, which is a firewall policy. |

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

netFirewall.getNetFirewallPolicy(100).then((result: netFirewall.NetFirewallPolicy) => {
  console.info('firewall policy: ', JSON.stringify(result));
}, (reason: BusinessError) => {
  console.error('get firewall policy failed: ', JSON.stringify(reason));
});
```
