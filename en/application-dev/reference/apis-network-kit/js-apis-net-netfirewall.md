# @ohos.net.netFirewall (Network Firewall)

<!--Kit: Network Kit-->
<!--Subsystem: Communication-->
<!--Owner: @wmyao_mm-->
<!--Designer: @guo-min_net-->
<!--Tester: @tongxilin-->
<!--Adviser: @zhang_yixin13-->

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
| Promise\<void>      | Promise that returns no value.               |

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
| Promise\<[NetFirewallPolicy](#netfirewallpolicy)> | Promise used to return the result, which is a firewall policy.|


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

> **Description**
> 
> 1. The following describes the priorities of firewall rules. ([setNetFirePolicy](#netfirewallsetnetfirewallpolicy) and [addNetFirewallRule](#netfirewalladdnetfirewallrule) can be called in any sequence.)<br>
>- Call [setNetFirePolicy](#netfirewallsetnetfirewallpolicy) to set the default policy to **DENY** and call [addNetFirewallRule](#netfirewalladdnetfirewallrule) to add an explicit rule. The priorities of the rules are as follows:<br>
>    - Explicit denying rule<br>
>    - Explicit allowing rule<br>
>    - Default denying policy<br>
>- Call [setNetFirePolicy](#netfirewallsetnetfirewallpolicy) to set the default policy to **ALLOW** and call [addNetFirewallRule](#netfirewalladdnetfirewallrule) to add an explicit rule. The priorities of the rules are as follows:<br>
>    - Explicit allowing rule<br>
>    - Explicit denying rule<br>
>    - Default allowing policy<br>
>- When the IP address rule and domain name rule of the firewall conflict (the IP of the domain name resolution is the same as that in the IP address rule, and the rule behavior conflicts):<br>
>    - If the access is performed using a domain name, the domain name rule has a higher priority than the IP address rule and is not affected by the rule of the IP parsed from the domain name.<br>
>    - If the access is performed using an IP address, the following rules are followed:<br>
>      - If the domain name rule allows the access and the domain name resolution has been performed, the IP address denying rule or the default denying policy will not take effect, and the access using the IP address will be allowed.<br>
>      - If the domain name rule allows the access and the domain name resolution has not been performed, the IP address denying rule or the default denying policy will take effect, and the access using the IP address will be denied.<br>
>      - If the domain name rule denies the access, the IP address allowing rule or the default policy will take effect, and the access using the IP address will be allowed.<br>
> 2. Supplementary description of rule types:<br>
>- When the input parameter **rule.type** of **addNetFirewallRule** is set to **RULE_IP**:<br>
>    - If **rule.action** is set to **RULE_ALLOW** and **rule.localIps** and **rule.remoteIps** are not configured, the rule takes effect as full IP range access is allowed.<br>
>    - If **rule.action** is set to **RULE_DENY** and **rule.localIps** and **rule.remoteIps** are not configured, the rule takes effect as full IP range access is denied.<br>
>- If **rule.type** of **addNetFirewallRule** is set to **RULE_DOMAIN** and **rule.domains** is not configured, the rule does not take effect.<br>
> 3. Description of the upper limit for adding firewall rules:<br>
>- A maximum of 1000 firewall rules can be added for a single system user ID. If this limit is exceeded, error code **29400001** is reported.<br>
>- A maximum of 2000 firewall rules can be added for all system user IDs. If this limit is exceeded, error code **29400001** is reported.<br>
>- A maximum of 100 fuzzy domain name rules can be added for all system user IDs. If this limit is exceeded, error code **29400005** is reported.<br>

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                                             | Mandatory| Description        |
| -------- | ------------------------------------------------- | ---- | ------------ |
| rule    |  [NetFirewallRule](#netfirewallrule)               | Yes  | Firewall rule.|

**Return value**

| Type                                           | Description                                    |
| ------------------------- | ----------------------------------------------------------- |
| Promise\<number>          | Promise used to return the result, which is the firewall rule ID automatically generated by the system.|

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
  userId: 100
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
    }],
  userId: 100
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
  userId: 100
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
| Promise\<void>      | Promise that returns no value.                                |

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
| Promise\<void>       | Promise that returns no value.                               |

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
  userId: 100
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
| Promise\<[FirewallRulePage](#firewallrulepage)> | Promise used to return the result, which is list of firewall rules.   |

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
| Promise\<[NetFirewallRule](#netfirewallrule)>   | Promise used to return the result, which is a firewall rule.           |

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
| action      | [FirewallRuleAction](#firewallruleaction)                   | No|No|Action, which can be allow or deny.                                                        |
| type        | [NetFirewallRuleType](#netfirewallruletype)                 | No|No|Rule type, which can be IP, Domain, or DNS.                                                   |
| isEnabled   | boolean                                                     | No|No|Whether to enable the rule. The value **true** means to enable the rule, and the value **false** means the opposite.                                                    |
| id          | number                                                      | No|Yes| ID of the firewall rule.                                                      |
| description | string                                                      | No|Yes|Firewall rule description. This parameter is optional and can contain a maximum of 256 characters.                               |
| appUid      | number                                                      | No|Yes|Application or service UID.                                           |
| localIps    | Array\<[NetFirewallIpParams](#netfirewallipparams)>         | No|Yes|Local IP addresses. This parameter is valid only when **ruleType** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.        |
| remoteIps   | Array\<[NetFirewallIpParams](#netfirewallipparams)>         | No|Yes|Remote IP addresses. This parameter is valid only when **ruleType** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.|
| protocol    | number                                                      | No| Yes|Protocol, which can be TCP (value **6**) or UDP (value **17**). This parameter is valid only when **ruleType** is set to **RULE_IP**. |
| localPorts  | Array\<[NetFirewallPortParams](#netfirewallportparams)>     | No| Yes|Local ports. This parameter is valid only when **ruleType** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 IP addresses can be specified.  |
| remotePorts | Array\<[NetFirewallPortParams](#netfirewallportparams)>     | No|Yes|Remote ports. This parameter is valid only when **ruleType** is set to **RULE_IP**. Otherwise, it will be ignored. A maximum of 10 ports can be specified.  |
| domains     | Array\<[NetFirewallDomainParams](#netfirewalldomainparams)> | No|Yes|List of domain names. This parameter is valid only when **ruleType** is set to **RULE_DOMAIN**. Currently, domain names cannot contain Chinese characters.        |
| dns         | [NetFirewallDnsParams](#netfirewalldnsparams)               | No|Yes|List of DNS server names. This parameter is valid only when **ruleType** is set to **RULE_DNS**. This parameter cannot be empty when ruleType is set to RULE_DNS.                |

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

Enumerates the sorting methods of firewall rules.
> **Description**
> 
> [getNetFirewallRules](#netfirewallgetnetfirewallrules) supports only the **ORDER_BY_RULE_NAME** field.<br>

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
| domain       | string  | No |No|If **isWildcard** is set to **false**, the complete domain name, for example, "www.example.cn", needs to be specified.|

## NetFirewallDnsParams

Defines the DNS information of a firewall rule.

 > **Description**
 >
 >  This parameter cannot be empty when **rule.type** of [addNetFirewallRule](#netfirewalladdnetfirewallrule) is set to RULE_DNS.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Type   | Read-Only| Optional|Description          |
| ------------ | --------|------|---|------------ |
| primaryDns   | string  | No  |No| Active DNS server.|
| standbyDns   | string  | No  | Yes|Standby DNS server.     |
