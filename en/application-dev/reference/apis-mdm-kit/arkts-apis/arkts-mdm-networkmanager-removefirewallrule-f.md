# removeFirewallRule

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## removeFirewallRule

```TypeScript
function removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void
```

Removes a firewall rule. This API is suitable for enterprise network security policy adjustment scenarios, such as canceling certain network access restrictions, adjusting firewall policies, and clearing outdated or invalid rules. It helps enterprises flexibly adjust network security policies and ensure that network access control policies meet actual requirements.

In API version 21 and earlier versions, only IPv4 is supported. IPv4 and IPv6 are supported since API version 22.

[LogType](arkts-mdm-networkmanager-logtype-e.md) is supported since API version 23.

If there is no rule with [Action](arkts-mdm-networkmanager-action-e.md) being **ALLOW** after the rule is removed, the **DENY** rules that are added by default with [addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md) will be removed.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| firewallRule | [FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md) | No | Firewall rule to remove. If the value is empty, all firewall rules will be removed. |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [9200001](../errorcode-enterpriseDeviceManager.md#9200001-deviceadmin-not-enabled) | The application is not an administrator application of the device. |
| [9200002](../errorcode-enterpriseDeviceManager.md#9200002-permission-denied) | The administrator application does not have permission to manage the device. |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission verification failed. The application does not have the permission required to call the API. |
| [401](../../errorcode-universal.md#401-parameter-check-failed) | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Examples**

```TypeScript
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let firewallRule: networkManager.FirewallRule = {
  // Replace with actual values.
  "srcAddr": "192.168.1.1-192.168.22.66",
  "destAddr": "10.1.1.1",
  "srcPort": "8080",
  "destPort": "8080",
  "appUid": "9696",
  "direction": networkManager.Direction.OUTPUT,
  "action": networkManager.Action.DENY,
  "protocol": networkManager.Protocol.UDP,
  "family": 1,
  "logType": networkManager.LogType.NFLOG
};

// Remove the specified firewall rule.
try {
  networkManager.removeFirewallRule(wantTemp, firewallRule);
  console.info('Succeeded in removing firewall rule.');
} catch (err) {
  console.error(`Failed to remove firewall rule. Code: ${err.code}, message: ${err.message}`);
}

// Clears all IPv4 rules.
try {
  networkManager.removeFirewallRule(wantTemp);
  console.info('Succeeded in removing all firewall rule.');
} catch (err) {
  console.error(`Failed to remove all firewall rule. Code: ${err.code}, message: ${err.message}`);
}
```
