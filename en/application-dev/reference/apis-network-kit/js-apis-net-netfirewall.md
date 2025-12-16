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


## netFirewall.getNetFirewallPolicy

getNetFirewallPolicy(userId: number): Promise\<NetFirewallPolicy>

Obtains a firewall policy. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                  | Mandatory| Description                                          |
| -------- | ---------------------- | ---- | ---------------------------------------------- |
| userId   | number                 | Yes  | Existing user ID.  |

**Return value**

| Type                                             | Description                                 |
| ------------------------------------------------- | ------------------------------------- |
| Promise\<[NetFirewallPolicy](#netfirewallpolicy)> | Promise used to return the result, which is a firewall policy.|


**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

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

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

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
      mask: 24
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
 
## netFirewall.removeNetFirewallRule

removeNetFirewallRule(userId: number, ruleId: number): Promise\<void>

Removes a firewall rule. This API uses a promise to return the result.

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                            | Mandatory| Description                                        |
| -------- | ----------------------------------- | ---- | -------------------------------------------- |
| userId   | number                              | Yes  | Existing user ID.    |
| ruleId   | number                              | Yes  | ID of the firewall rule.                              |

**Return value**

| Type               | Description                                                                |
| ------------------- | ---------------------------------------------------------------------|
| Promise\<void>      | Promise that returns no value.                                |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

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
   
## netFirewall.getNetFirewallRules

getNetFirewallRules(userId: number, requestParam: RequestParam): Promise\<FirewallRulePage>

Obtains firewall rules by user ID. You need to specify the pagination query parameter when calling this API. This API uses a promise to return the result.

**Required permission**: ohos.permission.GET_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name         | Type                         | Mandatory| Description                                        |
| --------------- | ----------------------------- | ---- | -------------------------------------------- |
| userId          | number                        | Yes  | Existing user ID.    |
| requestParam    | [RequestParam](#requestparam) | Yes  | Pagination query parameter.                              |

**Return value**

| Type                                           | Description                                    |
| ----------------------------------------------- | ---------------------------------------- |
| Promise\<[FirewallRulePage](#firewallrulepage)> | Promise used to return the result, which is list of firewall rules.   |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

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
| userId   | number                    | Yes  | Existing user ID.|
| ruleId   | number                    | Yes  | ID of the firewall rule.                              |

**Return value**

| Type                                           | Description                                    |
| ----------------------------------------------- | ---------------------------------------- |
| Promise\<[NetFirewallRule](#netfirewallrule)>   | Promise used to return the result, which is a firewall rule.           |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

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

## netFirewall.setNetFirewallPolicy

setNetFirewallPolicy(userId: number, policy: NetFirewallPolicy): Promise\<void>

Sets a firewall policy. This API uses a promise to return the result.

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name| Type                                   | Mandatory| Description                                        |
| ------ | ----------------------------------------| ---- | -------------------------------------------- |
| userId | number                                  | Yes  | Existing user ID.|
| policy | [NetFirewallPolicy](#netfirewallpolicy) | Yes  | Firewall policy.                          |

**Return value**

| Type               | Description                                    |
| ------------------- | ---------------------------------------- |
| Promise\<void>      | Promise that returns no value.               |

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

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

## netFirewall.addNetFirewallRule

addNetFirewallRule(rule: NetFirewallRule): Promise\<number>

Adds a firewall rule. This API uses a promise to return the result.

**Required permission**: ohos.permission.MANAGE_NET_FIREWALL

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

**Parameters**

| Name  | Type                                             | Mandatory| Description        |
| -------- | ------------------------------------------------- | ---- | ------------ |
| rule    |  [NetFirewallRule](#netfirewallrule)               | Yes  | Firewall rule.|

**Return value**

| Type                     | Description                    	                                  |
| ------------------------- | ----------------------------------------------------------- |
| Promise\<number>          | Promise used to return the result, which is the firewall rule ID automatically generated by the system.|

**Error codes**

For details about the error codes, see [Network Connection Management Error Codes](errorcode-net-connection.md) and [Universal Error Codes](../errorcode-universal.md).

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
      mask: 24
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
      mask: 24
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

## NetFirewallRule

Defines a firewall rule.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name       | Type                                                       |Read-Only| Optional|Description                                                          |
| ------------|-------------------------------------------------------------|----|---|-----------------------------------------------------------  |
| userId      | number                                                      | No|No|Existing user ID.                  |
| name        | string                                                      | No|No|Rule name. This parameter is mandatory and can contain a maximum of 128 characters.                               |
| direction   | [NetFirewallRuleDirection](#netfirewallruledirection)       | No|No|Interception direction, which can be inbound or outbound.                                        |
| action      | [FirewallRuleAction](#firewallruleaction)                   | No|No|Action.                                                        |
| type        | [NetFirewallRuleType](#netfirewallruletype)                 | No|No|Rule type.                                                    |
| isEnabled   | boolean                                                     | No|No|Whether to enable the rule. The value **true** means to enable the rule, and the value **false** means the opposite.                                                    |
| id          | number                                                      | No|Yes| Firewall rule ID.                                                      |
| description | string                                                      | No|Yes|Firewall rule description. This parameter is optional and can contain a maximum of 256 characters.                               |
| appUid      | number                                                      | No|Yes|Application or service UID.                                           |
| localIps    | Array\<[NetFirewallIpParams](#netfirewallipparams)>         | No|Yes|List of local IP addresses. This parameter is valid when **ruleType** is set to **RULE_IP**. A maximum of 10 local IP addresses are supported.        |
| remoteIps   | Array\<[NetFirewallIpParams](#netfirewallipparams)>         | No|Yes|List of remote IP addresses. This parameter is valid when **ruleType** is set to **RULE_IP**. A maximum of 10 local IP addresses are supported.|
| protocol    | number                                                      | No| Yes|Protocol. The value **6** indicates TCP and value **17** indicates UDP. This parameter is valid only when **ruleType** is set to **RULE_IP**. |
| localPorts  | Array\<[NetFirewallPortParams](#netfirewallportparams)>     | No| Yes|List of local ports. This parameter is valid when **ruleType** is set to **RULE_IP**. A maximum of 10 local ports are supported.  |
| remotePorts | Array\<[NetFirewallPortParams](#netfirewallportparams)>     | No|Yes|List of remote ports. This parameter is valid when **ruleType** is set to **RULE_IP**. A maximum of 10 remote ports are supported.  |
| domains     | Array\<[NetFirewallDomainParams](#netfirewalldomainparams)> | No|Yes|List of domain names. This parameter is valid only when **ruleType** is set to **RULE_DOMAIN**.        |
| dns         | [NetFirewallDnsParams](#netfirewalldnsparams)               | No|Yes|List of DNS server names. This parameter is valid only when **ruleType** is set to **RULE_DNS**.                 |

## RequestParam

Defines query parameters.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name      | Type                                            | Read-Only|Optional| Description                       |
|------------|--------------------------------------------------|------|-----|----------------------- |
| page       | number                                           | No  |No|Page number. The value range is [1,1000].   |
| pageSize   | number                                           | No |No|Page size. The value range is [1,50]. |
| orderField | [NetFirewallOrderField](#netfirewallorderfield)  | No  |No|Sorting order field.                 |
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

Defines a firewall policy.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name      | Type                                      | Read-Only|Optional| Description         |
| -----------| -------------------------------------------|------|----|---------- |
| isOpen     | boolean                                    | No  |No|Whether to enable the firewall. The value **true** means to enable the firewall, and the value **false** means the opposite.|
| inAction   | [FirewallRuleAction](#firewallruleaction)  | No  |No|Inbound action.   |
| outAction  | [FirewallRuleAction](#firewallruleaction)  | No | No|Outbound action.   |


## NetFirewallRuleDirection

Enumerates interception directions for firewall rules.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Value  | Description  |
|--------------|------|--------|
| RULE_IN      | 1    | Inbound direction.|
| RULE_OUT     | 2    | Outbound direction.|


## FirewallRuleAction

Enumerates actions for firewall rules.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name          | Value  | Description  |
|----------------|------|------- |
| RULE_ALLOW     | 0    | Allowing network connection.|
| RULE_DENY      | 1    | Denying network connection.|

## NetFirewallRuleType

Enumerates firewall rule types.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name          | Value  | Description        |
|----------------| ---- | ------------ |
| RULE_IP        | 1    | IP address-based firewall rule.  |
| RULE_DOMAIN    | 2    | Domain name-based rule.|
| RULE_DNS       | 3    | DNS-based firewall rule.   |

## NetFirewallOrderField

Enumerates firewall rule sorting types.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name                 | Value  | Description                  |
| --------------------- | ---- | --------------------- |
| ORDER_BY_RULE_NAME    | 1    | Sorting of firewall rules by name.|
| ORDER_BY_RECORD_TIME  | 100  | Sorting of firewall rules by time.    |

## NetFirewallOrderType

Enumerates firewall rule sorting orders.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name      | Value  | Description                          |
| ---------- | ---- | ------------------------------ |
| ORDER_ASC  | 1    | Sorting in ascending order.|
| ORDER_DESC | 100  | Sorting in descending order.|


## NetFirewallIpParams

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name       | Type  |Read-Only|Optional| Description                                            |
| ----------- | -------|----|------|------------------------------------------|
| type        | number | No|No|**1**: IP address or subnet. When a single IP address is used, the mask is 32.<br>**2**: IP address segment. |
| family      | number | No| Yes|**1**: The IP address family is **IPv4**.<br>**2**: The IP address family is **IPv6**.<br>The default value is **IPv4**. Other values are not supported currently.     |
| address     | string | No| Yes|IP address. This parameter is mandatory and valid only when type is set to **1**.                  |
| mask        | number | No|Yes|IPv4: subnet mask.<br>IPv6: address prefix.<br>This parameter is mandatory and valid only when type is set to **1**.      |
| startIp     | string | No|Yes|Start IP address. This parameter is mandatory and valid only when type is set to **2**.                        |
| endIp       | string | No|Yes|End IP address. This parameter is mandatory and valid only when type is set to **2**.                       |

## NetFirewallPortParams

Defines the port parameters of a firewall rule.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Type  | Read-Only|Optional| Description      |
| ------------ | -------|------|-----|------ |
| startPort    | number | No  |No|Start port number.|
| endPort      | number | No  |No|End port number.|

## NetFirewallDomainParams

Defines the domain information of a firewall rule.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Type   | Read-Only| Optional|Description                                     |
| ------------ | --------|------|-----|------------------------------------- |
| isWildcard   | boolean | No | No|Whether to contain wildcards. The value **true** means to contain wildcards; and the value **false** means the opposite.                         |
| domain       | string  | No |No|DNS domain. If **isWildcard** is **false**, you need to specify the complete domain name.|

## NetFirewallDnsParams

Defines the DNS information of a firewall rule.

**System capability**: SystemCapability.Communication.NetManager.NetFirewall

| Name        | Type   | Read-Only| Optional|Description          |
| ------------ | --------|------|---|------------ |
| primaryDns   | string  | No  |No| Active DNS server.|
| standbyDns   | string  | No  | Yes|Standby DNS server.     |
