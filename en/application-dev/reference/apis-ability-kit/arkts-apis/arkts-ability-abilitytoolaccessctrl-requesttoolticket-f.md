# requestToolTicket

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## requestToolTicket

```TypeScript
export function requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketOpions: TicketOpions): Promise<TicketQueryResult>
```

Obtain the execution authentication ticket for CLI tools. This function retrieves the execution authentication ticket for CLI tools and their subcommands. If the user has not yet authorized the permissions required by CLI tools, a list of permissions requiring authorization along with their status will be returned. If all permissions required by CLI tools have been authorized by the user, the authenticated ticket will be returned.

**Since:** 26.2.0

**Required permissions:** ohos.permission.EXEC_PUBLIC_CLI_TOOL

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-abilityToolAccessCtrl-export function requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketOpions: TicketOpions): Promise<TicketQueryResult>--><!--Device-abilityToolAccessCtrl-export function requestToolTicket(cliCmdInfos: CliCmdInfo[], ticketOpions: TicketOpions): Promise<TicketQueryResult>-End-->

**System capability:** SystemCapability.Security.Asset

**Parameters:**

| Name | Type | Mandatory | Description |
| --- | --- | --- | --- |
| cliCmdInfos | [CliCmdInfo](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i.md)[] | Yes | CLI command list. |
| ticketOpions | [TicketOpions](arkts-ability-abilitytoolaccessctrl-ticketopions-i.md) | Yes | generate ticket options. |

**Return value:**

| Type | Description |
| --- | --- |
| Promise&lt;[TicketQueryResult](arkts-ability-abilitytoolaccessctrl-ticketqueryresult-i.md)&gt; | Promise used to return ${TicketQueryResult}。 |

**Error codes:**

| Error Code ID | Error Message |
| --- | --- |
| [201](../../errorcode-universal.md#201-permission-denied) | Permission denial. The interface caller does not have permission "ohos.permission.EXEC_PUBLIC_CLI_TOOL". |
| [24010000](../errorcode-abilityToolAccessCtrl-sys.md#24010000-invalid-parameter) | Invalid parameter. TicketExpireTime exceeds 60s, etc. |
| [24010001](../errorcode-abilityToolAccessCtrl-sys.md#24010001-system-service-abnormal) | Service is abnormal. Possible cause: IPC failed. |
| [24010002](../errorcode-abilityToolAccessCtrl-sys.md#24010002-internal-service-error) | Common internal error. Possible cause: dependent service unavailable, resource access failure, etc. |
| [24010006](../errorcode-abilityToolAccessCtrl-sys.md#24010006-operation-not-allowed-while-the-device-is-locked) | The requested operation is not allowed to be executed while the device is locked. |
