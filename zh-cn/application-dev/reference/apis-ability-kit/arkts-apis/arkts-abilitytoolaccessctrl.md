# @ohos.abilityToolAccessCtrl

abilityToolAccessCtrl的命名空间

**起始版本：** 26.0.0

**ArkTS模式：** 仅支持ArkTS-Dyn，起始版本为26.0.0。

**废弃版本：** -1

<!--Device-unnamed-declare namespace abilityToolAccessCtrl--><!--Device-unnamed-declare namespace abilityToolAccessCtrl-End-->

**系统能力：** SystemCapability.Security.Asset

**系统接口：** 此接口为系统接口。

## 汇总

<!--Del-->
### 函数（系统接口）

| 名称 | 说明 |
| --- | --- |
| [generateControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrolleddevicepackage-f-sys.md#generateControlledDevicePackage) | 生成受控设备的授权包。 根据权限查询列表生成远程授权包。 生成的包可以发送到控制器设备进行权限验证。 |
| [generateControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-generatecontrollerdevicepackage-f-sys.md#generateControllerDevicePackage) | 生成控制器设备的授权包。 根据远程用户授权结果生成远程授权包。 生成的包可以发送到受控设备进行权限验证。 |
| [getRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-getremotegrantstatus-f-sys.md#getRemoteGrantStatus) | 获取远程授权状态。 该功能用于查询远程授权特性的使能状态。 启用时，设备可以向远程设备授予权限； 禁用时，不允许远程授权。 |
| [grantToolPermissionsByUser](arkts-ability-abilitytoolaccessctrl-granttoolpermissionsbyuser-f-sys.md#grantToolPermissionsByUser) | 根据用户授权结果授予工具权限。 该功能根据用户的授权决定授予工具（CLI命令或API）的权限。 授权成功后，会生成工单，用于权限验证。 |
| [requestToolPermissions](arkts-ability-abilitytoolaccessctrl-requesttoolpermissions-f-sys.md#requestToolPermissions) | 根据指定的操作查询工具权限。 该函数用于检查权限查询中指定的CLI命令或API的权限状态。 对于每个操作，它返回权限状态、授权状态以及是否需要用户对话框。 当needTicket设置为true时，远程授权会生成一个票据。 |
| [updateRemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-updateremotegrantstatus-f-sys.md#updateRemoteGrantStatus) | 更新远程授权状态。 该功能用于开启或关闭远程授权特性。 启用时，设备可以向远程设备授予权限； 禁用时，不允许远程授权。 |
| [verifyControlledDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrolleddevicepackage-f-sys.md#verifyControlledDevicePackage) | 对受控设备的授权包进行校验。 对被控设备发送的远程授权包进行校验。 它验证票证以确保授权是合法的。 |
| [verifyControllerDevicePackage](arkts-ability-abilitytoolaccessctrl-verifycontrollerdevicepackage-f-sys.md#verifyControllerDevicePackage) | 验证来自控制器设备的授权包。 验证控制器设备发送的远程授权包。 它验证票证和远程设备信息，以确保授权是合法的。 |
<!--DelEnd-->

<!--Del-->
### 接口（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatusInfo](arkts-ability-abilitytoolaccessctrl-authstatusinfo-i-sys.md) | 授权状态信息。 |
| [CliCmdInfo](arkts-ability-abilitytoolaccessctrl-clicmdinfo-i-sys.md) | CLI命令信息。 |
| [OperationInfo](arkts-ability-abilitytoolaccessctrl-operationinfo-i-sys.md) | 操作信息。 |
| [PermissionInfo](arkts-ability-abilitytoolaccessctrl-permissioninfo-i-sys.md) | 权限信息。 |
| [PermissionQuery](arkts-ability-abilitytoolaccessctrl-permissionquery-i-sys.md) | 权限查询信息。 |
| [PermissionQueryResult](arkts-ability-abilitytoolaccessctrl-permissionqueryresult-i-sys.md) | 权限查询结果。 |
| [RemoteAuthPackage](arkts-ability-abilitytoolaccessctrl-remoteauthpackage-i-sys.md) | 远程授权包。 |
| [RemoteControlParams](arkts-ability-abilitytoolaccessctrl-remotecontrolparams-i-sys.md) | 远程控制交互参数 |
| [RemoteInfo](arkts-ability-abilitytoolaccessctrl-remoteinfo-i-sys.md) | 远端设备信息。 |
| [RemoteUserAuthItem](arkts-ability-abilitytoolaccessctrl-remoteuserauthitem-i-sys.md) | 远程用户授权项。 |
| [RemoteUserAuthResults](arkts-ability-abilitytoolaccessctrl-remoteuserauthresults-i-sys.md) | 远程用户授权结果。 |
| [TicketInfo](arkts-ability-abilitytoolaccessctrl-ticketinfo-i-sys.md) | 凭据信息。 |
| [UserAuthResult](arkts-ability-abilitytoolaccessctrl-userauthresult-i-sys.md) | 用户授权结果。 |
<!--DelEnd-->

<!--Del-->
### 枚举（系统接口）

| 名称 | 说明 |
| --- | --- |
| [AuthStatus](arkts-ability-abilitytoolaccessctrl-authstatus-e-sys.md) | 授权状态。 |
| [OperationType](arkts-ability-abilitytoolaccessctrl-operationtype-e-sys.md) | 操作类型。 |
| [RemoteGrantStatus](arkts-ability-abilitytoolaccessctrl-remotegrantstatus-e-sys.md) | 远程授权状态。 |
| [Role](arkts-ability-abilitytoolaccessctrl-role-e-sys.md) | 设备角色。 |
<!--DelEnd-->

