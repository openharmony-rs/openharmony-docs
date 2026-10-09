# @ohos.net.netFirewall (Network Firewall)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->
<!-- md-trans-meta sourceCommit=b675ee6f9df522a97fd104e0dc165775ccc2d1c4 translatedAt=2026-09-23T02:09:24.890Z pushedAt=2026-09-24T06:00:14.201Z -->

The **netFirewall** module implements the network firewall functionality for applications. It allows applications to query the firewall interception records of the device.


> **NOTE**
>
> The initial APIs of this module are supported since API version 15. Newly added APIs will be marked with a superscript to indicate their earliest API version.

## Modules to Import

```ts
import { netFirewall } from '@kit.NetworkKit';
```
## netFirewall.setNetFirewallPolicy

setNetFirewallPolicy(userId: number, policy: NetFirewallPolicy): Promise\<void>

Sets the firewall policy for a system user ID, including the firewall switch status and default inbound or outbound behavior (allow or deny). Different firewall policies can be configured for different system user IDs. This API uses a promise to return the result.

> **NOTE**
>
> If this API is called by multiple applications under the same system user, the latest delivered policy prevails.

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name| Type                                   | Mandatory| Description                                        |
| ------ | ----------------------------------------| ---- | -------------------------------------------- |
| userId | number                                  | Yes  | System user ID, which must exist.|
| policy | [NetFirewallPolicy](#netfirewallpolicy) | Yes  | Firewall policy.                          |

**Return value**

| Type               | Description                                    |
| ------------------- | ---------------------------------------- |
| Promise\<void>      | Promise that returns no value.                |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Network Connection Management Error Codes](errorcode-net-connection.md), and [Firewall Error Codes](errorcode-net-netfirewall.md).

| ID| Error Message                                           |
| -------  | ----------------------------------------------------|
| 201      | Permission denied.                                  |
| 401      | Parameter error.                                    |
| 2100001  | Invalid parameter value.                            |
| 2100002  | Operation failed. Cannot connect to service.        |
| 2100003  | System internal error.                              |
| 29400000 | The specified user does not exist.                  |

**Example**

```ts
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let policy: netFirewall.NetFirewallPolicy = {
  isOpen: true,
  inAction: netFirewall.FirewallRuleAction.RULE_DENY,
  outAction: netFirewall.FirewallRuleAction.RULE_ALLOW
};
netFirewall.setNetFirewallPolicy(100, policy).then(() => {
  console.info("set firewall policy success.");
}).catch((error : BusinessError) => {
  console.error("set firewall policy failed: " + JSON.stringify(error));
});
```

## netFirewall.getNetFirewallPolicy

getNetFirewallPolicy(userId: number): Promise\<NetFirewallPolicy>

Queries the firewall policy for a system user ID, including the firewall switch status and default inbound or outbound behavior (allow or deny). This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                  | Mandatory| Description                                          |
| -------- | ---------------------- | ---- | ---------------------------------------------- |
| userId   | number                 | Yes  | System user ID, which must exist.  |

**Return value**

| Type                                             | Description                                 |
| ------------------------------------------------- | ------------------------------------- |
| Promise\<[NetFirewallPolicy](#netfirewallpolicy)> | Promise object used to return the firewall policy of the current user. |


**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Network Connection Management Error Codes](errorcode-net-connection.md), and [Firewall Error Codes](errorcode-net-netfirewall.md).

| ID| Error Message                                           |
| -------  | ----------------------------------------------------|
| 201      | Permission denied.                                  |
| 401      | Parameter error.                                    |
| 2100001  | Invalid parameter value.                            |
| 2100002  | Operation failed. Cannot connect to service.        |
| 2100003  | System internal error.                              |
| 29400000 | The specified user does not exist.                  |

**Example**

```ts
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

netFirewall.getNetFirewallPolicy(100).then((result: netFirewall.NetFirewallPolicy) => {
  console.info('firewall policy: ', JSON.stringify(result));
}, (reason: BusinessError) => {
  console.error('get firewall policy failed: ', JSON.stringify(reason));
});
```

## netFirewall.addNetFirewallRule

