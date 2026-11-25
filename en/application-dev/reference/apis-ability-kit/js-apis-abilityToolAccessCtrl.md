# @ohos.abilityToolAccessCtrl (Security Access Fence Service)

<!--Kit: Ability Kit-->
<!--Subsystem: Security-->
<!--Owner: @gcw_3MIoLA9y-->
<!--Designer: @wkr321_ent-->
<!--Tester: @nacyli-->
<!--Adviser: @zengyawen-->
<!-- md-trans-meta sourceCommit=37a41c7e4764d3e7f831e1f47fc28c3acf56e6c1 translatedAt=2026-11-03T13:21:15.704Z pushedAt=2026-11-04T03:19:12.241Z nl=1 -->

The Security Access Fence Service module provides the capability to obtain execution authentication credentials for tools (CLI commands). Through this module, an application can obtain the execution authentication ticket for a CLI tool and its subcommands. If the user has not yet authorized the permissions required by the CLI tool, the API returns the list of permissions that need to be authorized and their statuses; if the user has authorized all required permissions, the API directly returns the authenticated ticket.

Use the APIs of this module when you need to obtain the execution authentication ticket for a CLI tool.

**Since:** 26.1.0

## Modules to Import

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## abilityToolAccessCtrl.requestToolTicket

requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketOpions: TicketOpions): Promise&lt;TicketQueryResult&gt;

Obtains the execution authentication ticket for a CLI tool. This API uses a promise asynchronous callback.

Passes in a list of CLI commands. If the user has not yet authorized the permissions required by the CLI tool, the list of permissions to be authorized and their statuses are returned. If the user has authorized all required permissions, the authenticated ticket is returned.

**Since:** 26.1.0

**Required permissions:** ohos.permission.EXEC_PUBLIC_CLI_TOOL

**System capability**: SystemCapability.Security.Asset

**Parameters**

| Name | Type | Mandatory | Description |
| -------- | -------- | -------- | -------- |
| cliCmdInfos | [CliCmdInfo](#clicmdinfo)[] | Yes | List of CLI commands, specifying the CLI commands and their subcommands for which execution authentication tickets need to be obtained. The array length cannot exceed 300. |
| ticketOpions | [TicketOpions](#ticketopions) | Yes | Optional parameters for generating the ticket, including the ticket expiration time. |

**Returns**

| Type | Description |
| -------- | -------- |
| Promise&lt;[TicketQueryResult](#ticketqueryresult)&gt; | Promise object that returns the ticket query result, including permission status information and the ticket string. |

**Error codes**

For details about the error codes, see [Universal Error Codes](../errorcode-universal.md) and [Security Access Fence Service Error Codes](errorcode-abilityToolAccessCtrl.md).

| ID | Error Message |
| -------- | -------- |
| 201 | Permission denial. The interface caller does not have permission "ohos.permission.EXEC_PUBLIC_CLI_TOOL". |
| 24010000 | Invalid parameter. TicketExpireTime exceeds 60s, etc. |
| 24010001 | Service is abnormal. Possible cause: IPC failed. |
| 24010002 | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| 24010006 | The requested operation is not allowed to be executed while the device is locked. |

**Example**

```ts
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
import { BusinessError } from '@kit.BasicServicesKit';

let cliCmdInfos: abilityToolAccessCtrl.CliCmdInfo[] = [{
  cliCmdName: 'ohos-batteryManager',
  subCliCmdName: 'total-energy'
}];
let ticketOpions: abilityToolAccessCtrl.TicketOpions = {
  ticketExpireTimeMs: 10000
};
abilityToolAccessCtrl.requestToolTicket(cliCmdInfos, ticketOpions).then((data: abilityToolAccessCtrl.TicketQueryResult) => {
  console.info('requestToolTicket success, data: ' + JSON.stringify(data));
  if (data.ticket) {
    // The user has authorized all required permissions, and the authenticated ticket is obtained.
    console.info('ticket: ' + data.ticket);
  } else {
    // The user has not authorized all permissions. View the list of permissions to be authorized.
    for (let i = 0; i < data.permissionResults.length; i++) {
      let permission = data.permissionResults[i].permission;
      let status = data.permissionResults[i].permissionStatus;
      console.info(`permission: ${permission}, status: ${status}`);
    }
  }
}).catch((err: BusinessError): void => {
  console.error(`requestToolTicket fail, code: ${err.code}, message: ${err.message}`);
});
```

## CliCmdInfo

Represents the CLI (Command Line Interface) command information.

**Since**: 26.0.0

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| cliCmdName | string | No | No | CLI command name, used to specify the CLI command. You need to pass in a CLI command name supported by the system, such as 'ohos-batteryManager'.<br>The length cannot exceed 512 bytes and cannot be empty. |
| subCliCmdName | string | No | No | CLI subcommand name, used to specify the CLI subcommand. You need to pass in a subcommand name supported by the specified CLI command, such as 'total-energy'.<br>The length cannot exceed 512 bytes and can be an empty string. |

## TicketOpions

Represents the optional parameters for generating a ticket.

**Since:** 26.1.0

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| ticketExpireTimeMs | number | No | Yes | Expiration time of the ticket, in milliseconds. Value range: 1 to 60000 (60 seconds).<br>Default value: 10000 |

## TicketQueryResult

Represents the ticket query result.

**Since:** 26.1.0

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| permissionResults | abilityAccessCtrl.[PermissionInfo](#permissioninfo)[] | No | No | List of permission status results. When the user has not yet granted the permissions required by the CLI tool, the list of permissions that need to be granted and their statuses is returned. |
| ticket | string | No | No | Ticket string used for permission verification. When the user has granted all required permissions, the authenticated ticket is returned; when the user has not yet granted all permissions, this item is an empty string. |

## PermissionInfo

Represents permission information.

**Since**: 26.0.0

**System capability**: SystemCapability.Security.Asset

| Name | Type | Read-only | Optional | Description |
| -------- | -------- | -------- | -------- | -------- |
| permission | string | No | No | Permission name. For valid permission names, see [Application Permission List](../../security/AccessToken/app-permissions.md). |
| permissionStatus | abilityAccessCtrl.[PermissionStatus](js-apis-abilityAccessCtrl.md#permissionstatus20) | No | No | Permission status. |
<!--no_check-->