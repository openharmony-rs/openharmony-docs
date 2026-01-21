# @ohos.enterprise.networkManager (Network Management)
<!--Kit: MDM Kit-->
<!--Subsystem: Customization-->
<!--Owner: @huanleima-->
<!--Designer: @liuzuming-->
<!--Tester: @lpw_work-->
<!--Adviser: @Brilliantry_Rui-->

The **networkManager** module provides APIs for network management of enterprise devices, including obtaining the device IP address and MAC address.

> **NOTE**
>
> - The initial APIs of this module are supported since API version 12. Newly added APIs will be marked with a superscript to indicate their earliest API version.
>
> - The APIs of this module can be used only in the stage model.
>
> - The APIs of this module can be called only by a device administrator application that is enabled. For details, see [MDM Kit Development](../../mdm/mdm-kit-guide.md).
>

## Modules to Import

```ts
import { networkManager } from '@kit.MDMKit';
```

## networkManager.getAllNetworkInterfacesSync

getAllNetworkInterfacesSync(admin: Want): Array&lt;string&gt;

Obtains all activated wired network interfaces.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type               | Description                  |
| ------------------- | ---------------------- |
| Array&lt;string&gt; | Names of all activated wired network interfaces.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: Array<string> = networkManager.getAllNetworkInterfacesSync(wantTemp);
  console.info(`Succeeded in getting all network interfaces, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get all network interfaces. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.getIpAddressSync

getIpAddressSync(admin: Want, networkInterface: string): string

Obtains the device IP address based on the network interface.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name          | Type                                                   | Mandatory| Description          |
| ---------------- | ------------------------------------------------------- | ---- | -------------- |
| admin            | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| networkInterface | string                                                  | Yes  | Network port.|

**Return value**

| Type  | Description            |
| ------ | ---------------- |
| string | IP address of the network interface specified by the device.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: string = networkManager.getIpAddressSync(wantTemp, 'eth0');
  console.info(`Succeeded in getting ip address, result : ${result}`);
} catch (err) {
  console.error(`Failed to get ip address. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.getMacSync

getMacSync(admin: Want, networkInterface: string): string

Obtains the MAC address of a device based on the network interface.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name          | Type                                                   | Mandatory| Description          |
| ---------------- | ------------------------------------------------------- | ---- | -------------- |
| admin            | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| networkInterface | string                                                  | Yes  | Network port.|

**Return value**

| Type  | Description             |
| ------ | ----------------- |
| string | MAC address of the network interface specified by the device.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: string = networkManager.getMacSync(wantTemp, 'eth0');
  console.info(`Succeeded in getting mac, result : ${result}`);
} catch (err) {
  console.error(`Failed to get mac. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.isNetworkInterfaceDisabledSync

isNetworkInterfaceDisabledSync(admin: Want, networkInterface: string): boolean

Queries whether a specified network interface is disabled.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name          | Type                                                   | Mandatory| Description          |
| ---------------- | ------------------------------------------------------- | ---- | -------------- |
| admin            | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| networkInterface | string                                                  | Yes  | Network port.|

**Return value**

| Type   | Description                                                        |
| ------- | ------------------------------------------------------------ |
| boolean | Returns **true** if the network port is disabled; returns **false** otherwise.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: boolean = networkManager.isNetworkInterfaceDisabledSync(wantTemp, 'eth0');
  console.info(`Succeeded in querying network interface is disabled or not, result : ${result}`);
} catch (err) {
  console.error(`Failed to query network interface is disabled or not. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.setNetworkInterfaceDisabledSync

setNetworkInterfaceDisabledSync(admin: Want, networkInterface: string, isDisabled: boolean): void

Disables the device from using the specified network interface.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name          | Type                                                   | Mandatory| Description                                             |
| ---------------- | ------------------------------------------------------- | ---- | ------------------------------------------------- |
| admin            | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                           |
| networkInterface | string                                                  | Yes  | Network port.                                   |
| isDisabled       | boolean                                                 | Yes  | Network port status to set. The value **true** means to disable the network port, and **false** means to enable the network port.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  networkManager.setNetworkInterfaceDisabledSync(wantTemp, 'eth0', true);
  console.info(`Succeeded in setting network interface disabled`);
} catch (err) {
  console.error(`Failed to set network interface disabled. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.setGlobalProxySync

setGlobalProxySync(admin: Want, httpProxy: connection.HttpProxy): void

Sets the global network proxy.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                        | Mandatory| Description                      |
| --------- | ------------------------------------------------------------ | ---- | -------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.            |
| httpProxy | [connection.HttpProxy](../apis-network-kit/js-apis-net-connection.md#httpproxy10) | Yes  | Global HTTP proxy to set.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { connection } from '@kit.NetworkKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

// Replace with actual values.
let exclusionStr: string = "192.168,baidu.com";
let exclusionArray: Array<string> = exclusionStr.split(',');
let httpProxy: connection.HttpProxy = {
  host: "192.168.xx.xxx",
  port: 8080,
  exclusionList: exclusionArray
};

try {
  networkManager.setGlobalProxySync(wantTemp, httpProxy);
  console.info(`Succeeded in setting network global proxy.`);
} catch (err) {
  console.error(`Failed to set network global proxy. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.setGlobalProxyForAccount<sup>15+</sup>

setGlobalProxyForAccount(admin: Want, httpProxy: connection.HttpProxy, accountId: number): void

Sets the network proxy for a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name   | Type                                                        | Mandatory| Description                      |
| --------- | ------------------------------------------------------------ | ---- | -------------------------- |
| admin     | [Want](../apis-ability-kit/js-apis-app-ability-want.md)      | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.            |
| httpProxy | [connection.HttpProxy](../apis-network-kit/js-apis-net-connection.md#httpproxy10) | Yes  | HTTP proxy configuration of the network.|
| accountId | number                                                  | Yes  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { connection } from '@kit.NetworkKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

let httpProxy: connection.HttpProxy = {
  // Replace with actual values.
  host: '192.168.xx.xxx',
  port: 8080,
  exclusionList: ['192.168', 'baidu.com']
};

try {
  // Replace parameters with actual values.
  networkManager.setGlobalProxyForAccount(wantTemp, httpProxy, 100);
  console.info(`Succeeded in setting network global proxy.`);
} catch (err) {
  console.error(`Failed to set network global proxy. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.getGlobalProxySync

getGlobalProxySync(admin: Want): connection.HttpProxy

Obtains the global network proxy.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type                                                        | Description                          |
| ------------------------------------------------------------ | ------------------------------ |
| [connection.HttpProxy](../apis-network-kit/js-apis-net-connection.md#httpproxy10) | Global HTTP proxy configuration obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { connection } from '@kit.NetworkKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  let result: connection.HttpProxy = networkManager.getGlobalProxySync(wantTemp);
  console.info(`Succeeded in getting network global proxy, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get network global proxy. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.getGlobalProxyForAccount<sup>15+</sup>

getGlobalProxyForAccount(admin: Want | null, accountId: number): connection.HttpProxy

Obtains the network proxy for a specified user.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Device behavior differences**: This API can be properly called on PCs/2-in-1 devices. If it is called on other device types, error code 801 is returned.

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) \| null | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| accountId | number                                                  | Yes  | User ID, which must be greater than or equal to 0.<br> You can call [getOsAccountLocalId](../apis-basic-services-kit/js-apis-osAccount.md#getosaccountlocalid9-1) of **@ohos.account.osAccount** to obtain the user ID.|

**Return value**

| Type                                                        | Description                          |
| ------------------------------------------------------------ | ------------------------------ |
| [connection.HttpProxy](../apis-network-kit/js-apis-net-connection.md#httpproxy10) | HTTP proxy configuration of the network.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 801      | Capability not supported. Failed to call the API due to limited device capabilities. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';
import { connection } from '@kit.NetworkKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};

try {
  // Replace parameters with actual values.
  let result: connection.HttpProxy = networkManager.getGlobalProxyForAccount(wantTemp, 100);
  console.info(`Succeeded in getting network global proxy, result : ${JSON.stringify(result)}`);
} catch (err) {
  console.error(`Failed to get network global proxy. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.addFirewallRule

addFirewallRule(admin: Want, firewallRule: FirewallRule): void

Adds firewall rules for the device. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.<br>
After a rule with [Action](#action) set to **ALLOW** is added, a rule with **Action** set to **DENY** is added by default to discard or intercept all network data packets that do not meet the **ALLOW** rule.<br>
After the device is restarted, the firewall rules are cleared.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                |
| ------------ | ------------------------------------------------------- | ---- | -------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.      |
| firewallRule | [FirewallRule](#firewallrule)                           | Yes  | Firewall rule to add.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
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
  "family": 1
};

try {
  networkManager.addFirewallRule(wantTemp, firewallRule);
  console.info('Succeeded in adding firewall rule.');
} catch (err) {
  console.error(`Failed to add firewall rule. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.removeFirewallRule

removeFirewallRule(admin: Want, firewallRule?: FirewallRule): void

Removes firewall rules of the device. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.<br>
If there is no rule with [Action](#action) being **ALLOW** after the rule is removed, the **DENY** rules that are added by default with [addFirewallRule](#networkmanageraddfirewallrule) will be removed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name      | Type                                                   | Mandatory| Description                                                |
| ------------ | ------------------------------------------------------- | ---- | ---------------------------------------------------- |
| admin        | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                      |
| firewallRule | [FirewallRule](#firewallrule)                           | No  | Firewall rule to remove. If the value is empty, all firewall rules will be removed.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
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
  "family": 1
};

// Remove the specified firewall rule.
try {
  networkManager.removeFirewallRule(wantTemp, firewallRule);
  console.info('Succeeded in removing firewall rule.');
} catch (err) {
  console.error(`Failed to remove firewall rule. Code: ${err.code}, message: ${err.message}`);
}

// Remove all firewall rules.
try {
  networkManager.removeFirewallRule(wantTemp);
  console.info('Succeeded in removing all firewall rule.');
} catch (err) {
  console.error(`Failed to remove all firewall rule. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.getFirewallRules

getFirewallRules(admin: Want): Array\<FirewallRule>

Checks firewall rules of the device. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type                                 | Description                                                        |
| ------------------------------------- | ------------------------------------------------------------ |
| Array\<[FirewallRule](#firewallrule)> | A list of firewall rules configured for the device is returned. If the operation fails, an exception will be thrown.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
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

## networkManager.addDomainFilterRule

addDomainFilterRule(admin: Want, domainFilterRule: DomainFilterRule): void

Adds domain name filtering rules for the device. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.<br>
After a rule with [Action](#action) set to **ALLOW** is added, a rule with **Action** set to **DENY** is added by default to discard or intercept all packets for domain name resolution that do not meet the **ALLOW** rule.<br>
After the device is restarted, the domain name filtering rules are cleared.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name          | Type                                                   | Mandatory| Description              |
| ---------------- | ------------------------------------------------------- | ---- | ------------------ |
| admin            | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.    |
| domainFilterRule | [DomainFilterRule](#domainfilterrule)                   | Yes  | Domain name filtering rule to add.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
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
  "family": 1
};

try {
  networkManager.addDomainFilterRule(wantTemp, domainFilterRule);
  console.info('Succeeded in adding domain filter rules');
} catch (err) {
  console.error(`Failed to add domain filter rules. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.removeDomainFilterRule

removeDomainFilterRule(admin: Want, domainFilterRule?: DomainFilterRule): void

Removes domain name filtering rules for the device. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.<br>
If there is no rule with [Action](#action) being **ALLOW** after the rule is removed, the **DENY** rules that are added by default with [addDomainFilterRule](#networkmanageradddomainfilterrule) will be removed.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name          | Type                                                   | Mandatory| Description                                            |
| ---------------- | ------------------------------------------------------- | ---- | ------------------------------------------------ |
| admin            | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.                                  |
| domainFilterRule | [DomainFilterRule](#domainfilterrule)                   | No  | Domain name filtering rule to remove. If the value is empty, all domain name filtering rules will be removed.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
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
  "family": 1
};

// Remove the specified firewall rule.
try {
  networkManager.removeDomainFilterRule(wantTemp, domainFilterRule);
  console.info('Succeeded in removing domain filter rules');
} catch (err) {
  console.error(`Failed to remove domain filter rules. Code: ${err.code}, message: ${err.message}`);
}

// Remove all firewall rules.
try {
  networkManager.removeDomainFilterRule(wantTemp);
  console.info('Succeeded in removing all domain filter rules');
} catch (err) {
  console.error(`Failed to remove all domain filter rules. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.getDomainFilterRules

getDomainFilterRules(admin: Want): Array\<DomainFilterRule>

Checks domain name filtering rules of the device. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Return value**

| Type                                         | Description                                                        |
| --------------------------------------------- | ------------------------------------------------------------ |
| Array\<[DomainFilterRule](#domainfilterrule)> | A list of domain name filtering rules configured for the device is returned. If the operation fails, an exception will be thrown.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |
| 401      | Parameter error. Possible causes: 1. Mandatory parameters are left unspecified; 2. Incorrect parameter types; 3. Parameter verification failed. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
let domainFilterRule: Array<networkManager.DomainFilterRule>;
try {
  domainFilterRule = networkManager.getDomainFilterRules(wantTemp);
  console.info('Succeeded in getting  domain filter rules');
} catch (err) {
  console.error(`Failed to get domain filter rules. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.turnOnMobileData<sup>20+</sup>

turnOnMobileData(admin: Want, isForce: boolean): void

Turns on mobile data.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| isForce  | boolean | Yes  | Whether to forcibly enable mobile data. <br>The value **true** means to forcibly enable mobile data. Once enabled, it cannot be turned off manually; it can only be disabled via the [turnOffMobileData](#networkmanagerturnoffmobiledata20) API. The value **false** means not to forcibly enable mobile data. It can be turned off manually.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  networkManager.turnOnMobileData(wantTemp, true);
  console.info(`Turn on mobile data succeeded`);
} catch (err) {
  console.error(`Failed to turn on mobile data. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.turnOffMobileData<sup>20+</sup>

turnOffMobileData(admin: Want): void

Turns off mobile data.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { networkManager } from '@kit.MDMKit';
import { Want } from '@kit.AbilityKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility'
};
try {
  networkManager.turnOffMobileData(wantTemp);
  console.info(`Turn off mobile data succeeded`);
} catch (err) {
  console.error(`Failed to turn off mobile data. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.addApn<sup>20+</sup>

addApn(admin: Want, apnInfo: Record\<string, string>): void

Adds an access point name (APN).

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APN

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| apnInfo  | Record\<string, string> | Yes  | APN information to be added.<br>- **apnName**: APN identifier, which is mandatory.<br>- **mcc**: 3-digit mobile country code (MCC), which is mandatory.<br>- **mnc**: 2-digit or 3-digit mobile network code (MNC), which is mandatory.<br>- **apn**: access point name, which is mandatory.<br>- **type**: APN service type, which is optional.<br>- **user**: user name for APN authentication, which is optional.<br>- **password**: password for APN authentication, which is optional.<br>- **proxy**: address of the proxy server for a common data connection, which is optional.<br>- **mmsproxy**: dedicated proxy address of the MMS service, which is optional.<br>- **authType**: authentication protocol type of the APN, which is optional.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnInfo: Record<string, string> = {
  // Replace it as required.
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460",
};
try {
  networkManager.addApn(wantTemp, apnInfo);
  console.info(`Succeeded in adding apn.`);
} catch (err) {
  console.error(`Failed to add apn. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.deleteApn<sup>20+</sup>

deleteApn(admin: Want, apnId: string): void

Deletes the APN.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APN

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| apnId  | string | Yes  | APN ID to be deleted. You can obtain device information using [networkManager.queryApn](#networkmanagerqueryapn20).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnId: string = "1"; // Replace it as required.
try {
  networkManager.deleteApn(wantTemp, apnId);
  console.info(`Succeeded in deleting apn.`);
} catch (err) {
  console.error(`Failed to delete apn. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.updateApn<sup>20+</sup>

updateApn(admin: Want, apnInfo: Record\<string, string>, apnId: string): void

Updates the APN.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APN

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| apnInfo  | Record\<string, string> | Yes  | APN information to be updated.<br>- **apnName**: APN identifier, which is optional.<br>- **mcc**: 3-digit mobile country code (MCC), which is optional.<br>- **mnc**: 2-digit or 3-digit mobile network code (MNC), which is optional.<br>- **APN**: access point name, which is optional.<br>- **type**: APN service type, which is optional.<br>- **user**: user name for APN authentication, which is optional.<br>- **password**: password for APN authentication, which is optional.<br>- **proxy**: address of the proxy server for a common data connection, which is optional.<br>- **mmsproxy**: dedicated proxy address of the MMS service, which is optional.<br>- **authType**: authentication protocol type of the APN, which is optional.|
| apnId  | string | Yes  | APN ID to be updated. You can obtain device information using [networkManager.queryApn](#networkmanagerqueryapn20).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnInfo: Record<string, string> = {
  // Replace it as required.
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460",
};
let apnId: string = "1"; // Replace it as required.
try {
  networkManager.updateApn(wantTemp, apnInfo, apnId);
  console.info(`Succeeded in updating apn.`);
} catch (err) {
  console.error(`Failed to update apn. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.setPreferredApn<sup>20+</sup>

setPreferredApn(admin: Want, apnId: string): void

Sets the preferred APN.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APN

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| apnId  | string | Yes  | Preferred APN ID to be set. You can obtain device information using [networkManager.queryApn](#networkmanagerqueryapn20).|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnId: string = "1"; // Replace it as required.
try {
  networkManager.setPreferredApn(wantTemp, apnId);
  console.info(`Succeeded in setting preferred apn.`);
} catch (err) {
  console.error(`Failed to set preferred apn. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.queryApn<sup>20+</sup>

queryApn(admin: Want, apnInfo: Record\<string, string>): Array\<string>

Queries the APN ID.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APN

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| apnInfo  | Record\<string, string> | Yes  | APN information.<br>- **apnName**: APN identifier, which is optional.<br>- **mcc**: 3-digit mobile country code (MCC), which is optional.<br>- **mnc**: 2-digit or 3-digit mobile network code (MNC), which is optional.<br>- **apn**: access point name, which is optional.<br>- **type**: APN service type, which is optional.<br>- **user**: user name for APN authentication, which is optional.<br>- **proxy**: address of the proxy server for a common data connection, which is optional.<br>- **mmsproxy**: dedicated proxy address of the MMS service, which is optional.<br>- **authType**: authentication protocol type of the APN, which is optional.|

**Return value**

| Type                                         | Description                                                        |
| --------------------------------------------- | ------------------------------------------------------------ |
| Array\<string> | APN ID obtained.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnInfo: Record<string, string> = {
  // Replace it as required.
  "apnName": "CTNET",
  "apn": "CTNET",
  "mnc": "11",
  "mcc": "460",
};
try {
  let queryResult: Array<string> = networkManager.queryApn(wantTemp, apnInfo);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.queryApn<sup>20+</sup>

queryApn(admin: Want, apnId: string): Record\<string, string>

Queries the APN parameter information.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_APN

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility. **Want** must contain the ability name of the EnterpriseAdminExtensionAbility and the bundle name of the application.|
| apnId  | string | Yes  | Specified APN ID. You can obtain device information using [networkManager.queryApn](#networkmanagerqueryapn20).|

**Return value**

| Type                                         | Description                                                        |
| --------------------------------------------- | ------------------------------------------------------------ |
| Record\<string, string> | APN parameter information of the specified APN ID.<br>- **apnName**: APN identifier.<br>- **mcc**: 3-digit mobile country code (MCC).<br>- **mnc**: 2-digit or 3-digit mobile network code (MNC).<br>- **apn**: access point name.<br>- **type**: APN service type.<br>- **user**: user name for APN authentication.<br>- **proxy**: address of the proxy server for a common data connection.<br>- **mmsproxy**: dedicated proxy address of the MMS service.<br>- **authType**: authentication protocol type of the APN.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace it as required.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let apnId: string = "1"; // Replace it as required.
try {
  let queryResult: Record<string, string> = networkManager.queryApn(wantTemp, apnId);
  console.info(`Succeeded in querying apn, result : ${JSON.stringify(queryResult)}`);
} catch (err) {
  console.error(`Failed to query apn. Code: ${err.code}, message: ${err.message}`);
}
```

## networkManager.setEthernetConfig<sup>23+</sup>

setEthernetConfig(admin: Want, networkInterface: string, config: InterfaceConfig): void

Sets the IP address of a specific Ethernet interface.

**Required permissions**: ohos.permission.ENTERPRISE_MANAGE_NETWORK

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager

**Model restriction**: This API can be used only in the stage model.

**Parameters**

| Name| Type                                                   | Mandatory| Description          |
| ------ | ------------------------------------------------------- | ---- | -------------- |
| admin  | [Want](../apis-ability-kit/js-apis-app-ability-want.md) | Yes  | EnterpriseAdminExtensionAbility.|
| networkInterface  | string | Yes  | Network interface name to set.|
| config  | [InterfaceConfig](#interfaceconfig23) | Yes  | Network interface configuration to set.|

**Error codes**

For details about the error codes, see [Enterprise Device Management Error Codes](errorcode-enterpriseDeviceManager.md) and [Universal Error Codes](../errorcode-universal.md).

| ID| Error Message                                                    |
| -------- | ------------------------------------------------------------ |
| 9200001  | The application is not an administrator application of the device. |
| 9200002  | The administrator application does not have permission to manage the device. |
| 9200012  | Parameter verification failed. |
| 201      | Permission verification failed. The application does not have the permission required to call the API. |

**Example**

```ts
import { Want } from '@kit.AbilityKit';
import { networkManager } from '@kit.MDMKit';

let wantTemp: Want = {
  // Replace with actual values.
  bundleName: 'com.example.myapplication',
  abilityName: 'EnterpriseAdminAbility',
};
let config: networkManager.InterfaceConfig = {
  // Replace with actual values.
  "ipSetMode": networkManager.IpSetMode.STATIC,
  "ipAddress": "192.168.1.121",
  "gateway": "192.168.1.1",
  "netMask": "255.255.255.0",
  "dnsServers": "192.168.1.1"
}
let networkInterface: string = "eth0"; // Replace with actual values.
try {
  networkManager.setEthernetConfig(wantTemp, networkInterface, config);
  console.info('Succeeded in setting ethernet config.');
} catch (err) {
  console.error(`Failed to set ethernet config. Code: ${err.code}, message: ${err.message}`);
}
```

## FirewallRule

Represents a firewall rule. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.<br>

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name     | Type                   | Read-only| Optional| Description                                                        |
| --------- | ----------------------- | ---- | ---- |------------------------------------------------------------ |
| srcAddr   | string                  | No  | Yes|Source IP address. An IP address segment, for example, **192.168.0.0/22** or **192.168.1.100-192.168.1.200** is supported.|
| destAddr  | string                  | No  | Yes|Destination IP address. An IP address segment, for example, **192.168.0.0/22** or **192.168.1.100-192.168.1.200** is supported.|
| srcPort   | string                  | No  | Yes|Source port.                                                    |
| destPort  | string                  | No  | Yes|Destination port.                                                  |
| appUid    | string                  | No  | Yes|UID of the application.                                                   |
| direction | [Direction](#direction) | No  | Yes|Direction chains to which the rule applies.<br>This parameter is mandatory when a firewall filtering rule is added.<br>This parameter is optional when a firewall is removed. If this parameter is left empty, all [Direction](#direction) chains are cleared, and **srcAddr**, **destAddr**, **srcPort**, **destPort**, and **appUid** must be also left empty.|
| action    | [Action](#action)       | No  | Yes|Action to take, that is, receive or discard the data packets.<br>This parameter is mandatory when a firewall filtering rule is added.<br>This parameter is optional when a firewall is removed. If this parameter is left empty, all [Action](#action) chains are cleared, and **srcAddr**, **destAddr**, **srcPort**, **destPort**, and **appUid** must be also left empty.|
| protocol  | [Protocol](#protocol)   | No  | Yes|Network protocol. If the value is **ALL** or **ICMP**, the settings of **srcPort** and **destPort** are invalid.|
| family<sup>22+</sup>    | number    | No  | Yes|IP protocol version. The value can be **1** (IPv4) or **2** (IPv6).|

## DomainFilterRule

Represents a domain name filtering rule. IPv4 and IPv6 are supported since API version 22. In API version 21 and earlier versions, only IPv4 is supported.<br>

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name      | Type             | Read-only| Optional| Description                                                        |
| ---------- | ----------------- | ---- | ---- | ------------------------------------------------------------ |
| domainName | string            | No  | Yes|Domain name. This parameter is mandatory when a domain name filtering rule is added. Segment matching is supported. For example, if **domainName** is set to **example.com**, **example.com**, **www.example.com**, and **www.test.example.com** will be matched, while **linkexample.com** will not be matched.                              |
| appUid     | string            | No  | Yes|UID of the application.                                                   |
| action     | [Action](#action) | No  | Yes|Action to take, that is, receive or discard the data packets.<br>This parameter is mandatory when a domain name filtering rule is added.<br>This parameter is optional when a domain name filtering rule is removed. If this parameter is left empty, all [Action](#action) chains are cleared, and **domainName** and **appUid** must be also left empty.|
| direction<sup>15+</sup> | [Direction](#direction) | No| Yes|Direction chains to which the rule applies.<br>This parameter is optional when a domain name filtering rule is added. If this parameter is set to output chain or input chain, the output chain takes effect. If this parameter is set to a forward chain, **appUid** must be empty. Otherwise, error code 401 will be returned.<br>This parameter is optional when a domain name filtering rule is removed. If the value is empty, all [Direction](#direction) chains are cleared, and **domainName** and **appUid** must be empty.|
| family<sup>22+</sup>    | number| No  | Yes|IP protocol version. The value can be **1** (IPv4) or **2** (IPv6).|

## Direction

Enumerates the direction chains to which the rule applies.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name  | Value  | Description    |
| ------ | ---- | -------- |
| INPUT  | 0    | Input chain.|
| OUTPUT | 1    | Output chain.|
| FORWARD<sup>15+</sup> | 2   | Forward chain. |

## Action

Enumerates the actions that can be taken for data packets.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name | Value  | Description        |
| ----- | ---- | ------------ |
| ALLOW | 0    | Receive data packets.|
| DENY  | 1    | Discard data packets.|
| REJECT<sup>15+</sup> | 2 | Reject data packets.|

## Protocol

Enumerates network protocols.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name| Value  | Description          |
| ---- | ---- | -------------- |
| ALL  | 0    | All network protocols.|
| TCP  | 1    | TCP. |
| UDP  | 2    | UDP. |
| ICMP | 3    | ICMP.|

## InterfaceConfig<sup>23+</sup>

Enumerates Ethernet network interface configurations. Only IPv4 is supported.<br>

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name     | Type                   | Read-only| Optional| Description                                                        |
| --------- | ----------------------- | ---- | ---- |------------------------------------------------------------ |
| ipSetMode   | [IpSetMode](#ipsetmode23)                  | No  | No|Ethernet connection configuration mode.|
| ipAddress  | string                  | No  | Yes|Static IP address. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.)|
| gateway  | string                  | No  | Yes|Gateway. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.)|
| netMask  | string                  | No  | Yes|Subnet mask. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.)|
| dnsServers  | string                  | No  | Yes|DNS service address. The value ranges from **0.0.0.0** to **255.255.255.255**. (This parameter is not required in DHCP mode.) Multiple addresses are separated by commas (,).|

## IpSetMode<sup>23+</sup>

Enumerates Ethernet connection configuration modes.

**System capability**: SystemCapability.Customization.EnterpriseDeviceManager


| Name| Value  | Description          |
| ---- | ---- | -------------- |
| STATIC  | 0    | Static configuration of network information for Ethernet connection. When this mode is set, the IP address, subnet mask, default gateway, and DNS server need to be configured synchronously.|
| DHCP  | 1    | Dynamic configuration of network information for Ethernet connection. When this mode is set, the DHCP server in the network automatically assigns the IP address and other related information. |