addNetFirewallRule(rule: NetFirewallRule): Promise\<number>

Adds a firewall rule for the system user ID. The supported rule types are IP, Domain, and DNS. This API uses a promise to return the result.

> **NOTE**
> 
> 1. Firewall rule priority description (no call order is required between [setNetFirewallPolicy](#netfirewallsetnetfirewallpolicy) and [addNetFirewallRule](#netfirewalladdnetfirewallrule)):
>    - When [setNetFirewallPolicy](#netfirewallsetnetfirewallpolicy) is called to set the default policy to deny and [addNetFirewallRule](#netfirewalladdnetfirewallrule) is called to add explicit rules, the rule priority from high to low is as follows:
>      - Explicit deny rule
>      - Explicit allow rule
>      - Default deny policy
>    - When [setNetFirewallPolicy](#netfirewallsetnetfirewallpolicy) is called to set the default policy to allow and [addNetFirewallRule](#netfirewalladdnetfirewallrule) is called to add explicit rules, the rule priority from high to low is as follows:
>      - Explicit allow rule
>      - Explicit deny rule
>      - Default allow policy
>    - When a firewall IP rule conflicts with a domain rule (the IP resolved from the domain is the same as the IP in the IP rule, and the rule actions conflict):
>      - If the access is performed by domain name, the domain rule takes precedence over the IP rule and is not affected by the rule of the IP resolved from the domain.
>      - If the access is performed by IP address, the following principles apply:
>        - When the domain rule allows access, neither the IP rule nor the default policy can block the access, and the access by IP address is ultimately allowed.
>        - When the domain rule denies access, the allow action of the IP rule or the default policy still takes effect, and the access by IP address is ultimately allowed.
>       - The system identifies domain-based access and IP-based access as follows:
>         - If the destination IP matches an IP address in the system network-layer domain cache table, the application is considered to access by domain name.
>         - If the destination IP does not match any IP address in the system network-layer domain cache table, the application is considered to access by IP address.
>         - The system network layer proactively queries the DNS information configured in the firewall and caches the corresponding IP addresses so that the domain allow rule takes effect.
>        
> 2. Supplementary description of rule types:
>    - When **rule.type** of **addNetFirewallRule** is set to RULE_IP:
>      - If **rule.action** is **RULE_ALLOW** and neither **rule.localIps** nor **rule.remoteIps** is configured, the rule takes effect as allowing all IP segments.
>      - If **rule.action** is **RULE_DENY** and neither **rule.localIps** nor **rule.remoteIps** is configured, the rule takes effect as blocking all IP segments.
>    - When **rule.type** of **addNetFirewallRule** is set to **RULE_DOMAIN**, if **rule.domains** is not configured, the rule does not take effect.
> 3. Description of the upper limit for adding firewall rules:
>    - The upper limit of firewall rules added for a single system user ID is 1000. If this limit is exceeded, error code 29400001 is reported.
>    - The upper limit of the total number of firewall rules added for all system user IDs is 2000. If this limit is exceeded, error code 29400001 is reported.
>    - The upper limit of the total number of wildcard domain rules added for all system user IDs is 100. If this limit is exceeded, error code 29400005 is reported.

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                                             | Mandatory| Description        |
| -------- | ------------------------------------------------- | ---- | ------------ |
| rule    |  [NetFirewallRule](#netfirewallrule)               | Yes  | Firewall rule.|

**Return value**

| Type                                           | Description                                    |
| ------------------------- | ----------------------------------------------------------- |
| Promise\<number>          | Promise object used to return the firewall rule ID, which is automatically generated by the system. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Network Connection Management Error Codes](errorcode-net-connection.md), and [Firewall Error Codes](errorcode-net-netfirewall.md).

| ID| Error Message                                                                |
| -------  | ------------------------------------------------------------------------ |
| 201      | Permission denied.                                                       |
| 401      | Parameter error.                                                         |
| 2100001  | Invalid parameter value.                                                 |
| 2100002  | Operation failed. Cannot connect to service.                             |
| 2100003  | System internal error.                                                   |
| 29400000 | The specified user does not exist.                                       |
| 29400001 | The number of firewall rules exceeds the maximum.                        |
| 29400002 | The number of IP address rules in the firewall rule exceeds the maximum. |
| 29400003 | The number of port rules in the firewall rule exceeds the maximum.       |
| 29400004 | The number of domain rules in the firewall rule exceeds the maximum.     |
| 29400005 | The number of domain rules exceeds the maximum.                          |
| 29400007 | The dns rule is duplication.                                             |

**Example**

```ts
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ipRule: netFirewall.NetFirewallRule = {
  name: "rule1",
  description: "rule1 description",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_IP,
  isEnabled: true,
  appUid: 20001,
  localIps: [
    {
      family: 1,
      type: 1,
      address: "10.10.1.1",
      mask: 32
    },{
      family: 1,
      type: 2,
      startIp: "10.20.1.1",
      endIp: "10.20.1.10"
    }],
  remoteIps:[
    {
      family: 1,
      type: 1,
      address: "20.10.1.1",
      mask: 32
    },{
      family: 1,
      type: 2,
      startIp: "20.20.1.1",
      endIp: "20.20.1.10"
    }],
  protocol: 6,
  localPorts: [
    {
      startPort: 1000,
      endPort: 1000
    },{
      startPort: 2000,
      endPort: 2001
    }],
  remotePorts: [
    {
      startPort: 443,
      endPort: 443
    }],
  userId: 100,
  interface:"wlan0" // Supported since API version 26.0.0.
};
netFirewall.addNetFirewallRule(ipRule).then((result: number) => {
  console.info('rule Id: ', result);
}, (reason: BusinessError) => {
  console.error('add firewall rule failed: ', JSON.stringify(reason));
});

let domainRule: netFirewall.NetFirewallRule = {
  name: "rule2",
  description: "rule2 description",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_DOMAIN,
  isEnabled: true,
  appUid: 20002,
  domains: [
    {
      isWildcard: false,
      domain: "www.example.cn"
    },{
      isWildcard: true,
      domain: "*.example.cn"
    },{
      isWildcard: true,
      domain: "*w.example.cn"  // Supported since API version 26.0.0.
    },{
      isWildcard: true,
      domain: "www.example.*"  // Supported since API version 26.0.0.
    },{
      isWildcard: true,
      domain: "www.example.c*"  // Supported since API version 26.0.0.
    }],
  userId: 100,
  interface:"wlan0" // Supported since API version 26.0.0.
};
netFirewall.addNetFirewallRule(domainRule).then((result: number) => {
  console.info('rule Id: ', result);
}, (reason: BusinessError) => {
  console.error('add firewall rule failed: ', JSON.stringify(reason));
});

let dnsRule: netFirewall.NetFirewallRule = {
  name: "rule3",
  description: "rule3 description",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_DNS,
  isEnabled: true,
  appUid: 20003,
  dns:{
   primaryDns: "4.4.4.4",
   standbyDns: "8.8.8.8",
  },
  userId: 100,
  interface:"wlan0" // Supported since API version 26.0.0.
};
netFirewall.addNetFirewallRule(dnsRule).then((result: number) => {
  console.info('rule Id: ', result);
}, (reason: BusinessError) => {
  console.error('add firewall rule failed: ', JSON.stringify(reason));
});
```
## netFirewall.removeNetFirewallRule

removeNetFirewallRule(userId: number, ruleId: number): Promise\<void>

Deletes a specified firewall rule of a system user ID. This API uses a promise to return the result.

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                            | Mandatory| Description                                        |
| -------- | ----------------------------------- | ---- | -------------------------------------------- |
| userId   | number                              | Yes  | System user ID, which must exist.    |
| ruleId   | number                              | Yes  | ID of the firewall rule.                              |

**Return value**

| Type               | Description                                                                |
| ------------------- | ---------------------------------------------------------------------|
| Promise\<void>      | Promise that returns no value.                                 |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Network Connection Management Error Codes](errorcode-net-connection.md), and [Firewall Error Codes](errorcode-net-netfirewall.md).

| ID| Error Message                                                                       |
| -------  | ------------------------------------------------------------------------------- |
| 201      | Permission denied.                                                              |
| 401      | Parameter error.                                                                |
| 2100001  | Invalid parameter value.                                                        |
| 2100002  | Operation failed. Cannot connect to service.                                    |
| 2100003  | System internal error.                                                          |
| 29400000 | The specified user does not exist.                                              |
| 29400006 | The specified rule does not exist.                                              |

**Example**

```ts
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

netFirewall.removeNetFirewallRule(100, 1).then(() => {
  console.info("delete firewall rule success.");
}).catch((error : BusinessError) => {
  console.error("delete firewall rule failed: " + JSON.stringify(error));
});
```

## netFirewall.updateNetFirewallRule

updateNetFirewallRule(rule: NetFirewallRule): Promise\<void>

Updates a firewall rule. This API uses a promise to return the result.

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name | Type                                  | Mandatory| Description                            |
| ------- | -------------------------------------- | ---- | -------------------------------- |
| rule    | [NetFirewallRule](#netfirewallrule)    | Yes  | Firewall rule.                    |

**Return value**

| Type                | Description                                                               |
| -------------------  | ------------------------------------------------------------------- |
| Promise\<void>       | Promise that returns no value.                                |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Network Connection Management Error Codes](errorcode-net-connection.md), and [Firewall Error Codes](errorcode-net-netfirewall.md).

| ID| Error Message                                                                       |
| -------  | ------------------------------------------------------------------------------- |
| 201      | Permission denied.                                                              |
| 401      | Parameter error.                                                                |
| 2100001  | Invalid parameter value.                                                        |
| 2100002  | Operation failed. Cannot connect to service.                                    |
| 2100003  | System internal error.                                                          |
| 29400000 | The specified user does not exist.                                              |
| 29400002 | The number of IP address rules in the firewall rule exceeds the maximum.        |
| 29400003 | The number of port rules in the firewall rule exceeds the maximum.              |
| 29400004 | The number of domain rules in the firewall rule exceeds the maximum.            |
| 29400005 | The number of domain rules exceeds the maximum.                                 |
| 29400006 | The specified rule does not exist.                                              |
| 29400007 | The dns rule is duplication.                                                    |

**Example**

```ts
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

let ipRuleUpd: netFirewall.NetFirewallRule = {
  id: 1,
  name: "rule1",
  description: "rule1 description update",
  direction: netFirewall.NetFirewallRuleDirection.RULE_IN,
  action:netFirewall.FirewallRuleAction.RULE_DENY,
  type: netFirewall.NetFirewallRuleType.RULE_IP,
  isEnabled: false,
  appUid: 20001,
  localIps: [
    {
      family: 1,
      type: 1,
      address: "10.10.1.1",
      mask: 32
    },{
      family: 1,
      type: 2,
      startIp: "10.20.1.1",
      endIp: "10.20.1.10"
    }],
  userId: 100,
  interface:"wlan0" // Supported since API version 26.0.0.
};
netFirewall.updateNetFirewallRule(ipRuleUpd).then(() => {
  console.info('update firewall rule success.');
}, (reason: BusinessError) => {
  console.error('update firewall rule failed: ', JSON.stringify(reason));
});
```

## netFirewall.getNetFirewallRules

getNetFirewallRules(userId: number, requestParam: RequestParam): Promise\<FirewallRulePage>

Obtains firewall rules by user ID. You need to specify the pagination query parameter when calling this API. Currently, firewall rules can be sorted by name. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name         | Type                         | Mandatory| Description                                        |
| --------------- | ----------------------------- | ---- | -------------------------------------------- |
| userId          | number                        | Yes  | System user ID, which must exist.    |
| requestParam    | [RequestParam](#requestparam) | Yes  | Pagination query parameter. The **orderField** field can be sorted only by firewall rule name.                              |

**Return value**

| Type                                           | Description                                    |
| ----------------------------------------------- | ---------------------------------------- |
| Promise\<[FirewallRulePage](#firewallrulepage)> | Promise object that returns the paginated firewall rule list.    |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Network Connection Management Error Codes](errorcode-net-connection.md), and [Firewall Error Codes](errorcode-net-netfirewall.md).

| ID| Error Message                                                                       |
| -------  | --------------------------------------------------------------------------------|
| 201      | Permission denied.                                                              |
| 401      | Parameter error.                                                                |
| 2100001  | Invalid parameter value.                                                        |
| 2100002  | Operation failed. Cannot connect to service.                                    |
| 2100003  | System internal error.                                                          |
| 29400000 | The specified user does not exist.                                              |

**Example**

```ts
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

## netFirewall.getNetFirewallRule

getNetFirewallRule(userId: number, ruleId: number): Promise\<NetFirewallRule>

Obtains a firewall rule based on the specified user ID and rule ID. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                     | Mandatory| Description                                        |
| -------- | ------------------------- | ---- | -------------------------------------------- |
| userId   | number                    | Yes  | System user ID, which must exist.|
| ruleId   | number                    | Yes  | ID of the firewall rule.                              |

**Return value**

| Type                                           | Description                                    |
| ----------------------------------------------- | ---------------------------------------- |
| Promise\<[NetFirewallRule](#netfirewallrule)>   | Promise used to return the firewall rule.            |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md), [Network Connection Management Error Codes](errorcode-net-connection.md), and [Firewall Error Codes](errorcode-net-netfirewall.md).

| ID| Error Message                                                                       |
| -------  | ------------------------------------------------------------------------------- |
| 201      | Permission denied.                                                              |
| 401      | Parameter error.                                                                |
| 2100001  | Invalid parameter value.                                                        |
| 2100002  | Operation failed. Cannot connect to service.                                    |
| 2100003  | System internal error.                                                          |
| 29400000 | The specified user does not exist.                                              |
| 29400006 | The specified rule does not exist.                                              |

**Example**

```ts
import { netFirewall } from '@kit.NetworkKit';
import { BusinessError } from '@kit.BasicServicesKit';

netFirewall.getNetFirewallRule(100, 1).then((rule: netFirewall.NetFirewallRule) => {
  console.info("result:", JSON.stringify(rule));
}).catch((error : BusinessError) => {
  console.error(" get firewall rules failed: " + JSON.stringify(error));
});
```

## NetFirewallRule

Defines a firewall rule.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name       | Type                                                       |Read-Only| Optional|Description                                                          |
| ------------|-------------------------------------------------------------|----|---|-----------------------------------------------------------  |
| userId      | number                                                      | No|No|System user ID, which must exist.                  |
| name        | string                                                      | No|No|Rule name. This parameter is mandatory and can contain a maximum of 128 characters.                               |
| direction   | [NetFirewallRuleDirection](#netfirewallruledirection)       | No|No|Rule direction, which can be inbound or outbound.                                        |
| action      | [FirewallRuleAction](#firewallruleaction)                   | No|No|Action, which can be allowing or denying.                                                        |
| type        | [NetFirewallRuleType](#netfirewallruletype)                 | No|No|Rule type, which can be IP, Domain, or DNS.                                                   |
| isEnabled   | boolean                                                     | No|No|Whether to enable the rule. The value **true** means to enable the rule, and the value **false** means the opposite.                                                    |
| id          | number                                                      | No|Yes| ID of the firewall rule.                                                      |
| description | string                                                      | No|Yes|Firewall rule description. This parameter is optional and can contain a maximum of 256 characters.                               |
| appUid      | number                                                      | No|Yes|Application or service UID.                                           |
| localIps    | Array\<[NetFirewallIpParams](#netfirewallipparams)>         | No|Yes|Local IP addresses. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.        |
| remoteIps   | Array\<[NetFirewallIpParams](#netfirewallipparams)>         | No|Yes|Remote IP addresses. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.|
| protocol    | number                                                      | No | Yes | Protocol, including TCP: 6, UDP: 17, ICMP: 1, and ICMPv6: 58. Valid when **type=RULE_IP**.  |
| localPorts  | Array\<[NetFirewallPortParams](#netfirewallportparams)>     | No| Yes|Local ports. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 port ranges can be specified.  |
| remotePorts | Array\<[NetFirewallPortParams](#netfirewallportparams)>     | No|Yes|Remote ports. This parameter is valid only when **type** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 port ranges can be specified.  |
| domains     | Array\<[NetFirewallDomainParams](#netfirewalldomainparams)> | No|Yes|List of domain names. This parameter is valid only when **type** is set to **RULE_DOMAIN**. Currently, domain names cannot contain Chinese characters.        |
| dns         | [NetFirewallDnsParams](#netfirewalldnsparams)               | No|Yes|List of DNS server names. This parameter is valid only when **type** is set to **RULE_DNS**. This parameter cannot be empty when **type** is set to **RULE_DNS**.                |
| interface   | string                                                      | No | Yes | Name of the physical network interface card, for example, wlan0. Valid when **type=RULE_IP**; otherwise, it is ignored. Optional, with a maximum of 16 characters.<br>**Since:** 26.0.0<br>**Model restriction:** This API can be used only in the stage model.                 |

## RequestParam

Defines query parameters.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name      | Type                                            | Read-Only|Optional| Description                       |
|------------|--------------------------------------------------|------|-----|----------------------- |
| page       | number                                           | No  |No|Page number. The value range is [1,1000].   |
| pageSize   | number                                           | No |No|Page size. The value range is [1,50]. |
| orderField | [NetFirewallOrderField](#netfirewallorderfield)  | No  |No|Sorting method. This parameter can be used to sort firewall rules only by name.                |
| orderType  | [NetFirewallOrderType](#netfirewallordertype)    | No  |No|Sorting order type.                 |


## FirewallRulePage

Defines the pagination structure for firewall rules.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name      | Type                                       | Read-Only|Optional| Description         |
|------------|-------------------------------------------- |------|----|-----------|
| page       | number                                      | No |No|Current page number. The value range is [1,1000].   |
| pageSize   | number                                      | No |No|Page size. The value range is [1,50].     |
| totalPage  | number                                      | No  |No|Total number of pages. The value range is [1,1000].     |
| data       | Array\<[NetFirewallRule](#netfirewallrule)> | No  |No|Page data.   |

## NetFirewallPolicy

Defines the firewall policy, including the firewall switch status and default inbound or outbound action (allow or deny).

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name      | Type                                      | Read-Only|Optional| Description         |
| -----------| -------------------------------------------|------|----|---------- |
| isOpen     | boolean                                    | No  |No|Whether to enable the firewall. The value **true** means to enable the firewall, and the value **false** means the opposite.|
| inAction   | [FirewallRuleAction](#firewallruleaction)  | No  |No|Inbound action.   |
| outAction  | [FirewallRuleAction](#firewallruleaction)  | No | No|Outbound action.   |


## NetFirewallRuleDirection

Enumerates the firewall rule directions, including inbound and outbound.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Value  | Description  |
|--------------|------|--------|
| RULE_IN      | 1    | Inbound direction.|
| RULE_OUT     | 2    | Outbound direction.|


## FirewallRuleAction

Enumerates the firewall rule actions, including allowing or denying network connections.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name          | Value  | Description  |
|----------------|------|------- |
| RULE_ALLOW     | 0    | Allowing network connection.|
| RULE_DENY      | 1    | Denying network connection.|

## NetFirewallRuleType

Enumerates the firewall rule types, including IP, Domain, and DNS.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name          | Value  | Description        |
|----------------| ---- | ------------ |
| RULE_IP        | 1    | IP address-based firewall rule.  |
| RULE_DOMAIN    | 2    | Domain name-based rule.|
| RULE_DNS       | 3    | DNS-based firewall rule.   |

## NetFirewallOrderField

Enumeration type, the sorting method of firewall rules.
> **NOTE**
> 
> The [getNetFirewallRules](#netfirewallgetnetfirewallrules) API supports only the **ORDER_BY_RULE_NAME** field.<br>

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name                 | Value  | Description                  |
| --------------------- | ---- | --------------------- |
| ORDER_BY_RULE_NAME    | 1    | Sorting of firewall rules by name.|
| ORDER_BY_RECORD_TIME  | 100  | Sorting of firewall rules by time.    |

## NetFirewallOrderType

Enumerates the sorting order of firewall rules, which can be ascending or descending.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name      | Value  | Description                          |
| ---------- | ---- | ------------------------------ |
| ORDER_ASC  | 1    | Sorting in ascending order.|
| ORDER_DESC | 100  | Sorting in descending order.|


## NetFirewallIpParams

Defines the IP parameters of the firewall rule. The IP address type can be IPv4 or IPv6. A single IP address or IP address segment is supported.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name       | Type  |Read-Only|Optional| Description                                            |
| ----------- | -------|----|------|------------------------------------------|
| type        | number | No|No|**1**: IP address or subnet. In this case, the **address** and **mask** fields must be specified. When a single IP address is used, the **mask** field must be set to **32**.<br>**2**: IP address segment. In this case, the **startIp** and **endIp** fields must be specified. |
| family      | number | No| Yes|**1**: IPv4.<br>**2**: IPv6.<br>The default value is **IPv4**. Other values are not supported currently.     |
| address     | string | No| Yes|IP address. This parameter is mandatory and valid only when type is set to **1**.                  |
| mask        | number | No|Yes|IPv4: subnet mask.<br>IPv6: address prefix.<br>This parameter is mandatory and valid only when type is set to **1**.      |
| startIp     | string | No|Yes|Start IP address. This parameter is mandatory and valid only when type is set to **2**. The value ranges from 0.0.0.1 to 255.255.255.254. Otherwise, this parameter will be ignored.                        |
| endIp       | string | No|Yes|End IP address. This parameter is mandatory and valid only when type is set to **2**. The value ranges from 0.0.0.1 to 255.255.255.254. Otherwise, this parameter will be ignored.                       |

## NetFirewallPortParams

Defines the port parameters of a firewall rule.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Type  | Read-Only|Optional| Description      |
| ------------ | -------|------|-----|------ |
| startPort    | number | No  |No|Start port number.|
| endPort      | number | No  |No|End port number.|

## NetFirewallDomainParams

Defines domain name parameters of a firewall rule. Currently, Chinese domain names are not supported.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Type   | Read-Only| Optional|Description                                     |
| ------------ | --------|------|-----|------------------------------------- |
| isWildcard   | boolean | No | No|Whether to contain wildcards. The value **true** means to contain wildcards; and the value **false** means the opposite.                         |
| domain       | string  | No  | No | When **isWildcard** is **false**, a complete domain is required, for example, "www.example.com"; when **isWildcard** is **true**, wildcard rules are supported. For details about the format, see the description below. |

When **isWildcard** is **true**, **domain** supports the wildcard character *"\*"*, which can appear at the beginning, the end, or both the beginning and the end of a domain name, indicating that it matches any character of any length (including zero). The following wildcard formats are supported:

- `"*.xxx.xxx"`: prefix wildcard, matching xxx.xxx and all its subdomains. For example, "*.example.com" can match "example.com", "www.example.com", and "a.b.example.com". (Supported since API version 21)
- `"*xx.xxx.xxx"`: prefix wildcard, matching domain names ending with "xx.xxx.xxx". For example, "*a.example.com" can match "a.example.com" and "www.a.example.com". (Supported since API version 26.0.0)
- `"xxx.xxx.xxx.*"`: suffix wildcard, matching domain names starting with "xxx.xxx.xxx.". For example, "www.example.*" can match "www.example.com" and "www.example.cn". (Supported since API version 26.0.0)
- `"xxx.xxx.xxx.xx*"`: suffix wildcard, matching domain names starting with "xxx.xxx.xxx.xx". For example, "www.example.co*" can match "www.example.com" and "www.example.com.cn". (Supported since API version 26.0.0)

## NetFirewallDnsParams

Defines the DNS information of a firewall rule.

> **NOTE**
>
>  This parameter cannot be empty when **rule.type** of [addNetFirewallRule](#netfirewalladdnetfirewallrule) is set to **RULE_DNS**.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Type   | Read-Only| Optional|Description          |
| ------------ | --------|------|---|------------ |
| primaryDns   | string  | No  |No| Active DNS server.|
| standbyDns   | string  | No  | Yes|Standby DNS server.     |
