# @ohos.abilityToolAccessCtrl(This module provides the capabilities of tools access control)

This module provides permission management capabilities for tools (CLI commands and APIs), including permission query, user authorization, and remote authorization. Permission query is used to check the permission status of tools, user authorization grants permissions to tools based on user decisions, and remote authorization enables cross-device permission management through a ticket mechanism.

**Since:** 26.0.0

**Model restriction:** This API can be used in both the stage model and FA model.

<!--Device-unnamed-declare namespace abilityToolAccessCtrl--><!--Device-unnamed-declare namespace abilityToolAccessCtrl-End-->

**System capability:** SystemCapability.Security.Asset

## Modules to Import

```TypeScript
import { abilityToolAccessCtrl } from '@kit.AbilityKit';
```

## Summary

### Functions

| Name | Description |
| --- | --- |
| [queryControlAppStatus](arkts-ability-abilitytoolaccessctrl-querycontrolappstatus-f.md#querycontrolappstatus-1) | Queries the control permission status for the specified applications. This function checks whether each application in the input list is allowed or denied to be controlled by external tools. The result list corresponds to the input order. |
| [requestControlAppPermissionFromUser](arkts-ability-abilitytoolaccessctrl-requestcontrolapppermissionfromuser-f.md#requestcontrolapppermissionfromuser-1) | Requests the control permission for the specified applications from the user. This function displays a user dialog to obtain authorization decisions for controlling each application. The result reflects the user's allow or deny decision for each app. |
| [requestToolTicket](arkts-ability-abilitytoolaccessctrl-requesttoolticket-f.md#requesttoolticket-1) | Obtain the execution authentication ticket for CLI tools. This function retrieves the execution authentication ticket for CLI tools and their subcommands. If the user has not yet authorized the permissions required by CLI tools, a list of permissions requiring authorization along with their status will be returned. If all permissions required by CLI tools have been authorized by the user, the authenticated ticket will be returned. |

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [generateControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrolleddevicepackage-f-sys.md#generatecontrolleddevicepackage-1) | Generates an authorization package for the controlled device. This function generates a remote authorization package based on the permission query list. The generated package can be sent to the controller device for permission verification. |
| [generateControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrollerdevicepackage-f-sys.md#generatecontrollerdevicepackage-1) | Generates an authorization package for the controller device. This function generates a remote authorization package based on the remote user authorization results. The generated package can be sent to the controlled device for permission verification. |
| [generateTaskChallenge](arkts-ability-abilitytoolaccessctrl-generatetaskchallenge-f-sys.md#generatetaskchallenge-1) | Generate the challenge for task auth token generation. This function generates a challenge based on task identity info. |
| [generateTaskIdentity](arkts-ability-abilitytoolaccessctrl-generatetaskidentity-f-sys.md#generatetaskidentity-1) | Generate the task-based authentication identity for agent commands. This function generates a authentication identity based on caller identity and basic task attributes, such as task ID and task expire time. |
| [getRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-getremotegrantstatus-f-sys.md#getremotegrantstatus-1) | Gets the remote grant status. This function queries whether the remote authorization feature is enabled or disabled. When enabled, the device can grant permissions to remote devices; when disabled, remote authorization is not allowed. |
| [grantToolPermissionsByUser](arkts-ability-abilitytoolaccessctrl-granttoolpermissionsbyuser-f-sys.md#granttoolpermissionsbyuser-1) | Grants tool permissions based on user authorization results. This function grants permissions for tools (CLI commands or APIs) according to the user's authorization decisions. After successful authorization, tickets are generated which can be used for permission verification. |
| [requestToolPermissions](arkts-ability-abilitytoolaccessctrl-requesttoolpermissions-f-sys.md#requesttoolpermissions-1) | Queries tool permissions based on the specified operations. This function checks the permission status for CLI commands or APIs specified in permissionQuery.operationInfo. For each operation, it returns the permission status, authorization status, and whether a user dialog is required. When needTicket is set to true, a ticket will be generated for remote authorization. |
| [revokeTaskIdentity](arkts-ability-abilitytoolaccessctrl-revoketaskidentity-f-sys.md#revoketaskidentity-1) | Batch revoke task authentication identities for agent commands. This function batch revokes the task authentication identities and deletes the local cache of task attributes. |
| [updateRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-updateremotegrantstatus-f-sys.md#updateremotegrantstatus-1) | Updates the remote grant status. This function enables or disables the remote authorization feature. When enabled, the device can grant permissions to remote devices; when disabled, remote authorization is not allowed. |
| [verifyControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrolleddevicepackage-f-sys.md#verifycontrolleddevicepackage-1) | Verifies the authorization package from the controlled device. This function verifies the remote authorization package sent by the controlled device. It validates the ticket to ensure the authorization is legitimate. |
| [verifyControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrollerdevicepackage-f-sys.md#verifycontrollerdevicepackage-1) | Verifies the authorization package from the controller device. This function verifies the remote authorization package sent by the controller device. It validates the ticket and remote device information to ensure the authorization is legitimate. |
<!--DelEnd-->

### Interfaces

| Name | Description |
| --- | --- |
| [AppInfo](arkts-ability-abilitytoolaccessctrl-appinfo-i.md) | Information about an application. |
| [CliCmdInfo](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i.md) | CLI command information. |
| [ControlAppStatusResult](arkts-ability-abilitytoolaccessctrl-controlappstatusresult-i.md) | Control permission status result for an application. |
| [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i.md) | Permission information. |
| [TicketParams](arkts-ability-abilitytoolaccessctrl-ticketparams-i.md) | Parameters for the ticket. |
| [TicketQueryResult](arkts-ability-abilitytoolaccessctrl-ticketqueryresult-i.md) | Ticket query result. |

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AuthStatusInfo](arkts-ability-abilitytoolaccessctrl-authstatusinfo-i-sys.md) | Authorization status information. |
| [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md) | Operation information. |
| [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i-sys.md) | Permission information. |
| [PermissionQuery](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md) | Permission query information. |
| [PermissionQueryResult](arkts-ability-abilitytoolaccessctrl-permissionqueryresult-i-sys.md) | Permission query result. |
| [RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md) | Remote authorization package. |
| [RemoteControlParams](arkts-ability-abilitytoolaccessctrl-remotecontrolparams-i-sys.md) | Interaction params for remote control |
| [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md) | Remote device information. |
| [RemoteUserAuthItem](arkts-ability-abilitytoolaccessctrl-remoteuserauthitem-i-sys.md) | Remote user authorization item. |
| [RemoteUserAuthResults](arkts-ability-abilitytoolaccessctrl-remoteuserauthresults-i-sys.md) | Remote user authorization results. |
| [TaskIdentity](arkts-ability-abilitytoolaccessctrl-taskidentity-i-sys.md) | Task identity. |
| [TaskIdentityInfo](arkts-ability-abilitytoolaccessctrl-taskidentityinfo-i-sys.md) | Task identity input info used to generate TaskIdentity. |
| [TicketInfo](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md) | Ticket information. |
| [UserAuthResult](arkts-ability-abilitytoolaccessctrl-userauthresult-i-sys.md) | User authorization result. |
<!--DelEnd-->

### Enums

| Name | Description |
| --- | --- |
| [ControlAppStatus](arkts-ability-abilitytoolaccessctrl-controlappstatus-e.md) | Control permission status. |

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthStatus](arkts-ability-abilitytoolaccessctrl-authstatus-e-sys.md) | Authorization status. |
| [ExecuteType](arkts-ability-abilitytoolaccessctrl-executetype-e-sys.md) | Task execute type. |
| [OperationType](arkts-ability-abilitytoolaccessctrl-operationtype-e-sys.md) | Operation type. |
| [RemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-remotegrantstatus-e-sys.md) | Remote grant status. |
| [Role](arkts-ability-abilitytoolaccessctrl-role-e-sys.md) | Device role. |
<!--DelEnd-->
