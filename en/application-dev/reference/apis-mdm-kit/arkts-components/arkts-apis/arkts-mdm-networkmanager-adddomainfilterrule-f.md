# addDomainFilterRule

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## addDomainFilterRule

```TypeScript
function addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void
```

Adds domain name filtering rules for the device.

In API version 21 and earlier versions, only IPv4 is supported. IPv4 and IPv6 are supported since API version 22.

[LogType](arkts-mdm-networkmanager-logtype-e.md) is supported since API version 23.

> **NOTE:** 
> 
> - After a rule with [Action](arkts-mdm-networkmanager-action-e.md) set to **ALLOW** is added, a default **DENY** rule is added automatically to discard or intercept domain name resolution packets that are not covered by the **ALLOW**rule.
> 
> - The added rules will be cleared after the device restarts.
> 
> - To prevent interception rules from becoming ineffective due to DNS caching, it is recommended that you configure domain name filtering rules immediately after the system starts up. If interception fails because of DNS caching, restart the system to clear the cache and restore the interception function.
> 
> - Rule matching order: Domain name filtering rules added by this API are matched first, followed by IP firewall rules (added via [addFirewallRule](arkts-mdm-networkmanager-addfirewallrule-f.md)). Within both domain name rules and IP rules, matching is performed in the order of ALLOW, DENY, and REJECT [actions](arkts-mdm-networkmanager-action-e.md).

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |
| domainFilterRule | [DomainFilterRule](arkts-mdm-networkmanager-domainfilterrule-i.md) | Yes | Domain name filtering rule object, including the domain name, application UID, and IP protocol version. |

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
let domainFilterRule: networkManager.DomainFilterRule = {
  // Replace with actual values.
  "domainName": "www.example.com",
  "appUid": "9696",
  "action": networkManager.Action.DENY,
  "family": 1,
  "logType": networkManager.LogType.NFLOG
};

try {
  networkManager.addDomainFilterRule(wantTemp, domainFilterRule);
  console.info('Succeeded in adding domain filter rules');
} catch (err) {
  console.error(`Failed to add domain filter rules. Code: ${err.code}, message: ${err.message}`);
}
```
