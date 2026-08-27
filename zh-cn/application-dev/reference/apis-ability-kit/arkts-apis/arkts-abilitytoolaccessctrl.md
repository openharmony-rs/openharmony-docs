# @ohos.abilityToolAccessCtrl(This module provides the capabilities of tools access control)

abilityToolAccessCtrl的命名空间

**起始版本：** 26.0.0

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## 导入模块

```TypeScript
```

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [generateControlledDevicePackage(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-generatecontrolleddevicepackage-f-sys.md) | 生成受控设备的授权包。 根据权限查询列表生成远程授权包。 生成的包可以发送到控制器设备进行权限验证。 |
| [generateControllerDevicePackage(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-generatecontrollerdevicepackage-f-sys.md) | 生成控制器设备的授权包。 根据远程用户授权结果生成远程授权包。 生成的包可以发送到受控设备进行权限验证。 |
| [getRemoteGrantStatus(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-getremotegrantstatus-f-sys.md) | 获取远程授权状态。 该功能用于查询远程授权特性的使能状态。 启用时，设备可以向远程设备授予权限； 禁用时，不允许远程授权。 |
| [grantToolPermissionsByUser(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-granttoolpermissionsbyuser-f-sys.md) | 根据用户授权结果授予工具权限。 该功能根据用户的授权决定授予工具（CLI命令或API）的权限。 授权成功后，会生成工单，用于权限验证。 |
| [requestToolPermissions(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-requesttoolpermissions-f-sys.md) | 根据指定的操作查询工具权限。 该函数用于检查权限查询中指定的CLI命令或API的权限状态。 对于每个操作，它返回权限状态、授权状态以及是否需要用户对话框。 当needTicket设置为true时，远程授权会生成一个票据。 |
| [updateRemoteGrantStatus(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-updateremotegrantstatus-f-sys.md) | 更新远程授权状态。 该功能用于开启或关闭远程授权特性。 启用时，设备可以向远程设备授予权限； 禁用时，不允许远程授权。 |
| [verifyControlledDevicePackage(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-verifycontrolleddevicepackage-f-sys.md) | 对受控设备的授权包进行校验。 对被控设备发送的远程授权包进行校验。 它验证票证以确保授权是合法的。 |
| [verifyControllerDevicePackage(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-verifycontrollerdevicepackage-f-sys.md) | 验证来自控制器设备的授权包。 验证控制器设备发送的远程授权包。 它验证票证和远程设备信息，以确保授权是合法的。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatusInfo(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-authstatusinfo-i-sys.md) | 授权状态信息。 |
| [CliCmdInfo(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i-sys.md) | CLI命令信息。 |
| [OperationInfo(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md) | 操作信息。 |
| [PermissionInfo(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-permissioninfo-i-sys.md) | 权限信息。 |
| [PermissionQuery(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md) | 权限查询信息。 |
| [PermissionQueryResult(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-permissionqueryresult-i-sys.md) | 权限查询结果。 |
| [RemoteAuthPackage(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md) | 远程授权包。 |
| [RemoteControlParams(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-remotecontrolparams-i-sys.md) | 远程控制交互参数 |
| [RemoteInfo(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md) | 远端设备信息。 |
| [RemoteUserAuthItem(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-remoteuserauthitem-i-sys.md) | 远程用户授权项。 |
| [RemoteUserAuthResults(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-remoteuserauthresults-i-sys.md) | 远程用户授权结果。 |
| [TicketInfo(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md) | 凭据信息。 |
| [UserAuthResult(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-userauthresult-i-sys.md) | 用户授权结果。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatus(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-authstatus-e-sys.md) | 授权状态。 |
| [OperationType(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-operationtype-e-sys.md) | 操作类型。 |
| [RemoteGrantStatus(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-remotegrantstatus-e-sys.md) | 远程授权状态。 |
| [Role(This module provides the capabilities of tools access control)](arkts-ability-abilitytoolaccessctrl-role-e-sys.md) | 设备角色。 |
<!--DelEnd-->
