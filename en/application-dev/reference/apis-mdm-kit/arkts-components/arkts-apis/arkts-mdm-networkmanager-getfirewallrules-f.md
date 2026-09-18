# getFirewallRules

## Modules to Import

```TypeScript
import { networkManager } from '@kit.MDMKit';
```

## getFirewallRules

```TypeScript
function getFirewallRules(admin: Want): Array<FirewallRule>
```

Queries firewall rules of a device. This API is suitable for enterprise network security audit scenarios, such as checking the current firewall policy configuration, auditing network access control rules, verifying whether firewall rules are correctly executed, and troubleshooting network access issues. It helps enterprises audit and verify network security policies and ensure that network access control meets security requirements.

In API version 21 and earlier versions, only IPv4 is supported. IPv4 and IPv6 are supported since API version 22.

[LogType](arkts-mdm-networkmanager-logtype-e.md) is supported since API version 23.

**Since:** 12

**Required permissions:** ohos.permission.ENTERPRISE_MANAGE_NETWORK

**Model restriction:** This API can be used only in the stage model.

**System capability:** SystemCapability.Customization.EnterpriseDeviceManager

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| admin | [Want](../../apis-ability-kit/arkts-apis/arkts-ability-app-ability-want-want-c.md) | Yes | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application. |

**Return value:**

| Type | Description |
| --- | --- |
| Array&lt;[FirewallRule](arkts-mdm-networkmanager-firewallrule-i.md)&gt; | A list of firewall rules configured for the device is returned. If the operation fails, an exception will be thrown. |

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
let firewallRule: Array<networkManager.FirewallRule>;
try {
  firewallRule = networkManager.getFirewallRules(wantTemp);
  console.info('Succeeded in getting firewall rules');
} catch (err) {
  console.error(`Failed to get firewall rules. Code: ${err.code}, message: ${err.message}`);
}
```
