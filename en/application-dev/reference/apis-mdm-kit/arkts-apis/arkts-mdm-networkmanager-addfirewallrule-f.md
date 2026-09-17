# addFirewallRule

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## addFirewallRule

```TypeScript
function addFirewallRule(admin: Want, firewallRule: FirewallRule): void
```

Adds firewall rules for the device. This API is suitable for enterprise network security management and control scenarios. For example, it can be used to restrict network access from specific IP addresses, prevent malicious network attacks, control network communication of applications, and manage the trustlist or blocklist for network access. This helps enterprises implement refined control over network access and prevent network attacks and data leaks.

In API version 21 and earlier versions, only IPv4 is supported. IPv4 and IPv6 are supported since API version 22.

[LogType](arkts-mdm-networkmanager-logtype-e.md) is supported since API version 23.

> **NOTE:** 
> 
> - After a rule with [Action](arkts-mdm-networkmanager-action-e.md) set to **ALLOW** is added, a rule with **Action** set to **DENY** is added by default to discard or intercept all network data packets that do not meet the **ALLOW**rule.
> 
> - After the device is restarted, the firewall rules are cleared.
> 
> - Rule matching order: Domain name filtering rules (added via [addDomainFilterRule](arkts-mdm-networkmanager-adddomainfilterrule-f.md)) are matched first, followed by IP firewall rules added by this API. Within both domain name rules and IP rules, matching is performed in the order of ALLOW, DENY,and REJECT [actions](arkts-mdm-networkmanager-action-e.md).

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| firewallRule | [FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md) | Yes | Firewall rule to add. |

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

try {
  networkManager.addFirewallRule(wantTemp, firewallRule);
  console.info('Succeeded in adding firewall rule.');
} catch (err) {
  console.error(`Failed to add firewall rule. Code: ${err.code}, message: ${err.message}`);
}
```
