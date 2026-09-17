# @ohos.abilityToolAccessCtrl(This module provides the capabilities of tools access control)

This module provides permission management capabilities for tools (CLI commands and APIs), including permission query, user authorization, and remote authorization. Permission query is used to check the permission status of tools, user authorization grants permissions to tools based on user decisions, and remote authorization enables cross-device permission management through a ticket mechanism.

**Since:** 26.0.0

**System capability:** SystemCapability.Security.Asset

**System API:** This is a system API.

## Modules to Import

```TypeScript
```

## Summary

<!--Del-->
### Functions(System API)

| Name | Description |
| --- | --- |
| [generateControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrolleddevicepackage-f-sys.md) | Generates an authorization package for the controlled device. This function generates a remote authorization package based on the permission query list. The generated package can be sent to the controller device for permission verification. |
| [generateControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrollerdevicepackage-f-sys.md) | Generates an authorization package for the controller device. This function generates a remote authorization package based on the remote user authorization results. The generated package can be sent to the controlled device for permission verification. |
| [getRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-getremotegrantstatus-f-sys.md) | Gets the remote grant status. This function queries whether the remote authorization feature is enabled or disabled. When enabled, the device can grant permissions to remote devices; when disabled, remote authorization is not allowed. |
| [grantToolPermissionsByUser](arkts-ability-abilitytoolaccessctrl-granttoolpermissionsbyuser-f-sys.md) | Grants tool permissions based on user authorization results. This function grants permissions for tools (CLI commands or APIs) according to the user's authorization decisions. After successful authorization, tickets are generated which can be used for permission verification. |
| [requestToolPermissions](arkts-ability-abilitytoolaccessctrl-requesttoolpermissions-f-sys.md) | Queries tool permissions based on the specified operations. This function checks the permission status for CLI commands or APIs specified in permissionQuery.operationInfo. For each operation, it returns the permission status, authorization status, and whether a user dialog is required. When needTicket is set to true, a ticket will be generated for remote authorization. |
| [updateRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-updateremotegrantstatus-f-sys.md) | Updates the remote grant status. This function enables or disables the remote authorization feature. When enabled, the device can grant permissions to remote devices; when disabled, remote authorization is not allowed. |
| [verifyControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrolleddevicepackage-f-sys.md) | Verifies the authorization package from the controlled device. This function verifies the remote authorization package sent by the controlled device. It validates the ticket to ensure the authorization is legitimate. |
| [verifyControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrollerdevicepackage-f-sys.md) | Verifies the authorization package from the controller device. This function verifies the remote authorization package sent by the controller device. It validates the ticket and remote device information to ensure the authorization is legitimate. |
<!--DelEnd-->

<!--Del-->
### Interfaces(System API)

| Name | Description |
| --- | --- |
| [AuthStatusInfo](arkts-ability-abilitytoolaccessctrl-authstatusinfo-i-sys.md) | Authorization status information. |
| [CliCmdInfo](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i-sys.md) | CLI command information. |
| [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md) | Operation information. |
| [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i-sys.md) | Permission information. |
| [PermissionQuery](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md) | Permission query information. |
| [PermissionQueryResult](arkts-ability-abilitytoolaccessctrl-permissionqueryresult-i-sys.md) | Permission query result. |
| [RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md) | Remote authorization package. |
| [RemoteControlParams](arkts-ability-abilitytoolaccessctrl-remotecontrolparams-i-sys.md) | Interaction params for remote control |
| [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md) | Remote device information. |
| [RemoteUserAuthItem](arkts-ability-abilitytoolaccessctrl-remoteuserauthitem-i-sys.md) | Remote user authorization item. |
| [RemoteUserAuthResults](arkts-ability-abilitytoolaccessctrl-remoteuserauthresults-i-sys.md) | Remote user authorization results. |
| [TicketInfo](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md) | Ticket information. |
| [UserAuthResult](arkts-ability-abilitytoolaccessctrl-userauthresult-i-sys.md) | User authorization result. |
<!--DelEnd-->

<!--Del-->
### Enums(System API)

| Name | Description |
| --- | --- |
| [AuthStatus](arkts-ability-abilitytoolaccessctrl-authstatus-e-sys.md) | Authorization status. |
| [OperationType](arkts-ability-abilitytoolaccessctrl-operationtype-e-sys.md) | Operation type. |
| [RemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-remotegrantstatus-e-sys.md) | Remote grant status. |
| [Role](arkts-ability-abilitytoolaccessctrl-role-e-sys.md) | Device role. |
<!--DelEnd-->
